# Intune Drive Mapping Generator

A customized web application for generating Intune PowerShell scripts to map network drives on Entra ID joined devices. This version has been updated with a modern dark theme and is designed to run on Azure.

## Features

* Generate Intune PowerShell scripts to map network drives on Entra ID joined devices
* Seamlessly migrate existing network drive mapping group policies
* Generate a network drive mapping configuration from scratch
* Supports security group filtering (with nested groups)
* Supports recurring execution on clients
* **Requires Windows 11** for silent execution using `conhost.exe --headless`
* Modern dark theme UI
* Custom branding and Azure deployment ready

## Usage

1. (Optional) Export your existing group policy configuration which contains the network drive configuration to an XML file
2. Upload the configuration or generate a new one from scratch in the generator
3. Download your generated PowerShell script
4. Deploy the PowerShell script with Microsoft Intune

## Deployment

This application is configured to run on Azure and has been customized for personal use with:
- Dark theme implementation
- Removed external dependencies
- Custom branding
- Optimized for Azure hosting

## Technology Stack

- ASP.NET Core
- Bootstrap 4 with custom dark theme
- JavaScript/jQuery
- Designed for Azure App Service deployment
