# GEMINI.md - Project Context & Instructions

This file provides architectural context, development standards, and universal snippets for future AI interactions in this workspace.

---

## 1. Project Overview

**Name:** `@monorepo/let-me-test` (Monorepo) / `@packages/test-package-1` (Main Package)
**Purpose:** A TypeScript-based CLI application with an exported programmatic API.
**Architecture:** pnpm monorepo using [Turborepo](https://turbo.build/) for build orchestration.
**Key Technologies:**

- **Runtime:** Node.js (>=20)
- **Language:** TypeScript
- **CLI Framework:** [Commander.js](https://github.com/tj/commander.js)
- **Build Tool:** [tsdown](https://github.com/rolldown/tsdown)
- **Test Runner:** [Vitest](https://vitest.dev/)
- **Linting/Formatting:** ESLint, Prettier
- **Versioning:** [Changesets](https://github.com/changesets/changesets)
- **Git Hooks:** Husky, lint-staged

---

## 2. Directory Structure

- `/packages/test-package/`: The primary package.
  - `src/bin/app.ts`: CLI entry point.
  - `src/cli/`: Command and argument definitions.
  - `src/functions/`: Core logic and exported API.
  - `src/helpers/`: Shared options and utility functions.
  - `config/tsdownrc/`: Build configurations for dev/prod.
- `/configs/vitest/`: Shared testing configuration.
- `turbo.json`: Pipeline configuration for monorepo tasks.

---

## 3. Building, Running, and Testing

### Monorepo Level (Root)

- **Install:** `pnpm install`
- **Build All:** `pnpm build` (triggers `turbo build`)
- **Run Tests:** `pnpm test`
- **Lint All:** `pnpm lint`
- **Dev Mode:** `pnpm dev`

### Package Level (`/packages/test-package/`)

- **Build Dev:** `pnpm build:dev`
- **Build Prod:** `pnpm build:prod`
- **Test:** `pnpm test`
- **Link CLI globally:** `pnpm link-cli`

---

## 4. Development Conventions

- **Typing:** Use strict TypeScript. Define interfaces for CLI options and arguments.
- **Commits:** Use conventional commits via `commitsmile`.
- **Formatting:** Adhere to Prettier and ESLint rules (run `pnpm format` or `pnpm lint:fix` before committing).
- **Hooks:** Husky runs `lint-staged` on pre-commit. Do not bypass unless necessary.
- **File Headers:** Use the standardized comment blocks (see Snippets below) to section files.

---

## 5. Universal Snippets

Use these templates when generating or modifying code to maintain consistency with the user's IDE preferences.

### 1. Comment Block Outside

**Trigger:** `--`  
**Template:**

```javascript
// ----------------------
// ${1|Types,Functions,Classes,CONSTANTS,Errors,CLI APP|}
// ----------------------
```

### 2. Short Comment Block Outside

**Trigger:** `-`  
**Template:**

```javascript
// ----
// ${1|Variables,Methods,Constructor,Helpers|}
// ----
```

### 3. File Function Template

**Trigger:** `!-`  
**Template:**

```javascript
// ----------------------
// Types
// ----------------------

// ----------------------
// Functions
// ----------------------

export const $1 = () => {
  $0;
};
export default $1;
```

### 4. File Class Template

**Trigger:** `!-class`  
**Template:**

```javascript
// ----------------------
// Types
// ----------------------

// ----------------------
// Classes
// ----------------------

export class ${1:MyClass} {
	// ----
	// Variables
	// ----

	// ----
	// Constructor
	// ----

	constructor() {}

	// ----
	// Methods
	// ----
}

export default $1;
```
