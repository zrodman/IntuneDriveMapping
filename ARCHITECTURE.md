# Architecture Documentation

## System Overview
The Intune Drive Mapping Generator is a web-based tool built on ASP.NET Core MVC that converts Group Policy drive mapping configurations into Intune-compatible PowerShell scripts.

## Application Architecture

### Presentation Layer
- **Framework**: ASP.NET Core MVC
- **UI Framework**: Bootstrap 4 with custom dark theme
- **Views**: Razor templates with strongly-typed models
- **Static Assets**: CSS, JavaScript, and vendor libraries

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
- Generates Intune-compatible PowerShell scripts

### DriveMappingStore
- Session-based storage implementation
- Manages drive mapping collections per user session
- Interface-based design for potential future persistence layers

## Data Flow

1. **Upload**: User uploads Group Policy XML file
2. **Parse**: Converter extracts drive mapping configurations
3. **Display**: Configurations shown in editable table format
4. **Modify**: User can add/edit/delete drive mappings
5. **Generate**: System creates PowerShell script for Intune deployment
6. **Download**: User downloads generated script

## Security Considerations

- No persistent data storage (session-based only)
- File upload validation for XML files
- Input sanitization for user-provided data
- HTTPS enforcement in production

## Deployment Architecture

### Azure App Service
- Platform: Linux containers
- Runtime: .NET 6.0
- Scaling: Manual/automatic based on demand
- Monitoring: Application Insights integration

### CI/CD Pipeline
- Source: GitHub repository
- Build: GitHub Actions
- Deploy: Azure App Service deployment slots
- Rollback: Previous deployment slot switching

## Customizations

### Dark Theme Implementation
- Complete CSS override for Bootstrap components
- Consistent color palette across all UI elements
- Accessibility-compliant contrast ratios
- Responsive design maintained

### Branding Customizations
- Removed external dependencies and links
- Updated repository references
- Custom footer and navigation
- Maintained original functionality

## Performance Characteristics

- **Startup Time**: ~2-3 seconds (cold start)
- **Memory Usage**: ~50-100MB typical
- **File Processing**: Handles XML files up to 10MB
- **Concurrent Users**: Designed for low-medium traffic

## Monitoring and Logging

- Application Insights for performance monitoring
- Built-in ASP.NET Core logging
- Azure App Service diagnostic logs
- GitHub Actions deployment logs

## Future Considerations

- Database integration for persistent storage
- User authentication and authorization
- API endpoints for programmatic access
- Enhanced error handling and validation