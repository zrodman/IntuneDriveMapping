---
inclusion: always
---

# Project Context for AI Assistants

## Project Overview
This is a customized fork of the IntuneDriveMapping project - an ASP.NET Core web application that generates Intune PowerShell scripts for network drive mapping on Entra ID joined devices.

## Key Customizations Made
- **Modern Dark Theme**: CSS Custom Properties implementation with system preference detection
- **Custom Branding**: Removed original creator references, points to zrodman/IntuneDriveMapping
- **Azure Deployment**: Configured for Azure App Service with automated CI/CD
- **.NET 8.0 LTS**: Upgraded from .NET 6.0 for continued security support

## Architecture & Structure
- **Framework**: ASP.NET Core 8.0 LTS MVC
- **Frontend**: Bootstrap 4 + modern CSS Custom Properties dark theme
- **Deployment**: Azure App Service via GitHub Actions
- **Testing**: Unit tests in separate project

## Important Files & Locations
- **Main CSS**: `IntuneDriveMapping/wwwroot/css/site.css` (contains CSS Custom Properties theming system)
- **Layout**: `IntuneDriveMapping/Views/Shared/_Layout.cshtml` (main template with color-scheme meta tag)
- **Controllers**: `IntuneDriveMapping/Controllers/` (business logic)
- **Models**: `IntuneDriveMapping/Models/` (data structures)
- **Tests**: `IntuneDriveMapping.Tests/` (unit tests)

## Development Guidelines
1. **Modern Dark Theme**: Use CSS Custom Properties (--variables) for all theming
2. **System Preference Support**: Automatic detection via `prefers-color-scheme` media query
3. **Accessibility**: Maintain WCAG AA contrast ratios and color-scheme support
4. **No External Links**: Keep all references internal or to the zrodman repository
5. **Azure Compatibility**: Changes should work in Azure App Service environment

## Dark Theme Implementation
- **CSS Variables**: Semantic color system with `--text-primary`, `--bg-surface`, etc.
- **System Detection**: Automatic dark mode based on user's OS preference
- **Manual Override**: Support for `[data-theme="dark"]` and `[data-theme="light"]`
- **Smooth Transitions**: 0.3s ease transitions between themes
- **Image Optimization**: Brightness/contrast adjustments in dark mode

## Common Tasks
- **UI Changes**: Modify CSS variables in `site.css`, maintain semantic naming
- **Theme Updates**: Use CSS Custom Properties, avoid hardcoded colors
- **New Features**: Add controllers, views, models following MVC pattern
- **Branding Updates**: Update layout template and remove any external references
- **Deployment**: Automatic via GitHub Actions on push to main

## Testing Approach
- Run `dotnet test` for unit tests
- Test dark theme with system preference changes
- Verify smooth transitions between themes
- Check accessibility with contrast analyzers
- Verify Azure deployment through GitHub Actions

## Troubleshooting
- **Theme Issues**: Check CSS Custom Properties and `prefers-color-scheme` support
- **Deployment Issues**: Check GitHub Actions logs and Azure App Service logs
- **Accessibility Problems**: Verify contrast ratios and color-scheme meta tag
- **Browser Compatibility**: Ensure CSS Custom Properties support