A block in haxe starts with an opening curly brace `{` and ends with a closing curly brace `}`. A block may contain several expressions, each of which is followed by a semicolon `;`. The general syntax is thus:

```
{
	expr1;
	expr2;
	...
	exprN;
}
```
The value and by extension the type of a block-expression is equal to the value and the type of the last sub-expression.

Blocks can contain local variables declared by `var`-expression ([manual/var]), as well as local closures declared by `function`-expressions ([manual/Closure]). These are available within the block and within sub-blocks, but not outside the block. Also, they are available only after their declaration. The following example uses `var`, but the same rules apply to `function` usage:

```
{
	a; // error, a is not declared yet
	var a = 1; // declare a
	a; // ok, a was declared
	{
		a; // ok, a is available in sub-blocks
	}
	a; // ok, a is still available after sub-blocks
}
a; // error, a is not available outside
```
At runtime, blocks are evaluated from top to bottom. Control flow (e.g. exceptions ([manual/try_catch]) or return-expressions ([manual/return])) may leave a block before all expressions 
are evaluated.