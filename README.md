# Unit Lua API Documentation
### Quick Navigation
[Reflection Functions](#Reflection-Functions)\
[Table Modification Functions](#Table-Modification-Functions)\
[Keyboard and Mouse Functions](#Keyboard-and-Mouse-Functions)\
[Hooking Functions](#Hooking-Functions)\
[Unit Library](#Unit-Library)\
[Bit Library](#Bit-Library)\
[Drawing Library](#Drawing-Library)

## Reflection Functions
```lua
<function> loadstring(<string> chunk)
```
Loads *chunk* as a lua script, and returns it if compiled successfully. If there's an error, the error message will be returned.

```lua
<bool> islclosure(<function> f)
```
Returns *true or false* based on if *f* is an LClosure.

```lua
<bool> checkcaller(<void>)
```
Returns *true* if the current thread is used by Unit.

## Table Modification Functions
```lua
<table, nil> getrawmetatable(<T> value)
```
Retrieve the metatable of value regardless of value's metatable's *\_\_metatable* field. Returns *nil* if it doesn't exist.

```lua
<void> setreadonly(<table> table, <bool> bool)
```
Sets *table*'s read-only value to *bool*.

```lua
<void> make_readonly(<table> table)
```
Sets *table*'s read-only value to *true*.

```lua
<void> make_writeable(<table> table)
```
Sets *table*'s read-only value to *false*.

```lua
<bool> isreadonly(<table> table)
```
Returns *true or false* based off of *table*'s read-only condition.

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
<table> getsenv(<void>)
```
Grabs the enviorment of the script.

```lua
<table> getmenv(<void>)
```
Grabs the enviorment of the ModuleScript.

```lua
<table> getreg(<void>)
```
Returns the Lua registry.

```lua
<table> getgc(<bool [true or false]>)
```
Returns everything in the garbage collection in the form of a table, based on the bool.

```lua
<table> getinstances(<bool [true or false]>)
```
Returns a table of instances within the game.

```lua
<table> getnilinstances(<bool [true or false]>)
```
Returns a table of instances with the parent of Nil within the game.

## Keyboard and Mouse Functions
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
<void> mousemoveabs(<int> x, <int> y)
```
Moves to cursor to the provided *x* and *y* coordinates.

```lua
<void> mousemoverel(<int> x, <int> y)
```
Moves to cursor to the provided *x* and *y* coordinates.

## Hooking Functions
```lua
<function> newcclosure(<function> f)
```
Pushes a new CClosure that uses function *f* upon calling.

```lua
<function> hookfunction(<function> old, new)
```
Hooks *old* and returns *new* instead. [TEMPORARILY DISABLED]

## Misc Functions
```lua
<function> readfile(<string> filename)
```
Returns the contents of a file located in the *workspace* folder.

```lua
<function> writefile(<string> filename, <string> content)
```

```lua
<function> setthreadcontext(<int> identity)
```
Sets Unit's identity to *identity*

```lua
<void> setclipboard, toclipboard(<string> data)
```
Sets *data* to clipboard.

```lua
<string> getnamecallmethod(<void>)
```
Returns current namecall method.

```lua
<function> setnamecallmethod(<string> method)
```
Sets the provided namecall method.

```lua
<function> filteringbypass(<void>)
```
*Bypasses* filtering.

```lua
<function> virginitybypass(<void>)
```
Bypasses the virginity check located in RealLife.exe

```lua
<function> unitfingerprint(<void>)
```
Returns the HWID in a string form of the current user. Useful for making paid scripts/hubs.

```lua
<bool> isluau(<void>)
```
Returns a bool whether the game uses luau or not, (Used for pre-luau stage scripts)

```lua
<function> fireclickdetector(<userdata> instance, <int> times)
```
Fires the click detector of an *instance* by the amount of *times* set.

Example: ```lua
fireclickdetector(game.Workspace.WHATEVER.ClickDetector, 3)``` OR ```lua
for _,v in pairs(workspace:GetDescendants()) do
if v:IsA("ClickDetector") then
fireclickdetector(v)
end
end```

## Datamodel Library
```lua
<objects> game:GetObjects(<string> contenturl)
```
Returns an array of instances from the *contenturl*. For more information, visit the official roblox documentation; https://developer.roblox.com/en-us/api-reference/function/DataModel/GetObjects

```lua
<string> game:HttpGet(<string> url)
```
Returns content/text at *url*.

```lua
<string> game:HttpGetAsync(<string> url, <bool> cache)
```
Returns content/text at *url*, if *cache* is *true*, the request caches the response.

## Unit Library
```lua
<function> unit.require(<int> asset)
```
Similar to Roblox's native require function.

```lua
<function> unit.randomstring(<int> size)
```
Returns a random string generated by unit. [Example: print(unit.randomstring(5))]

```lua
<function> unit.secure(<string> data)
```
Secures the script in unit only format, no other executor will be able to run the secured script. [Example: setclipboard(unit.secure("print'hi'"))]

```lua
<function> unit.secure_run(<string> data)
```
Executes the script secured in unit only format. [Example: unit.secure_run(unit.secure("print'hi'"))]

```lua
<function> unit.base64.encode(<string> data)
```
Encodes a string into traditional Base64 format.

```lua
<function> unit.base64.decode(<string> data)
```
Decodes a string hashed in the traditional Base64 format.

```lua
<function> unit.binary.make(<int> number)
```
Returns the provided number in a binary form.

```lua
<function> unit.binary.reverse(<int> binary)
```
Returns the binary in its original form.

## Console Library
```lua
<function> console.log(<string> string)
```

```lua
<function> console.info(<string> string)
```

```lua
<function> console.warn(<string> string)
```

```lua
<function> console.error(<string> string)
```

## Bit Library

```lua
bit.tobit, bit.tohex, bit.bnot, bit.band, bit.bor, bit.bxor, bit.lshift, bit.rshift, bit.arshift, bit.rol, bit.ror, bit.bswap
```

Visit http://bitop.luajit.org/api.html for more information.

## Debug Library
```lua
debug.getregistry, debug.getmetatable, debug.setmetatable
```

Visit http://www.lua.org/manual/5.4/manual.html#6.10 for more information.

## Drawing Library
```lua
<drawable> DrawingLib.Create(<string> type)
```
Creates a new drawable object. *type* must be *"Circle"*, *"Line"*, *"Box"*, or *"Text"*.

```lua
<function> DrawingLib.Clear(<void>)
```
Clears the Drawing canvas.

```lua
<int> DrawingLib.DefaultFont
```
A value between *1* and *21*. Defaults to *21*

### Drawable (Base Class)
```lua
<string> ClassName [readonly]
```
The type of drawable.

```lua 
<Vector2> Position
```
The position of the drawable. (0, 0) represents the top left corner of the screen.

```lua
<Color3> Color
```
The color of the drawable.

```lua
<bool> Visible
```
The drawable's visibility.

```lua
<int> ZIndex
```
The drawable's layer. This integer can be 0 to 25. Drawables on higher layers render over drawables on lower layers.

```lua
<float> Transparency
```
A value from 0 to 1. A value of 1 meeans the drawable is transparent.

### Line
```lua
<Vector2> From
```
The line's start position.

```lua
<Vector2> To
```
The line's end position.

```lua
<float> Thickness
```
The line's thickness.

```lua
<float> Transparency
```
A value from 0 to 1. A value of 1 meeans the line is transparent.

### Text
```lua
<string> Text
```
The string to display

```lua
<string> Position
```
The text's position.

```lua
<float> Size
```
The text's font size.

```lua
<Color3> Color
```
The text's color.

```lua
<bool> Center
```
If *true*, text will be centered.

```lua
<bool> Outline
```
If *true*, text will be outlined.

```lua
<float> Transparency
```
A value from 0 to 1. A value of 1 meeans the text is transparent.

```lua
<Vector2> TextBounds [readonly]
```
The width and height of the text.

### Square
```lua
<Vector2> Position
```
The square's position.

```lua
<Vector2> Size
```
The square's size.

```lua
<Color3> Color
```
The square's color.

```lua
<float> Thickness
```
The square's thickness.

```lua
<bool> Filled
```
If *true*, the square will be filled.

```lua
<float> Transparency
```
A value from 0 to 1. A value of 1 meeans the square is transparent.

### Circle
```lua
<Vector2> Position
```
The circle's position.

```lua
<float> Radius
```
The circle's radius.

```lua
<Color3> Color
```
The circle's color.

```lua
<float> Thickness
```
The circle's thickness.

```lua
<bool> Filled
```
If *true*, the circle will be filled.

```lua
<float> Transparency
```
A value from 0 to 1. A value of 1 meeans the circle is transparent.

```lua
<int> NumSides
```
The circle's number of sides.

### Triangle
```lua
<Vector2> PointA
```
The triangle's first point location.

```lua
<Vector2> PointB
```
The triangle's second point location.

```lua
<Vector2> PointC
```
The triangle's third point location.

```lua
<Color3> Color
```
The triangle's color.

```lua
<float> Thickness
```
The triangle's thickness.


```lua
<bool> Filled
```
If *true*, the triangle will be filled.

```lua
<float> Transparency
```
A value from 0 to 1. A value of 1 meeans the triangle is transparent.
