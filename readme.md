**Ephemeral Macros**

Welcome to the documentation for Ephemeral, a powerful toolset designed to enhance the security, speed, and functionality of your Lua scripts. Below, you'll find comprehensive details on each macro available within the Ephemeral framework.

**Getting Started**

To ensure seamless integration of Ephemeral macros into your Lua scripts, follow these guidelines:

- Macros should be globally defined.
- Use the function(...) return ... end pattern to define macros.
- During testing, define macros to 'do nothing' to avoid errors in unobfuscated scripts. These definitions will be automatically removed during obfuscation.

Let's delve into the Ephemeral macros:

**EPH_ENCSTR**
- Description: Encrypts a string constant using an advanced encryption algorithm.
- Aliases: EPH_STRENC
- Correct Usage:

```lua
local myString = EPH_ENCSTR("Sensitive Information")
print(EPH_ENCSTR("Hello, World!"))
return EPH_ENCSTR("Goodbye!")
```

**EPH_ENCNUM**
- Description: Encrypts a number constant using a sophisticated encryption algorithm.
- Aliases: EPH_NUMENC
- Correct Usage:

```lua
local myNumber = EPH_ENCNUM(1000)
print(EPH_ENCNUM(1), EPH_ENCNUM(1.0))
return EPH_ENCNUM(1E100)
```

**EPH_CRASH**
- Description: Safely crashes the VM and disrupts the VM context.
- No Aliases
- Correct Usage:

```lua
EPH_CRASH()
return EPH_CRASH()
```

**EPH_JIT**
- Description: Optimizes a given function for significantly faster execution.
- Aliases: EPH_JIT_MAX (applies more aggressive optimizations)
- Correct Usage:

```lua
local myFunction = EPH_JIT(function() end)
EPH_JIT(function() end)()
someFunction(EPH_JIT(function() end))
```

**EPH_NO_VIRTUALIZE**
- Description: Disables obfuscation for specific sections of code.
- No Aliases
- Correct Usage:

```lua
local myFunction = EPH_NO_VIRTUALIZE(function() end)
EPH_NO_VIRTUALIZE(function() end)()
someFunction(EPH_NO_VIRTUALIZE(function() end))
```

**EPH_NO_UPVALUES**
- Description: Wraps a function with 0 upvalues to fix bugs related to high upvalue counts.
- No Aliases
- Correct Usage:

```lua
local myFunction = EPH_NO_UPVALUES(function() end)
EPH_NO_UPVALUES(function() end)()
someFunction(EPH_NO_UPVALUES(function() end))
```

**EPH_OBFUSCATED**
- Description: A constant value set as true during obfuscation.
- No Aliases
- Correct Usage:

```lua
if EPH_OBFUSCATED then
    validateWhitelist() -- This code will only run during obfuscation.
else
    skipWhitelist() -- This code will only run when the script is not obfuscated.
end
```

This revised documentation provides a modern and streamlined overview of the Ephemeral macros, empowering you to enhance the security and performance of your Lua scripts.
