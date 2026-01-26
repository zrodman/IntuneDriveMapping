# Intune Drive Mapping Generator

A web-based tool for generating PowerShell scripts that map network drives on Entra ID (Azure AD) joined devices managed by Microsoft Intune.

## What This Tool Does

This application generates PowerShell scripts that:
- Map network drives on Windows 11 devices
- Work with Entra ID joined devices (no domain controller required)
- Support security group filtering with nested groups
- Handle recurring execution through scheduled tasks
- Use `conhost.exe --headless` for silent execution (Windows 11 requirement)

**Important**: The generated PowerShell scripts are standalone and have no dependency on ASP.NET Core or this web application. This tool is simply a generator - once you download the script, you can deploy it through Intune without any connection back to this application.

## Getting Started

### For End Users

1. **Prepare Your Configuration**
   - (Optional) Export existing Group Policy drive mappings to XML
   - Or create mappings from scratch using the web interface

2. **Generate Your Script**
   - Visit the generator web interface
   - Upload your XML file or build from scratch
   - Configure drive letters, UNC paths, and security groups
   - Download the generated PowerShell script

3. **Deploy via Intune**
   - Upload the PowerShell script to Microsoft Intune
   - Assign to appropriate device groups
   - Monitor deployment through Intune reporting

### System Requirements

**Target Devices:**
- Windows 11 (required for silent execution)
- Entra ID joined devices
- Microsoft Intune management

**Generated Script Dependencies:**
- PowerShell 5.1 or later
- Network connectivity to file shares
- Appropriate permissions for target UNC paths

## Architecture

### Web Application (Hosting Platform)
- **Framework**: ASP.NET Core MVC
- **Frontend**: Bootstrap 4 with custom dark theme
- **Deployment**: Azure App Service
- **Purpose**: Generate PowerShell scripts only

### Generated Output (Standalone Scripts)
- **Language**: PowerShell
- **Dependencies**: None (beyond Windows PowerShell)
- **Execution**: Via Intune or manual deployment
- **Storage**: Local scheduled tasks and registry

## Key Features & Improvements

### Enhanced Windows 11 Support
- Uses `conhost.exe --headless` for silent script execution
- Eliminates PowerShell window flashing during scheduled task runs
- Improved user experience on modern Windows devices

### Security Group Integration
- Supports nested Active Directory groups
- Dynamic group membership evaluation
- Conditional drive mapping based on user group membership

### Robust Error Handling
- Comprehensive logging to `DriveMapping.log`
- Graceful handling of network connectivity issues
- Retry mechanisms for transient failures

## Troubleshooting

### Common Issues and Solutions

#### 1. Script Reports Success but No Drives Mapped

**Symptoms:**
- Intune shows "Successful" deployment
- No network drives appear in File Explorer
- No scheduled task created

**Solutions:**
- Check PowerShell execution policy: `Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope CurrentUser`
- Verify user has local admin rights (required for scheduled task creation)
- Check Windows Event Logs for PowerShell execution errors
- Ensure target UNC paths are accessible from the device

#### 2. "The local device name is already in use"

**Symptoms:**
- Error in DriveMapping.log
- Drive mappings fail to update when UNC paths change
- Existing drives not properly removed

**Root Cause:** Script cannot remove existing drive mappings before creating new ones

**Solutions:**
- Enable "Remove stale drives" option when generating script
- Manually disconnect existing drives: `net use * /delete /y`
- Use different drive letters for updated mappings
- Consider using `Remove-SmbMapping` for persistent connections

#### 3. Domain Controller Authentication Issues

**Symptoms:**
- "Cannot contact domain controller" errors
- Authentication failures for UNC paths
- VPN connectivity issues

**Solutions:**
- Ensure VPN connection is established before script execution
- Add network connectivity triggers to scheduled task:
  ```powershell
  # Network profile change triggers
  $trigger2.Subscription = '*[System[Provider[@name=''Microsoft-Windows-NetworkProfile''] and EventID=10002]]'
  $trigger3.Subscription = '*[System[Provider[@name=''Microsoft-Windows-NetworkProfile''] and EventID=4004]]'
  ```
- Verify DNS resolution to domain controllers
- Check firewall rules for domain authentication

#### 4. Disconnected/Obsolete Drive Removal

**Symptoms:**
- Old drive mappings remain after server changes
- `Get-PSDrive` doesn't detect disconnected network drives
- Manual cleanup required

**Solutions:**
- Use SMB mapping commands instead of PSDrive:
  ```powershell
  Get-SmbMapping | Where-Object {$_.Status -eq "Unavailable"} | Remove-SmbMapping -Force
  ```
- Enable comprehensive drive cleanup in generated script
- Implement custom logic for obsolete drive detection

#### 5. Security Group Filtering Not Working

**Symptoms:**
- Drives map for all users regardless of group membership
- Group-specific mappings appear for wrong users

**Solutions:**
- Verify `$searchRoot` variable contains correct domain name
- Check nested group membership resolution
- Ensure service account has permissions to query Active Directory
- Test group membership manually: `whoami /groups`

### Advanced Troubleshooting

#### Enable Detailed Logging
Add to generated script:
```powershell
$VerbosePreference = "Continue"
$DebugPreference = "Continue"
Start-Transcript -Path "C:\ProgramData\intune-drive-mapping-generator\DetailedLog.txt"
```

#### Network Connectivity Testing
```powershell
# Test UNC path accessibility
Test-Path "\\server\share"
Test-NetConnection -ComputerName "server" -Port 445
```

#### Scheduled Task Debugging
```powershell
# Check task status
Get-ScheduledTask -TaskName "IntuneDriveMapping"
Get-ScheduledTaskInfo -TaskName "IntuneDriveMapping"

# View task history
Get-WinEvent -FilterHashtable @{LogName="Microsoft-Windows-TaskScheduler/Operational"}
```

## Development & Customization

### Web Application Development
- Built with ASP.NET Core MVC
- Modern dark theme UI
- Azure App Service deployment
- Automated CI/CD via GitHub Actions

### Script Customization
The generated PowerShell scripts can be modified to:
- Add custom logging
- Implement additional network triggers
- Include organization-specific logic
- Integrate with other management tools

## Support & Resources

- **Repository**: [https://github.com/zrodman/IntuneDriveMapping](https://github.com/zrodman/IntuneDriveMapping)
- **Issues**: Report problems via GitHub Issues
- **Documentation**: See repository wiki for detailed guides

## Technology Stack

**Web Application:**
- ASP.NET Core 8.0 LTS
- Bootstrap 4 with custom dark theme
- Azure App Service hosting
- GitHub Actions CI/CD

**Generated Scripts:**
- Windows PowerShell 5.1+
- Windows Task Scheduler
- SMB/CIFS networking
- Active Directory integration
