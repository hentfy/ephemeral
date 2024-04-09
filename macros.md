
**Macros**

The ephemeral framework includes a set of macros designed to enhance security, optimize performance, and unlock additional features for your Lua scripts.

**Getting Started**

To ensure your unobfuscated script functions correctly while using ephemeral macros, you can define these macros within your script. During testing, these definitions ensure your script runs smoothly, and they are automatically removed during obfuscation.

The recommended way to define a macro is by assigning it a function that returns the same arguments.

Example for overriding EP_JIT:

```lua
EP_JIT = function(...) return ... end
```

**Macros**

The following macros are available within the ephemeral framework:

**EP_ENCSTR**

Encrypts the specified string constant using a stronger encryption algorithm.

Aliases: EP_STRENC

*Correct Usage:*

```lua
local myString = EP_ENCSTR("Important String")
print(EP_ENCSTR("Hello, World!"))
return EP_ENCSTR("Goodbye!")
```

*Incorrect Usage:*

```lua
local myString = EP_ENCSTR(variable) -- argument is not a constant.
print(EP_ENCSTR("A", "B")) -- too many arguments passed.
print(EP_ENCSTR()) -- not enough arguments passed.
```

**EP_ENCNUM**

Encrypts the specified number constant using a stronger encryption algorithm. Works on both doubles and integers (Lua 5.3+).

Aliases: EP_NUMENC

*Correct Usage:*

```lua
local myNumber = EP_ENCNUM(1000)
print(EP_ENCNUM(1), EP_ENCNUM(1.0))
return EP_ENCNUM(1E100)
```

*Incorrect Usage:*

```lua
local myString = EP_ENCNUM(variable) -- argument is not a constant.
print(EP_ENCNUM(0, 0)) -- too many arguments passed.
print(EP_ENCNUM()) -- not enough arguments passed.
```

**EP_CRASH**

Securely crashes the VM and corrupts the VM context.

*Correct Usage:*

```lua
EP_CRASH()
return EP_CRASH()
```

**EP_JIT**

Optimizes the passed function to run at exponentially higher speeds.

Aliases: EP_JIT_MAX (Applies more aggressive optimizations!)

*Correct Usage:*

```lua
local myFunction = EP_JIT(function() end)
EP_JIT(function() end)()
someFunction(EP_JIT(function() end))
```

*Incorrect Usage:*

```lua
EP_JIT(function() end) -- EP_JIT does not automatically call the passed function.
```

**EP_NO_VIRTUALIZE**

Disables obfuscation for certain sections of your code.

*Correct Usage:*

```lua
local myFunction = EP_NO_VIRTUALIZE(function() end)
EP_NO_VIRTUALIZE(function() end)()
someFunction(EP_NO_VIRTUALIZE(function() end))
```

*Incorrect Usage:*

```lua
EP_NO_VIRTUALIZE(function() end) -- EP_NO_VIRTUALIZE does not automatically call the passed function.
```

**EP_NO_UPVALUES**

Wraps the passed function in a proxy function with 0 upvalues to fix bugs caused by high upvalue counts.

*Correct Usage:*

```lua
local myFunction = EP_NO_UPVALUES(function() end)
EP_NO_UPVALUES(function() end)()
someFunction(EP_NO_UPVALUES(function() end))
```

*Incorrect Usage:*

```lua
EP_NO_UPVALUES(function() end) -- EP_NO_UPVALUES does not automatically call the passed function!
```

**EP_OBFUSCATED**

A constant value that is set as true during obfuscation.

*Correct Usage:*

```lua
if EP_OBFUSCATED then
	validateWhitelist()
else
	skipWhitelist()
end
```

*Incorrect Usage:*

```lua
EP_OBFUSCATED() -- EP_OBFUSCATED is a boolean value, not a function.
