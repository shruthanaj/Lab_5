# Reflection: Static Code Analysis Lab

## Issue Documentation Table

| **Issue** | **Type** | **Line(s)** | **Description** | **Fix Approach** |
|------------|-----------|--------------|------------------|------------------|
| Mutable default argument (`logs=[]`) | Bug | 9 | Mutable default list shared between calls | Changed default to `None` and initialized inside function |
| Broad `except:` | Security / Maintainability | 20 | Hides all errors silently | Used specific `KeyError` and `ValueError` handling |
| Dangerous use of `eval()` | Security | 56 | Executes arbitrary code | Removed and replaced with a safe print statement |
| Missing file context management | Code Quality | 28–36 | Files opened manually without `with` | Used `with open()` context manager |
| Missing type validation | Logical Bug | 41–42 | Non-string item and invalid quantity | Added type checking and error logging |
| Unused import (`logging`) | Style | 2 | Import unused | Used for proper logging setup |

---

## Reflection Questions

### 1. Which issues were easiest and hardest to fix?
- **Easiest:** Fixing mutable default arguments and unused imports. They were straightforward syntax and style corrections.
- **Hardest:** Handling exceptions properly and removing `eval()` safely, since they required considering logic flow and security implications.

### 2. Any false positives from the tools?
- Yes, Pylint occasionally flagged some variable naming conventions (like short names `i`) which were acceptable in context (for loops). These can be considered false positives.

### 3. How to integrate static analysis in real development?
- Integrate **Pylint**, **Flake8**, and **Bandit** into CI/CD pipelines so every code commit is automatically checked.
- Set up pre-commit hooks to ensure code passes lint checks before merging.

### 4. Improvements observed after fixes:
- Code readability improved with logging and structured exceptions.
- Security improved by removing unsafe `eval()` and adding validation.
- Maintainability increased by eliminating hidden errors and enforcing consistent file handling.
