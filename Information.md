Certainly! Here's a modernized version of the documentation with improved examples:

---

## Ephemeral Macros

Welcome to the documentation for Ephemeral, a powerful toolset designed to enhance the security, speed, and functionality of your Lua scripts. Below, you'll find comprehensive details on each macro available within the Ephemeral framework.

### Getting Started

To seamlessly integrate Ephemeral macros into your Lua scripts, follow these guidelines:

- Macros should be globally defined.
- Use the `function(...) return ... end` pattern to define macros.
- During testing, define macros to 'do nothing' to avoid errors in unobfuscated scripts. These definitions will be automatically removed during obfuscation.

Let's delve into the Ephemeral macros:

### EPH_ENCSTR

**Description:** Encrypts a string constant using an advanced encryption algorithm.

**Aliases:** EPH_STRENC

**Example:**
```lua
-- Encrypting sensitive information
local encryptedString = EPH_ENCSTR("Confidential Data")
print(EPH_ENCSTR("Hello, World!")) -- Encrypting a simple greeting
return EPH_ENCSTR("Goodbye!") -- Encrypting a farewell message
```

### EPH_ENCNUM

**Description:** Encrypts a number constant using a sophisticated encryption algorithm.

**Aliases:** EPH_NUMENC

**Example:**
```lua
-- Encrypting numerical values
local encryptedNumber = EPH_ENCNUM(1000)
print(EPH_ENCNUM(1), EPH_ENCNUM(1.0)) -- Encrypting integers and floats
return EPH_ENCNUM(1E100) -- Encrypting scientific notation
```

### EPH_CRASH

**Description:** Safely crashes the VM and disrupts the VM context.

**Example:**
```lua
-- Crashing the virtual machine
EPH_CRASH() -- Crash without returning anything
return EPH_CRASH() -- Crash and return from the script
```

### EPH_JIT

**Description:** Optimizes a given function for significantly faster execution.

**Aliases:** EPH_JIT_MAX (applies more aggressive optimizations)

**Example:**
```lua
-- JIT optimizing functions
local myFunction = EPH_JIT(function() end) -- Optimizing an empty function
EPH_JIT(function() end)() -- Executing an optimized function
someFunction(EPH_JIT(function() end)) -- Passing an optimized function as an argument
```

### EPH_NO_VIRTUALIZE

**Description:** Disables obfuscation for specific sections of code.

**Example:**
```lua
-- Disabling obfuscation for certain code blocks
local myFunction = EPH_NO_VIRTUALIZE(function() end) -- Disabling obfuscation for an empty function
EPH_NO_VIRTUALIZE(function() end)() -- Executing a non-obfuscated function
someFunction(EPH_NO_VIRTUALIZE(function() end)) -- Passing a non-obfuscated function as an argument
```

### EPH_NO_UPVALUES

**Description:** Wraps a function with 0 upvalues to fix bugs related to high upvalue counts.

**Example:**
```lua
-- Fixing bugs related to upvalue counts
local myFunction = EPH_NO_UPVALUES(function() end) -- Wrapping a function with 0 upvalues
EPH_NO_UPVALUES(function() end)() -- Executing the function with no upvalues
someFunction(EPH_NO_UPVALUES(function() end)) -- Passing the function with 0 upvalues as an argument
```

### EPH_OBFUSCATED

**Description:** A constant value set as true during obfuscation.

**Example:**
```lua
-- Conditional execution based on obfuscation
if EPH_OBFUSCATED then
    validateWhitelist() -- This code will only run during obfuscation.
else
    skipWhitelist() -- This code will only run when the script is not obfuscated.
end
```
