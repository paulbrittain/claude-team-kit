---
name: no-inline-imports
description: Use when writing, editing, or reviewing any module's code - enforces keeping imports at the top of the file and avoiding inline imports inside function bodies, type annotations, or interface fields.
---

# No inline imports

Always place imports at the top of the module. Avoid inline imports in function bodies, type annotations, or interface fields unless there is a strict circular-dependency reason and it is documented in a code comment at the import site.

## Apply when

- Writing new modules.
- Adding new dependencies to an existing module.
- Reviewing diffs that introduce `require(...)` or dynamic `import(...)` inside function bodies, or `import type` references inline.

## Exceptions

Inline import is acceptable only when:
- Required to break a documented circular dependency, with a comment explaining why.
- Lazy-loading is intentional and measurable (e.g., bundle-size sensitive code paths).
