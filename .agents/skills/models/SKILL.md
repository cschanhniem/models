```markdown
# models Development Patterns

> Auto-generated skill from repository analysis

## Overview
This skill teaches the core development patterns and conventions used in the `models` Python repository. The codebase is framework-agnostic, focusing on consistent file organization, import/export styles, and lightweight, testable modules. You'll learn how to structure files, write imports and exports, and follow the project's conventions for maintainable and readable code.

## Coding Conventions

### File Naming
- Use **snake_case** for all Python files.
  - Example: `user_model.py`, `data_processor.py`

### Import Style
- Prefer **relative imports** within the package.
  - Example:
    ```python
    from .base_model import BaseModel
    from .utils import process_data
    ```

### Export Style
- Use **named exports** (explicitly define what is exported).
  - Example:
    ```python
    __all__ = ['UserModel', 'process_data']
    ```

### Commit Messages
- Freeform, concise messages (~21 characters on average).
  - Example: `fix bug in data loader`

## Workflows

### Adding a New Model
**Trigger:** When you need to introduce a new data model.
**Command:** `/add-model`

1. Create a new Python file in snake_case (e.g., `order_model.py`).
2. Define your model class.
    ```python
    class OrderModel:
        ...
    ```
3. Use relative imports for dependencies.
    ```python
    from .base_model import BaseModel
    ```
4. Add your class to `__all__` for named export.
    ```python
    __all__ = ['OrderModel']
    ```

### Running Tests
**Trigger:** When you want to verify code correctness.
**Command:** `/run-tests`

1. Identify test files (pattern: `*.test.*`).
2. Use the project's preferred test runner (framework not specified; check project docs or use `pytest` as default).
    ```bash
    pytest
    ```
3. Review test output and address failures.

### Refactoring Imports
**Trigger:** When reorganizing code or resolving import issues.
**Command:** `/refactor-imports`

1. Change absolute imports to relative imports within the package.
    ```python
    # Before
    from base_model import BaseModel

    # After
    from .base_model import BaseModel
    ```
2. Update all affected files.
3. Run tests to ensure nothing is broken.

## Testing Patterns

- Test files follow the pattern `*.test.*` (e.g., `user_model.test.py`).
- Testing framework is unspecified; use standard Python testing tools like `pytest` or `unittest`.
- Place tests alongside or near the modules they test for easy discovery.

  Example test file:
  ```python
  # user_model.test.py
  from .user_model import UserModel

  def test_user_creation():
      user = UserModel(name="Alice")
      assert user.name == "Alice"
  ```

## Commands
| Command         | Purpose                                 |
|-----------------|-----------------------------------------|
| /add-model      | Scaffold and add a new model module     |
| /run-tests      | Run all test files in the repository    |
| /refactor-imports | Convert absolute imports to relative   |
```
