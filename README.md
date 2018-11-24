# Lua

The Lua programming language with some additional compile-time configuration
options.

See <https://www.lua.org> for more infomation on the Lua language.

All additional options are controlled by preprocessor defines in `luaconf.h`.

## Additional Configuration

### `LUA_DISABLE_FLOAT`

Disable all floating point support in Lua.  Only integers will be supported for
numeric operations.  This removes any dependency on the standard C library's
`<math.h>` as well.  Setting this will also remove the following features, which
require floating point support:

 * Floating point format specifiers for `string.format` (`A`, `a`, `E`, `e`,
   `f`, `G`, and `g`).
 * Floating point format specifiers for `string.pack`, `string.packsize`, and
   `string.unpack` (`f`, `d`, and `n`).
 * Floating point literals (e.g `-3.5` or `7e5`).
 * Floating point output of `collectgarbage("count")`.  Instead of a fractional
   value in kilobytes this call will return the total number of bytes as an
   integer.
 * The `^` (power) operator.
 * The zero-parameter form of `math.random`.  The function will always require
   one or two parameters.
 * `math.acos`
 * `math.asin`
 * `math.atan2`
 * `math.atan`
 * `math.ceil`
 * `math.cos`
 * `math.cosh`
 * `math.deg`
 * `math.exp`
 * `math.floor`
 * `math.fmod`
 * `math.frexp`
 * `math.huge`
 * `math.ldexp`
 * `math.log10`
 * `math.log`
 * `math.modf`
 * `math.pi`
 * `math.pow`
 * `math.rad`
 * `math.sin`
 * `math.sinh`
 * `math.sqrt`
 * `math.tan`
 * `math.tanh`
