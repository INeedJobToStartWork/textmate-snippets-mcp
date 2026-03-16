# Universal Snippets for Future Agents

This document contains translated TextMate snippets from the user's IDE. Future agents should use these templates when generating or modifying code within the specified contexts.

---

### 1. Comment Block Outside

**Trigger:** `--`  
**Context:** `javascript, typescript, javascriptreact, typescriptreact`  
**Template:**

```javascript
//----------------------
//${1|Types,Functions,Classes,CONSTANTS,Errors|}
//----------------------
$0;
```

**Placeholders:**

- `${1|...|}`: Choice list for the header title (Types, Functions, Classes, etc.).
- `$0`: Final cursor position after insertion.

**Example Usage:**

- **Input:** `--` (followed by selecting "Types")
- **Output:**

```javascript
//----------------------
//Types
//----------------------
| //cursor here
```

---

### 2. Short Comment Block Outside

**Trigger:** `-`  
**Context:** `javascript, typescript, javascriptreact, typescriptreact`  
**Template:**

```javascript
//----
//${1|Variables,Methods,Constructor,Helpers|}
//----
$0;
```

**Placeholders:**

- `${1|...|}`: Choice list for the sub-header title (Variables, Methods, etc.).
- `$0`: Final cursor position.

**Example Usage:**

- **Input:** `-` (followed by selecting "Methods")
- **Output:**

```javascript
//----
//Methods
//----
| //cursor here
```

---

### 3. File Function Template

**Trigger:** `!-`  
**Context:** `javascript, typescript, javascriptreact, typescriptreact`  
**Template:**

```javascript
//----------------------
//Types
//----------------------

//----------------------
//Functions
//----------------------

export const $1 = () => {
  $0;
};
export default $1;
```

**Placeholders:**

- `$1`: The name of the constant/function. It is used both in the declaration and the `export default`.
- `$0`: Final cursor position inside the function body.

**Example Usage:**

- **Input:** `!-` (typing "myFunction")
- **Output:**

```javascript
//----------------------
//Types
//----------------------

//----------------------
//Functions
//----------------------

export const myFunction = () => {
| //cursor here
}
export default myFunction;
```

---

### 4. File Class Template

**Trigger:** `!-class`  
**Context:** `javascript, typescript, javascriptreact, typescriptreact`  
**Template:**

```javascript
//----------------------
//Types
//----------------------

//----------------------
//Classes
//----------------------

export class ${1:MyClass} {
	//----
	//Variables
	//----

	//----
	//Constructor
	//----

	constructor() {}

	//----
	//Methods
	//----
}

export default $1;
```

**Placeholders:**

- `${1:MyClass}`: The class name (defaults to `MyClass`).
- `$1`: Mirrored placeholder for the `export default` statement.

**Example Usage:**

- **Input:** `!-class` (typing "UserService")
- **Output:**

```javascript
//----------------------
//Types
//----------------------

//----------------------
//Classes
//----------------------

export class UserService {
  //----
  //Variables
  //----

  //----
  //Constructor
  //----

  constructor() {}

  //----
  //Methods
  //----
}

export default UserService;
```
