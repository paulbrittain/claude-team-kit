---
name: typescript-exhaustive-switch
description: Use when writing or editing TypeScript switch statements over discriminated unions or enums - enforces an exhaustive `never` check in the default case so newly added variants produce compile-time failures until handled.
---

# TypeScript exhaustive switch

In switch statements over discriminated unions or enums, use a `never` check in the default case so newly added variants cause compile-time failures until handled.

## Pattern

```ts
function handle(event: Event) {
  switch (event.kind) {
    case "a":
      return doA(event);
    case "b":
      return doB(event);
    default: {
      const _exhaustive: never = event;
      throw new Error(`Unhandled event: ${JSON.stringify(_exhaustive)}`);
    }
  }
}
```

## Apply when

- Switching over a discriminated union (`type X = { kind: "a" } | { kind: "b" }`).
- Switching over a TypeScript `enum` or string-literal union.

Don't apply when the switch intentionally handles only a subset and falls through — but in that case prefer an `if` or a named helper rather than a non-exhaustive switch.
