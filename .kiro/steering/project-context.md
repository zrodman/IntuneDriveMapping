---
inclusion: always
---

# Project Context for AI Assistants

## Project Overview
This is a customized fork of the IntuneDriveMapping project - an ASP.NET Core web application that generates Intune PowerShell scripts for network drive mapping on Entra ID joined devices.

## Key Customizations Made
- **Dark Theme**: Complete dark mode implementation with proper contrast
- **Custom Branding**: Removed original creator references, points to zrodman/IntuneDriveMapping
- **Azure Deployment**: Configured for Azure App Service with automated CI/CD

## Architecture & Structure
- **Framework**: ASP.NET Core MVC
- **Frontend**: Bootstrap 4 + custom dark theme CSS
- **Deployment**: Azure App Service via GitHub Actions
- **Testing**: Unit tests in separate project

## Important Files & Locations
- **Main CSS**: `IntuneDriveMapping/wwwroot/css/site.css` (contains all dark theme styling)
- **Layout**: `IntuneDriveMapping/Views/Shared/_Layout.cshtml` (main template)
- **Controllers**: `IntuneDriveMapping/Controllers/` (business logic)
- **Models**: `IntuneDriveMapping/Models/` (data structures)
- **Tests**: `IntuneDriveMapping.Tests/` (unit tests)

## Development Guidelines
1. **Dark Theme Consistency**: All UI changes must maintain dark theme standards
2. **Text Contrast**: Ensure light text (#e0e0e0) on dark backgrounds
3. **No External Links**: Keep all references internal or to the zrodman repository
4. **Azure Compatibility**: Changes should work in Azure App Service environment

## Common Tasks
- **UI Changes**: Modify CSS in `site.css`, maintain dark theme variables
- **New Features**: Add controllers, views, models following MVC pattern
- **Branding Updates**: Update layout template and remove any external references
- **Deployment**: Automatic via GitHub Actions on push to main

## Testing Approach
- Run `dotnet test` for unit tests
- Test dark theme in browser dev tools
- Verify Azure deployment through GitHub Actions

## Troubleshooting
- **Text Visibility Issues**: Check CSS for proper color contrast in dark theme
- **Deployment Issues**: Check GitHub Actions logs and Azure App Service logs
- **Styling Problems**: Verify Bootstrap 4 compatibility with custom dark theme