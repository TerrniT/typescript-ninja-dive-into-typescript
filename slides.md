---
theme: default
background: https://source.unsplash.com/collection/94734566/1920x1080
class: text-center
highlighter: shiki
lineNumbers: true
drawings:
  persist: false
transition: slide-left
title: TypeScript Ninja Masterclass
mdc: true
---

# TypeScript Ninja Masterclass
Mastering the Art of Type-Safe Programming

<div class="pt-12">
  <span @click="$slidev.nav.next" class="px-2 py-1 rounded cursor-pointer" hover="bg-white bg-opacity-10">
    Press Space for next page <carbon:arrow-right class="inline"/>
  </span>
</div>

<!--
Test Notes
-->

---
layout: intro
---

# What We'll Cover

<v-clicks>

- Type System Fundamentals
- Advanced Type Features
- Best Practices & Patterns
- Real-world Applications

</v-clicks>

---
layout: default
---

# Type Inference Mastery

```ts {all|1|3-6|8-11|all}
let message = "Hello, TypeScript!"; // Type: string

const user = {
    name: "Alice",
    age: 30
}; // Type: { name: string; age: number }

function multiply(a: number, b: number) {
    return a * b;
} // Return type: number (inferred)
```

<v-clicks>

- TypeScript automatically infers types
- Reduces need for explicit annotations
- Makes code cleaner and more maintainable
- Still maintains type safety

</v-clicks>

---
layout: two-cols
---

# Interface Power

```ts {all|1-5|7-10|12-15|all}
interface User {
    id: number;
    name: string;
    email?: string; // Optional
}

const alice: User = {
    id: 1,
    name: "Alice"
};

interface Admin extends User {
    role: string;
    permissions: string[];
}
```

::right::

<div class="ml-4">

# Type Aliases

```ts {all|1-2|4-5|7-10|all}
type StringOrNumber = string | number;
type UserID = number | string;

// Union type usage
let id: UserID = "123";

type Theme = {
    primary: string;
    secondary: string;
};
```

</div>

---
layout: default
---

# Generics Excellence

```ts {all|1-3|5-11|13-19|all}
function identity<T>(arg: T): T {
    return arg;
}

class Container<T> {
    private value: T;

    constructor(value: T) {
        this.value = value;
    }
}

interface ApiResponse<T> {
    data: T;
    status: number;
    message: string;
}

const response: ApiResponse<User> = {
    data: { id: 1, name: "Alice" },
    status: 200,
    message: "Success"
};
```

---
layout: default
---

# Utility Types

```ts {all|1-4|6-7|9-10|12-13|all}
interface Todo {
    title: string;
    description: string;
    completed: boolean;
}

// Make all properties optional
type PartialTodo = Partial<Todo>;

// Pick specific properties
type TodoPreview = Pick<Todo, "title" | "completed">;

// Make all properties readonly
type ReadonlyTodo = Readonly<Todo>;
```

<v-clicks>

- `Partial<T>`: All properties optional
- `Pick<T, K>`: Select specific properties
- `Readonly<T>`: Make properties immutable
- `Record<K, T>`: Create key-value pairs

</v-clicks>

---
layout: default
---

# Type Guards & Narrowing

```ts {all|1-3|5-13|15-21|all}
type StringOrNumber = string | number;
type UserRole = "admin" | "user" | "guest";
type Nullable<T> = T | null;

function processValue(value: StringOrNumber) {
    if (typeof value === "string") {
        // TypeScript knows value is string here
        return value.toUpperCase();
    } else {
        // TypeScript knows value is number here
        return value.toFixed(2);
    }
}

function isAdmin(role: UserRole): role is "admin" {
    return role === "admin";
}

if (isAdmin(userRole)) {
    // TypeScript knows userRole is "admin" here
}
```

---
layout: fact
---

# "Type-safety isn't optional, it's a responsibility"

---
layout: default
---

# Best Practices

<v-clicks>

- Enable strict mode in `tsconfig.json`
- Avoid using `any` type
- Use interfaces for object shapes
- Leverage type inference
- Document with JSDoc comments
- Use type guards for runtime safety
- Prefer union types over enums
- Make immutability the default

</v-clicks>

---
layout: default
---

# Advanced Patterns

```ts {all|1-4|6-9|11-14|all}
// Conditional Types
type IsString<T> = T extends string ? true : false;
type CheckString = IsString<"hello">; // true
type CheckNumber = IsString<42>; // false

// Mapped Types
type ReadonlyFields<T> = {
    readonly [K in keyof T]: T[K];
};

// Template Literal Types
type EventName<T extends string> = `${T}Changed`;
type UserEvent = EventName<"user">; // "userChanged"
```

---
layout: center
class: text-center
---

# Thank You!

Become a TypeScript Ninja 🥷

[Documentation](https://www.typescriptlang.org/) · [GitHub](https://github.com/microsoft/TypeScript)
