# TypeScript Interview Questions — Basic

## 1. What is TypeScript?

**Answer:**  
TypeScript is a superset of JavaScript that adds static typing. It helps catch errors during development and makes code easier to maintain.

**Follow-up:** Does TypeScript run directly in the browser?

**Answer:**  
No. TypeScript is compiled/transpiled into JavaScript, which runs in the browser or Node.js.

---

## 2. JavaScript vs TypeScript?

**Answer:**  
JavaScript is dynamically typed, while TypeScript adds static typing and catches many type errors during development.

---

## 3. What is type inference?

**Answer:**  
Type inference means TypeScript automatically determines the type of a variable.

```ts
let name = "Soumay";
```

TypeScript knows `name` is a `string`.

---

## 4. What is `type` vs `interface`?

**Answer:**  
Both can define object structures. `interface` is commonly used for object contracts, while `type` is more flexible and can define unions, intersections, primitives, etc.

---

## 5. What is a union type?

**Answer:**  
A union allows a value to have multiple possible types.

```ts
let id: string | number;
```

Here, `id` can be a `string` or `number`.

---

## 6. What is an intersection type?

**Answer:**  
An intersection combines multiple types using `&`.

```ts
type A = { name: string };
type B = { age: number };

type User = A & B;
```

`User` must have both properties.

---

## 7. What is `any`?

**Answer:**  
`any` disables TypeScript's type checking for that value. It should generally be avoided when possible.

---

## 8. What is `unknown`?

**Answer:**  
`unknown` represents a value whose type isn't known. We must check its type before using it.

---

## 9. `any` vs `unknown`?

**Answer:**  
`any` removes type safety, while `unknown` requires type checking before use.

---

## 10. What are generics?

**Answer:**  
Generics allow us to write reusable code that works with different types while maintaining type safety.

```ts
function identity<T>(value: T): T {
  return value;
}
```

---

## 11. What is a type guard?

**Answer:**  
A type guard is a check that helps TypeScript determine the specific type of a value.

```ts
if (typeof value === "string") {
  // value is string
}
```

---

## 12. What is type narrowing?

**Answer:**  
Type narrowing means reducing a broader type to a more specific type using checks such as `typeof`, `instanceof`, or `in`.

---

## 13. What is `void`?

**Answer:**  
`void` is commonly used as the return type of a function that doesn't return a value.

```ts
function log(): void {
  console.log("Hello");
}
```

---

## 14. What is `never`?

**Answer:**  
`never` represents a value that never occurs.

```ts
function error(): never {
  throw new Error("Failed");
}
```

---

## 15. What is `keyof`?

**Answer:**  
`keyof` creates a union of the keys of a type.

```ts
interface User {
  name: string;
  age: number;
}

type UserKey = keyof User;
// "name" | "age"
```

---

## 16. What is `Partial<T>`?

**Answer:**  
`Partial<T>` makes all properties of a type optional.

```ts
interface User {
  name: string;
  age: number;
}

type UpdateUser = Partial<User>;
```

Useful for update operations.

---

## 17. What is `Pick<T, K>`?

**Answer:**  
`Pick` creates a type containing only selected properties.

```ts
type UserPreview = Pick<User, "name">;
```

---

## 18. What is `Omit<T, K>`?

**Answer:**  
`Omit` creates a type while removing selected properties.

```ts
type PublicUser = Omit<User, "age">;
```

---

## 19. What is `Readonly<T>`?

**Answer:**  
`Readonly<T>` prevents properties from being reassigned.

```ts
const user: Readonly<User> = {
  name: "Soumay",
  age: 25
};
```

---

## 20. What are generics useful for?

**Answer:**  
They are useful for creating reusable and type-safe functions, components, hooks, and API utilities.

---

# TypeScript Interview Questions — Important Intermediate

## 21. What is a generic constraint?

**Answer:**  
A generic constraint restricts what types can be passed to a generic using `extends`.

```ts
function getLength<T extends { length: number }>(value: T) {
  return value.length;
}
```

---

## 22. What is `Record<K, T>`?

**Answer:**  
`Record` creates an object type with specific key and value types.

```ts
type Roles = Record<string, string>;

const roles: Roles = {
  admin: "Administrator",
  user: "User"
};
```

---

## 23. What is a type assertion?

**Answer:**  
A type assertion tells TypeScript to treat a value as a specific type.

```ts
const value: unknown = "Hello";

const text = value as string;
```

It does not perform runtime validation.

---

## 24. What is `as const`?

**Answer:**  
`as const` makes values readonly and preserves their literal types.

```ts
const status = "success" as const;
```

The type is `"success"` instead of `string`.

---

## 25. What is a tuple?

