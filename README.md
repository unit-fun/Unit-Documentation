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

## Keyboard & Mouse Functions
```lua
<void> keypress(<int> keycode)
```
Simulates a key press for *keycode*. More information about keycodes can be found here: http://keycode.info/

```lua
<void> mouse1click(<void>)
```
Simulates a left mouse click.

```lua
<void> mouse1press(<void>)
```
Simulates a left mouse press without releasing.

```lua
<void> mouse1release(<void>)
```
Simulates a left mouse release.

```lua
<void> mouse2click(<void>)
```
Simulates a right mouse click.

```lua
<void> mouse2press(<void>)
```
Simulates a right mouse press without releasing.

```lua
<void> mouse2release(<void>)
```
Simulates a right mouse release.

```lua
<void> mousemoverel(<int> x, <int> y)
```
Moves to cursor to the provided *x* and *y* coordinates.

## Hooking Functions
```lua
<function> newcclosure(<function> f)
```
Pushes a new CClosure that uses function *f* upon calling.
