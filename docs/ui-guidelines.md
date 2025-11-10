# UI Guidelines

## Overview

This document outlines the user interface guidelines and design standards for the project.

## Component Library

### Material-UI Components

This project uses Material-UI (MUI) components for a consistent and professional user interface.

- Use Material-UI components wherever possible
- Follow Material Design principles
- Import components from `@mui/material`

**Required Components:**
- Buttons: Use `<Button>` component
- Forms: Use `<TextField>`, `<Select>`, `<Checkbox>`, etc.
- Layout: Use `<Container>`, `<Grid>`, `<Box>`
- Feedback: Use `<Snackbar>`, `<Alert>`, `<CircularProgress>`
- Navigation: Use `<AppBar>`, `<Drawer>`, `<Tabs>`

## Color Palette

### Primary Colors
- **Primary**: `#1976d2` (Blue)
- **Primary Dark**: `#115293`
- **Primary Light**: `#42a5f5`

### Secondary Colors
- **Secondary**: `#dc004e` (Pink/Red)
- **Secondary Dark**: `#9a0036`
- **Secondary Light**: `#e33371`

### Neutral Colors
- **Background**: `#f5f5f5` (Light Gray)
- **Surface**: `#ffffff` (White)
- **Text Primary**: `rgba(0, 0, 0, 0.87)`
- **Text Secondary**: `rgba(0, 0, 0, 0.6)`
- **Divider**: `rgba(0, 0, 0, 0.12)`

### Status Colors
- **Success**: `#4caf50` (Green)
- **Warning**: `#ff9800` (Orange)
- **Error**: `#f44336` (Red)
- **Info**: `#2196f3` (Blue)

## Button Styles

### Variants
- **Contained**: Primary actions (e.g., Submit, Save, Create)
  ```jsx
  <Button variant="contained" color="primary">Submit</Button>
  ```
- **Outlined**: Secondary actions (e.g., Cancel, Reset)
  ```jsx
  <Button variant="outlined" color="primary">Cancel</Button>
  ```
- **Text**: Tertiary actions (e.g., Learn More, Skip)
  ```jsx
  <Button variant="text" color="primary">Learn More</Button>
  ```

### Sizes
- **Small**: For compact spaces
- **Medium**: Default size
- **Large**: For emphasis or hero sections

### States
- **Disabled**: Use `disabled` prop when action is unavailable
- **Loading**: Use `<CircularProgress>` with `disabled` state for async actions

## Accessibility Requirements

### WCAG 2.1 Level AA Compliance

#### Color Contrast
- Text on background must have a contrast ratio of at least 4.5:1
- Large text (18pt+) must have a contrast ratio of at least 3:1
- UI components must have a contrast ratio of at least 3:1

#### Keyboard Navigation
- All interactive elements must be keyboard accessible
- Use proper tab order (logical flow)
- Provide visible focus indicators
- Support standard keyboard shortcuts (Enter, Space, Escape, Arrow keys)

#### Screen Reader Support
- Use semantic HTML elements
- Provide `aria-label` or `aria-labelledby` for all interactive elements
- Use `role` attributes when necessary
- Ensure form inputs have associated `<label>` elements
- Provide `alt` text for all images

#### Form Accessibility
- All form fields must have visible labels
- Use `<FormHelperText>` for additional instructions
- Provide clear error messages with `error` prop
- Use `required` attribute for mandatory fields
- Group related inputs with `<fieldset>` and `<legend>`

#### Focus Management
- Maintain logical focus order
- Return focus appropriately after modal/dialog closes
- Skip navigation links for keyboard users
- No keyboard traps

#### Responsive Design
- Support zoom up to 200% without horizontal scrolling
- Use relative units (rem, em) instead of fixed pixels
- Ensure touch targets are at least 44x44 pixels
- Support both portrait and landscape orientations

### Testing Requirements
- Test with keyboard only (no mouse)
- Test with screen readers (NVDA, JAWS, VoiceOver)
- Validate with accessibility tools (axe, Lighthouse)
- Ensure color blindness compatibility

## Typography

### Font Family
- Primary: `Roboto, "Helvetica Neue", Arial, sans-serif`
- Monospace: `"Courier New", Courier, monospace` (for code)

### Font Sizes
- **h1**: 2.5rem (40px)
- **h2**: 2rem (32px)
- **h3**: 1.75rem (28px)
- **h4**: 1.5rem (24px)
- **h5**: 1.25rem (20px)
- **h6**: 1rem (16px)
- **body1**: 1rem (16px)
- **body2**: 0.875rem (14px)
- **caption**: 0.75rem (12px)

## Spacing

Use Material-UI's spacing system based on 8px increments:
- `theme.spacing(1)` = 8px
- `theme.spacing(2)` = 16px
- `theme.spacing(3)` = 24px
- etc.

## Best Practices

1. **Consistency**: Use the same component for the same purpose throughout the app
2. **Feedback**: Provide clear visual feedback for user actions
3. **Simplicity**: Keep the interface clean and uncluttered
4. **Responsiveness**: Ensure the UI works on all screen sizes
5. **Performance**: Optimize for fast load times and smooth interactions
6. **Accessibility**: Always consider users with disabilities