**Answer:**  
A tuple is an array with a fixed number of elements and specific types for each position.

```ts
let user: [string, number] = ["Soumay", 25];
```

---

## 26. How do you type a function in TypeScript?

**Answer:**  
We can specify the parameter types and return type.

```ts
function add(a: number, b: number): number {
  return a + b;
}
```

---

## 27. What are optional properties?

**Answer:**  
An optional property uses `?` and may or may not exist.

```ts
interface User {
  name: string;
  age?: number;
}
```

---

## 28. What is a discriminated union?

**Answer:**  
It is a union of types that share a common property used to identify the specific type.

```ts
type Result =
  | { status: "success"; data: string }
  | { status: "error"; message: string };

function handle(result: Result) {
  if (result.status === "success") {
    console.log(result.data);
  }
}
```

---

## 29. What are mapped types?

**Answer:**  
Mapped types allow us to create a new type by transforming the properties of an existing type.

```ts
type User = {
  name: string;
  age: number;
};

type OptionalUser = {
  [K in keyof User]?: User[K];
};
```

---

## 30. What are conditional types?

**Answer:**  
Conditional types allow a type to depend on a condition.

```ts
type IsString<T> = T extends string ? true : false;
```

---

## 31. What is function overloading?

**Answer:**  
Function overloading allows a function to have multiple type signatures for different inputs.

```ts
function format(value: string): string;
function format(value: number): string;

function format(value: string | number): string {
  return String(value);
}
```

---

## 32. What is the difference between `interface` and `class`?

**Answer:**  
An `interface` defines the structure a value should follow, while a `class` defines an actual object with properties and methods and can be instantiated.

---

## 33. What is `strict` mode in TypeScript?

**Answer:**  
`strict` enables stronger type checking and helps catch more potential errors during development.

```json
{
  "compilerOptions": {
    "strict": true
  }
}
```

---

## 34. What is `tsconfig.json`?

**Answer:**  
`tsconfig.json` contains the configuration options for a TypeScript project, such as compiler settings, target JavaScript version, module system, and strictness.

---

## 35. What is `Promise<T>` in TypeScript?

**Answer:**  
`Promise<T>` represents a promise that will eventually resolve to a value of type `T`.

```ts
async function getUser(): Promise<User> {
  // ...
}
```

---

## 36. How do you type an API response?

**Answer:**  
We can create an interface or type representing the expected response.

```ts
interface User {
  id: number;
  name: string;
}

async function getUsers(): Promise<User[]> {
  const response = await fetch("/api/users");
  return response.json();
}
```

---

## 37. Does TypeScript validate API responses at runtime?

**Answer:**  
No. TypeScript only provides compile-time type checking. External API data may still need runtime validation.

---

## 38. How do you type React component props?

**Answer:**  
We can use an interface or type for the props.

```tsx
interface ButtonProps {
  title: string;
  disabled?: boolean;
}

function Button({ title, disabled }: ButtonProps) {
  return <button disabled={disabled}>{title}</button>;
}
```

---

## 39. How do you type `useState` in React?

**Answer:**  
TypeScript can often infer simple state types. For complex state, we can explicitly provide the type.

```tsx
const [count, setCount] = useState<number>(0);
```

For objects:

```tsx
const [user, setUser] = useState<User | null>(null);
```

---

## 40. What is the difference between `null` and `undefined`?

**Answer:**  
`undefined` usually means a value has not been assigned or is missing, while `null` is an explicit representation of no value.

---

## 41. What is the non-null assertion operator `!`?

**Answer:**  
`!` tells TypeScript that a value is not `null` or `undefined`.

```ts
const element = document.getElementById("app")!;
```

It should be used carefully because it does not perform runtime validation.

---

## 42. What is an index signature?

**Answer:**  
An index signature allows an object to have dynamic keys.

```ts
interface Users {
  [key: string]: string;
}

const users: Users = {
  admin: "Soumay",
  user: "Rahul"
};
```

---

## 43. What is the difference between `interface` extension and intersection?

**Answer:**  
An interface can extend another interface using `extends`, while intersection types combine types using `&`.

```ts
interface User {
  name: string;
}

interface Employee extends User {
  employeeId: number;
}
```

---

## 44. What is structural typing in TypeScript?

**Answer:**  
TypeScript uses structural typing, meaning compatibility is based on the structure of a type rather than its name.

```ts
interface User {
  name: string;
}

const person = {
  name: "Soumay"
};

const user: User = person;
```

This works because `person` has the required structure.

---

## 45. Why is TypeScript useful in React projects?

**Answer:**  
TypeScript provides type safety for props, state, API responses, hooks, and functions. It also improves autocomplete and makes refactoring safer in large React applications.

---
