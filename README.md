# Unit Lua API Documentation

## Reflection Functions
```lua
<function> loadstring(<string> chunk)
```
Loads *chunk* as a lua script, and returns it if compiled successfully. If there's an error, the error message will be returned.

```lua
<bool> islclosure(<function> f)
```
Returns *true or false* based on if *f* is an LClosure.

## Environment Functions
```lua
<table> getgenv(<void>)
```
Returns the environment that is applied to each script executed.

```lua
<table> getrenv(<void>)
```
Returns the global environment for the LocalScript state.

```lua
<table> getreg(<void>)
```
Returns the Lua registry.

## Hooking Functions
```lua
<function> newcclosure(<function> f)
```
Pushes a new CClosure that uses function *f* upon calling.
