---
inclusion: manual
---

# AI Assistant Guidance

## When Working on This Project

### Understanding the Codebase
- This is a customized ASP.NET Core MVC application
- Focus on maintaining dark theme consistency
- All external references should point to zrodman/IntuneDriveMapping
- Azure App Service deployment is automated via GitHub Actions

### Common AI Tasks

#### UI/Styling Changes
- Always check `IntuneDriveMapping/wwwroot/css/site.css` for dark theme variables
- Ensure text contrast meets accessibility standards (#e0e0e0 on dark backgrounds)
- Test changes across different screen sizes
- Maintain Bootstrap 4 compatibility

#### Code Changes
- Follow ASP.NET Core MVC patterns
- Add appropriate error handling
- Update unit tests when modifying business logic
- Consider Azure App Service compatibility

#### Documentation Updates
- Keep README.md current with any major changes
- Update ARCHITECTURE.md for structural changes
- Maintain CONTRIBUTING.md for development process changes

### Problem-Solving Approach

1. **Identify the Issue**: Understand what needs to be changed/fixed
2. **Locate Relevant Files**: Use the file structure guide in project-context.md
3. **Check Dependencies**: Consider impact on dark theme, Azure deployment, etc.
4. **Implement Changes**: Follow development standards
5. **Test Thoroughly**: Verify dark theme, functionality, and deployment
6. **Document**: Update relevant documentation if needed

### Red Flags to Avoid
- ❌ Adding external links or references to original creator
- ❌ Breaking dark theme consistency
- ❌ Introducing dependencies that won't work in Azure App Service
- ❌ Modifying core functionality without understanding impact
- ❌ Ignoring accessibility standards

### Best Practices
- ✅ Always test dark theme changes in browser
- ✅ Maintain consistent color palette
- ✅ Follow existing code patterns
- ✅ Add appropriate comments for complex changes
- ✅ Consider mobile responsiveness
- ✅ Verify Azure deployment compatibility

### Quick Reference

#### Dark Theme Colors
- Background: `#1a1a1a`
- Container: `#2d2d2d`
- Input: `#3d3d3d`
- Text: `#e0e0e0`
- Muted: `#aaa`
- Border: `#404040`
- Input Border: `#555`

#### Key Files for Common Tasks
- Layout changes: `Views/Shared/_Layout.cshtml`
- Styling: `wwwroot/css/site.css`
- Main functionality: `Controllers/DriveMappingController.cs`
- Data models: `Models/DriveMapping.cs`
- Business logic: `Helpers/Converter.cs`

#### Testing Commands
```bash
# Run unit tests
dotnet test

# Build project
dotnet build

# Run locally
dotnet run --project IntuneDriveMapping
```