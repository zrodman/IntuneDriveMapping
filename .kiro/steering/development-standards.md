---
inclusion: fileMatch
fileMatchPattern: "*.cs|*.cshtml|*.css|*.js"
---

# Development Standards

## Code Style Guidelines

### C# Standards
- Use PascalCase for public members, methods, and classes
- Use camelCase for private fields and local variables
- Add XML documentation for public APIs
- Follow async/await patterns for I/O operations
- Use meaningful exception messages

### Razor View Standards
- Keep views focused on presentation logic only
- Use strongly-typed models
- Maintain consistent indentation (4 spaces)
- Use HTML helpers and tag helpers appropriately

### CSS Standards
- Maintain dark theme consistency (#1a1a1a background, #e0e0e0 text)
- Use semantic class names
- Group related styles together
- Comment major sections
- Ensure proper contrast ratios (minimum 4.5:1)

### JavaScript Standards
- Use modern ES6+ syntax where supported
- Maintain jQuery compatibility for Bootstrap components
- Add error handling for AJAX calls
- Use meaningful variable names

## Dark Theme Requirements
- Background colors: #1a1a1a (body), #2d2d2d (containers), #3d3d3d (inputs)
- Text colors: #e0e0e0 (primary), #aaa (muted)
- Border colors: #404040 (primary), #555 (inputs)
- Maintain accessibility standards (WCAG 2.1 AA)

## Testing Requirements
- Unit tests for all business logic
- Integration tests for controllers
- UI tests for critical user flows
- Test dark theme in multiple browsers

## Performance Considerations
- Minimize CSS bundle size
- Optimize images for web
- Use CDN for external libraries
- Enable compression in Azure App Service