# Code quality guidelines

!!!success "Status"
    Whole page reflects both branches.

A few guides onto how code contributed to Sokora should look like.

- Use `camelCase` for both variables and function names. Use `CONST_CASE` for constant values that are shared, exported or not.
- Use early returns to avoid nesting.
- Avoid non-nullish assertions, they are valid only when absolutely needed.
- Really try not to use ignore comments. The linter is (almost) always right.
- Prefer, when possible, `Promise.all` over having several `await` statements.

There's not a deep style guide since the `ql` task should be able to handle everything on its own.
