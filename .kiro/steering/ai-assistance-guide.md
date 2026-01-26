---
inclusion: manual
---

# AI Assistant Guidance

## When Working on This Project

### Understanding the Codebase
- This is a customized ASP.NET Core 8.0 LTS MVC application
- Modern dark theme using CSS Custom Properties with system preference detection
- All external references point to zrodman/IntuneDriveMapping
- Azure App Service deployment is automated via GitHub Actions

### Common AI Tasks

#### UI/Styling Changes
- **CSS Custom Properties**: Use semantic variables in `IntuneDriveMapping/wwwroot/css/site.css`
- **Theme System**: Implement `@media (prefers-color-scheme: dark)` and `[data-theme]` selectors
- **Accessibility**: Ensure WCAG AA contrast ratios (4.5:1 minimum)
- **Smooth Transitions**: Add `transition: background-color 0.3s ease, color 0.3s ease`
- **System Integration**: Include `color-scheme` meta tag in layout

#### Code Changes
- Follow ASP.NET Core 8.0 LTS patterns and best practices
- Add appropriate error handling and logging
- Update unit tests when modifying business logic
- Consider Azure App Service compatibility
- Maintain session-based storage approach

#### Documentation Updates
- Keep README.md current with major changes
- Update ARCHITECTURE.md for structural changes
- Maintain CONTRIBUTING.md for development process changes
- Update steering files for AI context

### Problem-Solving Approach

1. **Identify the Issue**: Understand what needs to be changed/fixed
2. **Locate Relevant Files**: Use the file structure guide in project-context.md
3. **Check Dependencies**: Consider impact on theme system, Azure deployment, etc.
4. **Implement Changes**: Follow modern development standards
5. **Test Thoroughly**: Verify theme switching, accessibility, and deployment
6. **Document**: Update relevant documentation if needed

### Red Flags to Avoid
- ❌ Adding external links or references to original creator
- ❌ Using hardcoded colors instead of CSS Custom Properties
- ❌ Breaking system preference detection or manual theme override
- ❌ Introducing dependencies incompatible with Azure App Service
- ❌ Ignoring accessibility standards or smooth transitions
- ❌ Using outdated .NET versions or packages

### Best Practices
- ✅ Use CSS Custom Properties for all theming
- ✅ Test both automatic and manual theme switching
- ✅ Maintain semantic variable naming (--text-primary, not --white)
- ✅ Follow .NET 8.0 LTS patterns and security practices
- ✅ Add appropriate comments for complex theme logic
- ✅ Consider mobile responsiveness and accessibility
- ✅ Verify Azure deployment compatibility

### Quick Reference

#### Modern CSS Custom Properties
```css
:root {
  /* Light mode (default) */
  --text-primary: #212529;
  --bg-body: #ffffff;
  --color-primary: #007bff;
}

@media (prefers-color-scheme: dark) {
  :root {
    /* Dark mode */
    --text-primary: #e0e0e0;
    --bg-body: #121212;
    --color-primary: #4d94ff;
  }
}

/* Manual override */
[data-theme="dark"] {
  --text-primary: #e0e0e0;
  --bg-body: #121212;
}
```

#### Key Files for Common Tasks
- **Theme System**: `wwwroot/css/site.css` (CSS Custom Properties)
- **Layout**: `Views/Shared/_Layout.cshtml` (includes color-scheme meta tag)
- **Main Logic**: `Controllers/DriveMappingController.cs`
- **Data Models**: `Models/DriveMapping.cs`
- **Business Logic**: `Helpers/Converter.cs` (includes conhost enhancements)

#### Testing Commands
```bash
# Run unit tests
dotnet test

# Build project (.NET 8.0)
dotnet build

# Run locally
dotnet run --project IntuneDriveMapping

# Check for outdated packages
dotnet list package --outdated
```

#### Theme Testing
- Test system preference changes (OS dark/light mode)
- Verify smooth transitions between themes
- Check accessibility with contrast analyzers
- Test manual theme override functionality
- Validate color-scheme meta tag behavior

#### Browser Compatibility
- **CSS Custom Properties**: All modern browsers (IE 11+ with fallbacks)
- **prefers-color-scheme**: Safari 12.1+, Chrome 76+, Firefox 67+
- **color-scheme**: Safari 13+, Chrome 81+, Firefox 96+