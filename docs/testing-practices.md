# Testing Practices

This document outlines the testing guidelines and practices for this project.

## Testing Philosophy

- Tests should give confidence that the code works as expected
- Tests should act as documentation for code behavior
- Tests should catch regressions early
- Tests should be maintainable and not brittle
- All new features should include appropriate tests

## Test Types

### Unit Tests

Unit tests focus on testing individual functions, components, or modules in isolation.

#### Guidelines for Unit Tests:

- Test one thing per test
- Mock external dependencies
- Keep tests fast and lightweight
- Focus on testing behavior rather than implementation details
- Use descriptive test names that explain the expected behavior
- Follow the AAA pattern (Arrange, Act, Assert)

### Integration Tests

Integration tests verify that different parts of the application work together correctly.

#### Guidelines for Integration Tests:

- Focus on testing the interaction between components
- Use minimal mocking, only for external services
- Test critical user flows
- Ensure different modules integrate correctly

### End-to-End Tests

End-to-End tests verify the application works correctly from a user's perspective, testing the entire application stack.

#### Guidelines for End-to-End Tests:

- Focus on critical user journeys
- Keep the number of E2E tests manageable
- Run E2E tests in a production-like environment
- Use stable selectors (data-testid attributes) for UI elements

## Testing Tools

### Frontend Testing

- Jest as the test runner and assertion library
- React Testing Library for testing React components
- Mock Service Worker for API mocking

### Backend Testing

- Jest as the test runner and assertion library
- Supertest for HTTP assertions

## Test Structure

### Naming Conventions

- Test files should be named similarly to the files they test with a `.test.js` suffix
- Place test files close to the code they test:
  - In a `__tests__` directory in the same directory as the code
  - Or with the same filename but with a `.test.js` extension

### Test Organization

Organize tests with describe blocks for logical grouping:

```javascript
describe('UserService', () => {
  describe('createUser', () => {
    it('should create a user with valid data', () => {
      // Test implementation
    });

    it('should throw an error with invalid data', () => {
      // Test implementation
    });
  });

  describe('getUserById', () => {
    it('should return user when found', () => {
      // Test implementation
    });
    
    it('should return null when user not found', () => {
      // Test implementation
    });
  });
});
```

## Writing Effective Tests

### The AAA Pattern

Structure tests using the Arrange-Act-Assert pattern:

```javascript
it('should calculate total price correctly with discount', () => {
  // Arrange: Set up test data and conditions
  const items = [
    { name: 'Item 1', price: 10 },
    { name: 'Item 2', price: 20 }
  ];
  const discount = 0.1;
  
  // Act: Perform the action being tested
  const result = calculateTotal(items, discount);
  
  // Assert: Verify the result is as expected
  expect(result).toBe(27); // (10 + 20) * (1 - 0.1) = 27
});
```

### Testing React Components

When testing React components, focus on user interactions and outcomes rather than implementation details:

```javascript
import { render, screen, fireEvent } from '@testing-library/react';
import UserForm from './UserForm';

describe('UserForm', () => {
  it('should call onSubmit with form data when submitted', () => {
    // Arrange
    const mockSubmit = jest.fn();
    render(<UserForm onSubmit={mockSubmit} />);
    
    // Act
    fireEvent.change(screen.getByLabelText(/name/i), {
      target: { value: 'John Doe' }
    });
    fireEvent.change(screen.getByLabelText(/email/i), {
      target: { value: 'john@example.com' }
    });
    fireEvent.click(screen.getByRole('button', { name: /submit/i }));
    
    // Assert
    expect(mockSubmit).toHaveBeenCalledWith({
      name: 'John Doe',
      email: 'john@example.com'
    });
  });
});
```

### Mocking

Use mocking judiciously to isolate the code being tested:

```javascript
// Mocking a module
jest.mock('../api/userApi');
import { fetchUser } from '../api/userApi';

// Setting up mock implementation
fetchUser.mockResolvedValue({ id: 1, name: 'John' });

// Verifying mock was called
expect(fetchUser).toHaveBeenCalledWith('1');
```

## Test Coverage

- Aim for high test coverage, but focus on critical paths first
- Use Jest's coverage reports to identify untested code
- Run coverage reports regularly:

```bash
npm test -- --coverage
```

## Continuous Integration

- All tests should run on each pull request
- PRs should not be merged if tests fail
- Tests should run quickly enough to provide fast feedback

## Debugging Tests

- Use `console.log` for simple debugging
- Use Jest's `--watch` mode during development
- Use the `debug()` function from Testing Library to see rendered output:

```javascript
const { debug } = render(<MyComponent />);
debug();
```

## Testing Asynchronous Code

Use async/await for testing asynchronous code:

```javascript
it('should load user data asynchronously', async () => {
  // Arrange
  const userId = '1';
  fetchUser.mockResolvedValue({ id: userId, name: 'John' });
  
  // Act
  const result = await loadUserData(userId);
  
  // Assert
  expect(result.name).toBe('John');
});
```

## Best Practices

1. **Test behaviors, not implementation details**
   - Focus on what the code does, not how it does it
   - This makes tests more resilient to refactoring

2. **Keep tests simple and readable**
   - Tests serve as documentation
   - Complex test code is harder to maintain

3. **Use test data factories**
   - Create helper functions to generate test data
   - This reduces duplication and makes tests more maintainable

4. **Clean up after tests**
   - Reset mocks between tests
   - Clean up any side effects

5. **Don't test third-party code**
   - Assume libraries work as documented
   - Focus on testing your application code

6. **Don't skip tests**
   - Fix failing tests rather than skipping them
   - Skipped tests often indicate underlying issues

7. **Run tests locally before committing**
   - This catches issues early and saves time
