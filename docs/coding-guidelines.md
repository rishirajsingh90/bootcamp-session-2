# Coding Guidelines

## Overview

This document outlines the coding standards and best practices for the project. Following these guidelines ensures code consistency, maintainability, and quality across the codebase.

## General Formatting Rules

### Indentation
- Use **2 spaces** for indentation (no tabs)
- Be consistent with indentation throughout the file
- Ensure proper nesting and alignment

### Line Length
- Maximum line length: **100 characters**
- Break long lines at logical points
- Use proper indentation for continuation lines

### Whitespace
- Use blank lines to separate logical sections of code
- No trailing whitespace at the end of lines
- Include a newline at the end of each file
- Use spaces around operators: `a + b`, not `a+b`
- No space before function parentheses: `function myFunc()`, not `function myFunc ()`

### Naming Conventions

#### Variables and Functions
- Use **camelCase** for variables and functions
- Use descriptive, meaningful names
- Avoid single-letter names except for loops or callbacks
```javascript
// Good
const userName = 'John';
const calculateTotal = (items) => { /* ... */ };

// Bad
const un = 'John';
const calc = (i) => { /* ... */ };
```

#### Constants
- Use **UPPER_SNAKE_CASE** for constants
```javascript
const MAX_RETRY_ATTEMPTS = 3;
const API_BASE_URL = 'https://api.example.com';
```

#### Classes and Components
- Use **PascalCase** for classes and React components
```javascript
class UserProfile { /* ... */ }
const TaskList = () => { /* ... */ };
```

#### Files
- Use **kebab-case** for file names
- Match component name for React components
```
user-profile.js
task-list.js
TaskList.jsx  // Exception for React components
```

## Import Organization

### Import Order
Organize imports in the following order, with blank lines between groups:

1. **External libraries** (from node_modules)
2. **Internal modules** (project-specific utilities, services)
3. **Components** (React components)
4. **Styles** (CSS, SCSS files)
5. **Assets** (images, fonts, etc.)

```javascript
// External libraries
import React, { useState, useEffect } from 'react';
import { Button, TextField } from '@mui/material';
import axios from 'axios';

// Internal modules
import { apiService } from '../services/api-service';
import { formatDate } from '../utils/date-utils';

// Components
import TaskList from './TaskList';
import TaskItem from './TaskItem';

// Styles
import './App.css';
```

### Import Practices
- Use named imports when possible
- Avoid wildcard imports (`import * as`)
- Group related imports together
- Remove unused imports

## Linter Usage

### ESLint Configuration
- Follow the project's ESLint configuration
- Run the linter before committing code
- Address all linter errors and warnings
- Do not disable linter rules without justification

### Running the Linter
```bash
# Check for linting issues
npm run lint

# Auto-fix fixable issues
npm run lint -- --fix
```

### Common Rules
- No unused variables
- No console statements in production code
- Consistent quote style (prefer single quotes)
- Semicolons required at the end of statements
- No var declarations (use const or let)

## Best Practices

### DRY Principle (Don't Repeat Yourself)
- Avoid code duplication
- Extract common logic into reusable functions or components
- Use utility functions for repeated operations

```javascript
// Bad: Duplicated logic
const formatUserName = (user) => {
  return user.firstName + ' ' + user.lastName;
};
const formatAdminName = (admin) => {
  return admin.firstName + ' ' + admin.lastName;
};

// Good: Reusable function
const formatFullName = (person) => {
  return `${person.firstName} ${person.lastName}`;
};
```

### Single Responsibility Principle
- Each function should do one thing well
- Keep functions small and focused
- Break complex functions into smaller helpers

### Error Handling
- Always handle errors appropriately
- Use try-catch blocks for async operations
- Provide meaningful error messages
- Log errors for debugging

```javascript
try {
  const data = await fetchData();
  return data;
} catch (error) {
  console.error('Failed to fetch data:', error);
  throw new Error('Unable to load data. Please try again.');
}
```

### Code Comments
- Write self-documenting code with clear names
- Use comments to explain "why", not "what"
- Document complex algorithms or business logic
- Keep comments up to date with code changes

```javascript
// Good: Explains the reasoning
// Use exponential backoff to avoid overwhelming the server
const delay = Math.pow(2, retryCount) * 1000;

// Bad: States the obvious
// Increment the counter
counter++;
```

### Async/Await
- Prefer async/await over promise chains
- Always handle promise rejections
- Use Promise.all() for parallel operations

```javascript
// Good
const fetchUserData = async (userId) => {
  try {
    const user = await getUser(userId);
    const tasks = await getTasks(userId);
    return { user, tasks };
  } catch (error) {
    handleError(error);
  }
};
```

### Const vs Let
- Use `const` by default
- Use `let` only when reassignment is necessary
- Never use `var`

### Function Declarations
- Use arrow functions for callbacks and anonymous functions
- Use function declarations for named functions at module level
- Be consistent within a file or module

### Destructuring
- Use destructuring for objects and arrays when appropriate
- Makes code more readable and concise

```javascript
// Good
const { firstName, lastName, email } = user;
const [first, second, ...rest] = items;

// Less ideal
const firstName = user.firstName;
const lastName = user.lastName;
```

### Template Literals
- Use template literals for string interpolation
- Prefer template literals over string concatenation

```javascript
// Good
const greeting = `Hello, ${userName}!`;

// Bad
const greeting = 'Hello, ' + userName + '!';
```

## Code Organization

### File Structure
- Keep related code together
- Separate concerns (components, services, utils)
- Use index files to simplify imports
- Limit file size (aim for < 300 lines)

### Component Structure (React)
```javascript
// 1. Imports
import React, { useState } from 'react';

// 2. Component definition
const MyComponent = ({ prop1, prop2 }) => {
  // 3. Hooks
  const [state, setState] = useState(null);
  
  // 4. Event handlers
  const handleClick = () => { /* ... */ };
  
  // 5. Render
  return (
    <div>
      {/* JSX */}
    </div>
  );
};

// 6. Export
export default MyComponent;
```

## Code Review Standards

- Review code for adherence to these guidelines
- Provide constructive feedback
- Focus on code quality, not personal preferences
- Ensure tests are included with new features
- Verify documentation is updated

## Tools and Automation

### Prettier
- Use Prettier for automatic code formatting
- Run before committing code
- Configure to match project standards

### Git Hooks
- Use pre-commit hooks to run linter and formatter
- Ensure tests pass before committing
- Use conventional commit messages

### CI/CD
- Automated linting in CI pipeline
- Automated tests in CI pipeline
- Code coverage reports
- Block merges that fail quality checks

## Resources

- [JavaScript Style Guide](https://github.com/airbnb/javascript)
- [React Best Practices](https://react.dev/learn)
- [Clean Code Principles](https://github.com/ryanmcdermott/clean-code-javascript)
