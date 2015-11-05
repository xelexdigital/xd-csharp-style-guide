# Xelex Digital's C# Style Guide

This guide was taken mostly from [Ray Wenderlich's](https://github.com/rwenderlich) very well structured [c-sharp-style-guide](https://github.com/raywenderlich/c-sharp-style-guide) with a bit closer adherence to [Microsoft's Coding Conventions](https://msdn.microsoft.com/en-us/library/ff926074.aspx). We're also utilizing [ASPNet's Engineering Guidelines](https://github.com/aspnet/Home/wiki/Engineering-guidelines#coding-guidelines) here.

## Quick Reference

#### Naming
- naming should follow [Microsoft's Guidelines](https://msdn.microsoft.com/en-us/library/ms229002(v=vs.110).aspx)

#### Layout
- one statement or declaration per line
- generally prefer curly braces on their own line, with exceptions
- no braces for single line conditional statements 
- always use braces for conditional statements spanning multiple lines
- one blank line between method definitions and property definitions
- 100 characters per line
- spaces for indentation rather than tabs
- indent 4 spaces
- indent an additional 4 spaces for line wraps

#### Language
- use `var` over explicit type where type can be inferred (`var foo = "bar";` over `string foo = "bar";`)
- avoid using `this` unless absolutely necessary
- use `_camelCase` for private fields
- specify member visiblity (`private string _foo;` not `string _foo;`)
- prefer C# type keywords over .NET type names (`string` over `String`)

## Table of Contents

- [Quick Reference](#quick-reference)
- [Nomenclature](#nomenclature)
  + [Namespaces](#namespaces)
  + [Classes & Interfaces](#classes--interfaces)
  + [Methods](#methods)
  + [Fields](#fields)
  + [Parameters](#parameters)
  + [Delegates](#delegates)
  + [Events](#events)
  + [Misc](#misc)
- [Declarations](#declarations)
  + [Access Level Modifiers](#access-level-modifiers)
  + [Fields & Variables](#fields--variables)
  + [Classes](#classes)
  + [Interfaces](#interfaces)
- [Spacing](#spacing)
  + [Indentation](#indentation)
  + [Line Length](#line-length)
  + [Vertical Spacing](#vertical-spacing)
- [Brace Style](#brace-style)
- [Switch Statements](#switch-statements)
- [Language](#language)
- [Copyright Statement](#copyright-statement)

## Nomenclature

On the whole, naming should follow C# standards.

### Namespaces

Namespaces are all __UpperCamelCase__, multiple words concatenated together,
without
hypens or underscores:

__BAD__:

```c#
com.webchartmd.fpsgame.hud.healthbar
```

__GOOD__:

```c#
WebChartMD.FPSGame.HUD.Healthbar
```

### Classes & Interfaces

Written in __UpperCamelCase__. For example `RadialSlider`. 

### Methods

Public methods are written in __UpperCamelCase__. For example `DoSomething`. 

Private methods are written in __lowerCamelCase__. For example: `doSometing`

### Fields

Written in __lowerCamelCase__.

Static fields should be written in __UpperCamelCase__:

```c#
public static int TheAnswer = 42;
```

Public and protected non-static fields are written __lowerCamelCase__.

For example:

```C#
public class MyClass 
{
  public int publicField;
  private int packagePrivate;
  private int myPrivate;
  protected int myProtected;
}
```

Use _camelCase for private fields.

__BAD:__

```c#
private int myPrivateVariable
```

__GOOD:__

```c#
private int _myPrivateVariable
```


### Parameters

Parameters are written in __lowerCamelCase__.

__BAD:__

```c#
private void doSomething(Vector3 Location)
```
__GOOD:__

```c#
private void doSomething(Vector3 location)
```

Single character values to be avoided except for temporary looping variables.

### Delegates

Delegats are written in __UpperCamelCase__.

When declaring delegates, DO add the suffix __EventHandler__ to names of delegates that are used in events. 

__BAD:__

```c#
public delegate void Click()
```
__GOOD:__

```c#
public delegate void ClickEventHandler()
```
DO add the suffix __Callback__ to names of delegates other than those used as event handlers.

__BAD:__

```c#
public delegate void Render()
```
__GOOD:__

```c#
public delegate void RenderCallback()
```
### Events

Prefix event methods with the prefix __On__.

__BAD:__

```c#
public static event CloseCallback Close;
```
__GOOD:__

```c#
public static event CloseCallback OnClose;
```

### Misc

In code, acronyms should be treated as words. For example:

__BAD:__

```c#
XMLHTTPRequest
string URL
findPostByID
```
__GOOD:__

```c#
XmlHttpRequest
string url
findPostById
```

## Declarations

### Access Level Modifiers

Access level modifiers should be explicitly defined for classes, methods and
member variables.

### Fields & Variables

Prefer single declaration per line.

__BAD:__

```c#
string username, twitterHandle;
```

__GOOD:__

```c#
string username;
string twitterHandle;
```

### Classes

Exactly one class per source file, although inner classes are encouraged where
scoping appropriate.

### Interfaces

All interfaces should be prefaced with the letter __I__. 

__BAD:__

```c#
RadialSlider
```

__GOOD:__

```c#
IRadialSlider
```

## Spacing

### Indentation

Indentation is using spaces - never tabs (configure VS to convert tabs to spaces).

#### Blocks

Indentation for blocks uses 4 spaces:

__BAD:__

```c#
for (int i = 0; i < 10; i++) {
  Debug.Log("index=" + i);
}

for (int i = 0; i < 10; i++) {
        Debug.Log("index=" + i);
}
```

__GOOD:__

```c#
for (int i = 0; i < 10; i++) {
    Debug.Log("index=" + i);
}
```

#### Line Wraps

Indentation for line wraps should use an additional 4 spaces from the originating line:

__BAD:__

```c#
CoolUiWidget widget =
        someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
        
CoolUiWidget widget =
  someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

__GOOD:__

```c#
CoolUiWidget widget =
    someIncrediblyLongExpression(that, reallyWouldNotFit, on, aSingle, line);
```

### Line Length

Lines should be no longer than 100 characters long.


### Vertical Spacing

There should be exactly one blank line between methods to aid in visual clarity 
and organization. Whitespace within methods should separate functionality, but 
having too many sections in a method often means you should refactor into
several methods.


## Brace Style

Curly braces are preferred on their own line, with exceptions for loops, 
object initialization and similar cases:

__BAD:__

```c#
class MyClass {
  void DoSomething() {
    if (someTest) {
      // ...
    } else {
      // ...
    }
  }
}
```

__GOOD:__

```c#
class MyClass
{
  void DoSomething()
  {
    if (someTest)
    {
      // ...
    }
    else
    {
      // ...
    }
  }
}
```

Singe line conditional statements don't uses braces, always use them over multiple lines.

__BAD:__

```c#
if (someTest)
  doSomething();
if (someTest) { doSomethingElse(); }
```

__GOOD:__

```c#
if (someTest) doSomething();
if (someTest) { 
  doSomethingElse();
}
```


## Switch Statements

Switch statements fall-through by default, but this can be unintuitive. Do not use fall-through behavior. 

Alway include the `default` case.

## Language

Use US English spelling.

__BAD:__

```c#
string colour = "red";
```

__GOOD:__

```c#
string color = "red";
```

## Copyright Statement

The following copyright statement should be included at the top of every source
file:

    /*
     * Copyright (c) 2015 Xelex Digital, LLC
     * 
     * Permission is hereby granted, free of charge, to any person obtaining a copy
     * of this software and associated documentation files (the "Software"), to deal
     * in the Software without restriction, including without limitation the rights
     * to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
     * copies of the Software, and to permit persons to whom the Software is
     * furnished to do so, subject to the following conditions:
     * 
     * The above copyright notice and this permission notice shall be included in
     * all copies or substantial portions of the Software.
     * 
     * THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
     * IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
     * FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
     * AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
     * LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
     * OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
     * THE SOFTWARE.
     */
