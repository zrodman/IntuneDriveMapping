# Contributing to Intune Drive Mapping Generator

## Project Overview
This is a customized ASP.NET Core web application for generating Intune PowerShell scripts for network drive mapping. It features a modern dark theme and is designed for Azure deployment.

## Development Setup

### Prerequisites
- .NET 6.0 or later
- Visual Studio 2022 or VS Code
- Git

### Local Development
1. Clone the repository
2. Open `IntuneDriveMapping.sln` in Visual Studio
3. Restore NuGet packages
4. Run the application (F5)

## Architecture

### Project Structure
- `IntuneDriveMapping/` - Main web application
  - `Controllers/` - MVC controllers
  - `Models/` - Data models
  - `Views/` - Razor views
  - `Helpers/` - Utility classes
  - `wwwroot/` - Static assets (CSS, JS, images)
- `IntuneDriveMapping.Tests/` - Unit tests

### Key Components
- **DriveMappingController**: Main functionality for drive mapping generation
- **Converter**: Handles XML to PowerShell conversion
- **DriveMappingStore**: Data persistence layer

## Customizations Made
- **Dark Theme**: Complete dark mode implementation in `site.css`
- **Custom Branding**: Removed external links, updated to personal repository
- **Azure Ready**: Configured for Azure App Service deployment

## Making Changes

### UI/Theme Changes
- Main CSS file: `IntuneDriveMapping/wwwroot/css/site.css`
- Layout template: `IntuneDriveMapping/Views/Shared/_Layout.cshtml`
- Dark theme variables are consistently used throughout

### Adding Features
1. Create/modify controllers in `Controllers/`
2. Add corresponding views in `Views/`
3. Update models if needed in `Models/`
4. Add tests in `IntuneDriveMapping.Tests/`

### Deployment
- Automatic deployment via GitHub Actions on push to main branch
- Deploys to Azure App Service
- No manual deployment steps required

## Code Standards
- Follow standard C# conventions
- Use meaningful variable and method names
- Maintain dark theme consistency in UI changes
- Add appropriate error handling
- Include unit tests for new functionality

## Testing
Run tests locally:
```bash
dotnet test
```

## Troubleshooting
- Check Azure App Service logs for deployment issues
- Verify all NuGet packages are restored
- Ensure .NET version compatibility