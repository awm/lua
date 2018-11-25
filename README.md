# Lua

The Lua programming language with some additional compile-time configuration
options.

See [lua.org](https://www.lua.org) for more infomation on the Lua language.

All additional options are controlled by preprocessor defines in
[`luaconf.h`][luaconf.h].

## Additional Configuration

### `LUA_DISABLE_FLOAT`

Disable all floating point support in Lua.  Only integers will be supported for
numeric operations.  This removes any dependency on the standard C library's
`<math.h>`.  Setting this will also remove the following features, which require
floating point support:

 * Floating point format specifiers for [`string.format`][string.format] (`A`,
   `a`, `E`, `e`, `f`, `G`, and `g`).
 * Floating point format specifiers for [`string.pack`][string.pack],
   [`string.packsize`][string.packsize], and [`string.unpack`][string.unpack]
   (`f`, `d`, and `n`).
 * Floating point literals (e.g `-3.5` or `7e5`).
 * Floating point output of [`collectgarbage("count")`][collectgarbage].
   Instead of a fractional value in kilobytes this call will return the total
   number of bytes as an integer.
 * The `^` (power) operator.
 * The zero-parameter form of [`math.random`][math.random].  The function will
   always require one or two parameters.
 * [`math.acos`][math.acos]
 * [`math.asin`][math.asin]
 * `math.atan2`
 * [`math.atan`][math.atan]
 * [`math.ceil`][math.ceil]
 * [`math.cos`][math.cos]
 * `math.cosh`
 * [`math.deg`][math.deg]
 * [`math.exp`][math.exp]
 * [`math.floor`][math.floor]
 * [`math.fmod`][math.fmod]
 * `math.frexp`
 * [`math.huge`][math.huge]
 * `math.ldexp`
 * `math.log10`
 * [`math.log`][math.log]
 * [`math.modf`][math.modf]
 * [`math.pi`][math.pi]
 * `math.pow`
 * [`math.rad`][math.rad]
 * [`math.sin`][math.sin]
 * `math.sinh`
 * [`math.sqrt`][math.sqrt]
 * [`math.tan`][math.tan]
 * `math.tanh`

## `LUA_DISABLE_FS`

Disable file system support in Lua.  It is still possible to create io file
objects in C code and pass them to Lua scripts.  The standard streams (`stdin`,
`stdout`, and `stderr`) will continue to exist.  Setting this will remove the
following features, which require file system support:

 * The ability to pass a string containing a file name to be opened to
   [`io.input`][io.input],  [`io.lines`][io.lines], or [`io.output`][io.output].
 * [`dofile`][dofile]
 * [`io.open`][io.open]
 * [`io.tmpfile`][io.tmpfile]
 * [`loadfile`][loadfile]
 * `module`
 * [`os.remove`][os.remove]
 * [`os.rename`][os.rename]
 * [`os.tmpname`][os.tmpname]
 * [`package.config`][package.config]
 * [`package.cpath`][package.cpath]
 * [`package.loadlib`][package.loadlib]
 * [`package.path`][package.path]
 * [`package.preload`][package.preload]
 * [`package.searchers`][package.searchers]
 * [`package.searchpath`][package.searchpath]
 * [`require`][require]
 * `seeall`

**Note:** this option does _not_ remove the ability to load Lua files from
within C code (for example, using `luaL_loadfile`).


[collectgarbage]:       <https://www.lua.org/manual/5.3/manual.html#pdf-collectgarbage>
[dofile]:               <https://www.lua.org/manual/5.3/manual.html#pdf-dofile>
[io.input]:             <https://www.lua.org/manual/5.3/manual.html#pdf-io.input>
[io.lines]:             <https://www.lua.org/manual/5.3/manual.html#pdf-io.lines>
[io.open]:              <https://www.lua.org/manual/5.3/manual.html#pdf-io.open>
[io.output]:            <https://www.lua.org/manual/5.3/manual.html#pdf-io.output>
[io.tmpfile]:           <https://www.lua.org/manual/5.3/manual.html#pdf-io.tmpfile>
[loadfile]:             <https://www.lua.org/manual/5.3/manual.html#pdf-loadfile>
[luaconf.h]:            <src/luaconf.h>
[math.acos]:            <https://www.lua.org/manual/5.3/manual.html#pdf-math.acos>
[math.asin]:            <https://www.lua.org/manual/5.3/manual.html#pdf-math.asin>
[math.atan]:            <https://www.lua.org/manual/5.3/manual.html#pdf-math.atan>
[math.ceil]:            <https://www.lua.org/manual/5.3/manual.html#pdf-math.ceil>
[math.cos]:             <https://www.lua.org/manual/5.3/manual.html#pdf-math.cos>
[math.deg]:             <https://www.lua.org/manual/5.3/manual.html#pdf-math.deg>
[math.exp]:             <https://www.lua.org/manual/5.3/manual.html#pdf-math.exp>
[math.floor]:           <https://www.lua.org/manual/5.3/manual.html#pdf-math.floor>
[math.fmod]:            <https://www.lua.org/manual/5.3/manual.html#pdf-math.fmod>
[math.huge]:            <https://www.lua.org/manual/5.3/manual.html#pdf-math.huge>
[math.log]:             <https://www.lua.org/manual/5.3/manual.html#pdf-math.log>
[math.modf]:            <https://www.lua.org/manual/5.3/manual.html#pdf-math.modf>
[math.pi]:              <https://www.lua.org/manual/5.3/manual.html#pdf-math.pi>
[math.rad]:             <https://www.lua.org/manual/5.3/manual.html#pdf-math.rad>
[math.random]:          <https://www.lua.org/manual/5.3/manual.html#pdf-math.random>
[math.sin]:             <https://www.lua.org/manual/5.3/manual.html#pdf-math.sin>
[math.sqrt]:            <https://www.lua.org/manual/5.3/manual.html#pdf-math.sqrt>
[math.tan]:             <https://www.lua.org/manual/5.3/manual.html#pdf-math.tan>
[os.remove]:            <https://www.lua.org/manual/5.3/manual.html#pdf-os.remove>
[os.rename]:            <https://www.lua.org/manual/5.3/manual.html#pdf-os.rename>
[os.tmpname]:           <https://www.lua.org/manual/5.3/manual.html#pdf-os.tmpname>
[package.config]:       <https://www.lua.org/manual/5.3/manual.html#pdf-package.config>
[package.cpath]:        <https://www.lua.org/manual/5.3/manual.html#pdf-package.cpath>
[package.loadlib]:      <https://www.lua.org/manual/5.3/manual.html#pdf-package.loadlib>
[package.path]:         <https://www.lua.org/manual/5.3/manual.html#pdf-package.path>
[package.preload]:      <https://www.lua.org/manual/5.3/manual.html#pdf-package.preload>
[package.searchers]:    <https://www.lua.org/manual/5.3/manual.html#pdf-package.searchers>
[package.searchpath]:   <https://www.lua.org/manual/5.3/manual.html#pdf-package.searchpath>
[require]:              <https://www.lua.org/manual/5.3/manual.html#pdf-require>
[string.format]:        <https://www.lua.org/manual/5.3/manual.html#pdf-string.format>
[string.pack]:          <https://www.lua.org/manual/5.3/manual.html#pdf-string.pack>
[string.packsize]:      <https://www.lua.org/manual/5.3/manual.html#pdf-string.packsize>
[string.unpack]:        <https://www.lua.org/manual/5.3/manual.html#pdf-string.unpack>
