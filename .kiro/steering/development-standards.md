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
- Target .NET 8.0 LTS for security and performance

### Razor View Standards
- Keep views focused on presentation logic only
- Use strongly-typed models
- Maintain consistent indentation (4 spaces)
- Use HTML helpers and tag helpers appropriately
- Include color-scheme meta tag for theme support

### CSS Standards - Modern Dark Theme Implementation
- **Use CSS Custom Properties**: Define all colors as semantic variables (--text-primary, --bg-surface)
- **System Preference Support**: Implement `@media (prefers-color-scheme: dark)` for automatic detection
- **Manual Override Support**: Use `[data-theme="dark"]` and `[data-theme="light"]` selectors
- **Smooth Transitions**: Add `transition: background-color 0.3s ease, color 0.3s ease`
- **Semantic Naming**: Use purpose-based names, not appearance-based (--text-primary vs --color-white)
- **Accessibility**: Ensure minimum 4.5:1 contrast ratios (WCAG AA)
- **Image Optimization**: Apply `filter: brightness(0.8) contrast(1.1)` in dark mode

### JavaScript Standards
- Use modern ES6+ syntax where supported
- Maintain jQuery compatibility for Bootstrap components
- Add error handling for AJAX calls
- Use meaningful variable names
- Consider theme switching functionality if needed

## Modern Dark Theme Requirements

### CSS Custom Properties Structure
```css
:root {
  /* Semantic color variables */
  --text-primary: #212529;    /* Light mode */
  --bg-body: #ffffff;
  --color-primary: #007bff;
}

@media (prefers-color-scheme: dark) {
  :root {
    --text-primary: #e0e0e0;  /* Dark mode */
    --bg-body: #121212;
    --color-primary: #4d94ff;
  }
}
```

### Color Guidelines
- **Light Mode**: Use standard Bootstrap colors
- **Dark Mode**: Use Material Design dark theme colors (#121212 background)
- **Desaturated Colors**: Reduce saturation in dark mode to prevent eye strain
- **Off-Black/Off-White**: Avoid pure black (#000000) and pure white (#ffffff)

### Browser Support
- **CSS Custom Properties**: Supported in all modern browsers
- **prefers-color-scheme**: Supported in Safari, Chrome, Firefox, Edge
- **color-scheme**: Add meta tag for browser UA styling

## Testing Requirements
- Unit tests for all business logic
- Integration tests for controllers
- UI tests for critical user flows
- **Theme Testing**: Test both light and dark modes
- **System Preference Testing**: Verify automatic theme switching
- **Accessibility Testing**: Use contrast analyzers and screen readers

## Performance Considerations
- Minimize CSS bundle size with efficient Custom Properties
- Optimize images for web with dark mode filters
- Use CDN for external libraries
- Enable compression in Azure App Service
- **Theme Switching**: Ensure smooth transitions without layout shifts