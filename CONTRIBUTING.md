# Contributing to Intune Drive Mapping Generator

## Project Overview
This is a customized ASP.NET Core 8.0 LTS web application for generating Intune PowerShell scripts for network drive mapping. It features a modern dark theme with CSS Custom Properties and is designed for Azure deployment.

## Development Setup

### Prerequisites
- .NET 8.0 SDK or later
- Visual Studio 2022 or VS Code
- Git

### Local Development
1. Clone the repository
2. Open `IntuneDriveMapping.sln` in Visual Studio
3. Restore NuGet packages: `dotnet restore`
4. Run the application: `dotnet run` or F5 in Visual Studio

## Architecture

### Project Structure
- `IntuneDriveMapping/` - Main web application (.NET 8.0 LTS)
  - `Controllers/` - MVC controllers
  - `Models/` - Data models
  - `Views/` - Razor views
  - `Helpers/` - Utility classes
  - `wwwroot/` - Static assets (CSS with Custom Properties, JS, images)
- `IntuneDriveMapping.Tests/` - Unit tests (.NET 8.0)

### Key Components
- **DriveMappingController**: Main functionality for drive mapping generation
- **Converter**: Handles XML to PowerShell conversion with Windows 11 conhost support
- **DriveMappingStore**: Session-based data persistence layer

## Customizations Made

### Modern Dark Theme
- **CSS Custom Properties**: Semantic variable system (--text-primary, --bg-surface)
- **System Preference Detection**: Automatic dark mode via `prefers-color-scheme`
- **Manual Override**: Support for `[data-theme="dark"]` and `[data-theme="light"]`
- **Smooth Transitions**: 0.3s ease transitions between themes
- **Accessibility**: WCAG AA contrast ratios and color-scheme meta tag

### Windows 11 Enhancements
- **conhost.exe --headless**: Silent PowerShell execution without window flashing
- **Improved UX**: Better experience on modern Windows devices

### Custom Branding
- Removed external links and original creator references
- Updated to point to zrodman/IntuneDriveMapping repository
- Custom footer and navigation

### Azure Ready
- Configured for Azure App Service deployment
- Automated CI/CD via GitHub Actions
- .NET 8.0 LTS for long-term support

## Making Changes

### UI/Theme Changes
- **Main CSS**: `IntuneDriveMapping/wwwroot/css/site.css`
- **Use CSS Custom Properties**: Define colors as semantic variables
- **System Preference Support**: Use `@media (prefers-color-scheme: dark)`
- **Manual Override**: Support `[data-theme]` attribute selectors
- **Layout Template**: `IntuneDriveMapping/Views/Shared/_Layout.cshtml`

### Adding Features
1. Create/modify controllers in `Controllers/`
2. Add corresponding views in `Views/`
3. Update models if needed in `Models/`
4. Add tests in `IntuneDriveMapping.Tests/`
5. Ensure theme compatibility with new UI elements

### Theme Development Guidelines
```css
/* Use semantic CSS Custom Properties */
:root {
  --text-primary: #212529;    /* Light mode */
  --bg-surface: #ffffff;
}

@media (prefers-color-scheme: dark) {
  :root {
    --text-primary: #e0e0e0;  /* Dark mode */
    --bg-surface: #1e1e1e;
  }
}

/* Apply variables to elements */
.my-component {
  color: var(--text-primary);
  background: var(--bg-surface);
  transition: background-color 0.3s ease, color 0.3s ease;
}
```

### Deployment
- **Automatic**: GitHub Actions deploys on push to main branch
- **Target**: Azure App Service with .NET 8.0 runtime
- **No manual steps**: Fully automated CI/CD pipeline

## Code Standards

### C# Conventions
- Follow standard C# conventions and .NET 8.0 best practices
- Use PascalCase for public members, camelCase for private fields
- Add XML documentation for public APIs
- Target .NET 8.0 LTS for security and performance

### CSS Standards
- **Use CSS Custom Properties**: Avoid hardcoded colors
- **Semantic Naming**: Use purpose-based names (--text-primary vs --white)
- **System Preference Support**: Always implement `prefers-color-scheme`
- **Accessibility**: Maintain WCAG AA contrast ratios (4.5:1 minimum)
- **Smooth Transitions**: Add transitions for theme switching

### Razor Views
- Use strongly-typed models
- Maintain consistent indentation (4 spaces)
- Include accessibility attributes
- Support both light and dark themes

## Testing

### Local Testing
```bash
# Run unit tests
dotnet test

# Build project
dotnet build

# Run locally
dotnet run --project IntuneDriveMapping
```

### Theme Testing
- Test both light and dark system preferences
- Verify smooth transitions between themes
- Check accessibility with contrast analyzers
- Test on multiple browsers and devices

### Browser Support
- **CSS Custom Properties**: All modern browsers
- **prefers-color-scheme**: Safari 12.1+, Chrome 76+, Firefox 67+
- **Graceful Degradation**: Fallback to light theme on older browsers

## Troubleshooting

### Common Issues
- **Theme not switching**: Check CSS Custom Properties support and `prefers-color-scheme`
- **Contrast issues**: Verify color variables and WCAG compliance
- **Build failures**: Ensure .NET 8.0 SDK is installed
- **Azure deployment**: Check GitHub Actions logs for deployment status

### Development Tools
- **Browser DevTools**: Test theme switching and inspect CSS variables
- **Accessibility Tools**: Use contrast analyzers and screen readers
- **Performance**: Monitor Core Web Vitals and theme switching performance