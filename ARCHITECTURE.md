# Architecture Documentation

## System Overview
The Intune Drive Mapping Generator is a web-based tool built on ASP.NET Core 8.0 LTS MVC that converts Group Policy drive mapping configurations into Intune-compatible PowerShell scripts.

## Application Architecture

### Presentation Layer
- **Framework**: ASP.NET Core 8.0 LTS MVC
- **UI Framework**: Bootstrap 4 with modern CSS Custom Properties dark theme
- **Theme System**: Automatic system preference detection with manual override support
- **Views**: Razor templates with strongly-typed models
- **Static Assets**: CSS with Custom Properties, JavaScript, and vendor libraries

### Business Logic Layer
- **Controllers**: Handle HTTP requests and coordinate business operations
- **Helpers**: Utility classes for conversion and data manipulation
- **Models**: Data transfer objects and view models

### Data Layer
- **Storage**: In-memory session-based storage (no persistent database)
- **File Processing**: XML parsing and PowerShell script generation

## Key Components

### DriveMappingController
- Primary controller handling drive mapping operations
- Actions: Index, Upload, Create, Edit, Delete, Download
- Manages user session state for drive mappings

### Converter Helper
- Core business logic for XML to PowerShell conversion
- Handles Group Policy XML parsing
- Generates Intune-compatible PowerShell scripts with Windows 11 conhost support

### DriveMappingStore
- Session-based storage implementation
- Manages drive mapping collections per user session
- Interface-based design for potential future persistence layers

## Modern Dark Theme Architecture

### CSS Custom Properties System
- **Semantic Variables**: Purpose-based naming (--text-primary, --bg-surface)
- **Automatic Detection**: `@media (prefers-color-scheme: dark)` for system preferences
- **Manual Override**: `[data-theme="dark"]` and `[data-theme="light"]` selectors
- **Smooth Transitions**: 0.3s ease transitions between themes
- **Accessibility**: WCAG AA contrast ratios and color-scheme meta tag

### Theme Implementation
```css
:root {
  --text-primary: #212529;  /* Light mode */
  --bg-body: #ffffff;
}

@media (prefers-color-scheme: dark) {
  :root {
    --text-primary: #e0e0e0;  /* Dark mode */
    --bg-body: #121212;
  }
}
```

## Data Flow

1. **Upload**: User uploads Group Policy XML file
2. **Parse**: Converter extracts drive mapping configurations
3. **Display**: Configurations shown in editable table format with dark theme support
4. **Modify**: User can add/edit/delete drive mappings
5. **Generate**: System creates PowerShell script for Intune deployment with conhost enhancements
6. **Download**: User downloads generated script

## Security Considerations

- No persistent data storage (session-based only)
- File upload validation for XML files
- Input sanitization for user-provided data
- HTTPS enforcement in production
- Content Security Policy headers

## Deployment Architecture

### Azure App Service
- Platform: Linux containers
- Runtime: .NET 8.0 LTS (supported until November 2026)
- Scaling: Manual/automatic based on demand
- Monitoring: Application Insights integration

### CI/CD Pipeline
- Source: GitHub repository (zrodman/IntuneDriveMapping)
- Build: GitHub Actions with .NET 8.0 SDK
- Deploy: Azure App Service deployment slots
- Rollback: Previous deployment slot switching

## Customizations

### Modern Dark Theme Implementation
- CSS Custom Properties for maintainable theming
- Automatic system preference detection
- Smooth transitions and proper contrast ratios
- Material Design dark theme colors (#121212 background)
- Image brightness adjustments for dark mode
- Accessibility-compliant contrast ratios

### Windows 11 Enhancements
- PowerShell script generation with `conhost.exe --headless` support
- Silent execution without PowerShell window flashing
- Improved user experience on modern Windows devices

### Branding Customizations
- Removed external dependencies and links
- Updated repository references to zrodman/IntuneDriveMapping
- Custom footer and navigation
- Maintained original functionality

## Performance Characteristics

- **Startup Time**: ~2-3 seconds (cold start)
- **Memory Usage**: ~50-100MB typical
- **File Processing**: Handles XML files up to 10MB
- **Concurrent Users**: Designed for low-medium traffic
- **Theme Switching**: Smooth transitions without layout shifts

## Browser Support

### Modern Features
- **CSS Custom Properties**: All modern browsers (IE 11+ with fallbacks)
- **prefers-color-scheme**: Safari 12.1+, Chrome 76+, Firefox 67+, Edge 79+
- **color-scheme**: Safari 13+, Chrome 81+, Firefox 96+

### Fallback Strategy
- Graceful degradation for older browsers
- Default light theme when dark mode unsupported
- Progressive enhancement approach

## Monitoring and Logging

- Application Insights for performance monitoring
- Built-in ASP.NET Core logging with structured logging
- Azure App Service diagnostic logs
- GitHub Actions deployment logs
- Theme usage analytics (if implemented)

## Future Considerations

- Database integration for persistent storage
- User authentication and authorization
- API endpoints for programmatic access
- Enhanced error handling and validation
- Theme customization options
- Additional theme variants (high contrast, etc.)