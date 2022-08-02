# 2022XojoDelegate
Create a Delegate for programming graphics using Xojo 2022 r2

This is the code to make a delegate to draw a stick person
  - Compatible with Windows 11
  - Xojo IDE: 2022 r2
  - Xojo API: API 2
  - Level: Advanced
  
  Youtube video:
[![Xojo Plugin Creation from Scratch](https://github.com/eugenedakin/2022XojoPlugin/blob/main/PluginScreenUpdated.png)](https://youtu.be/Ap3Ufre_RXk)

Instructions:
- Install Xojo 2022 r 2
- Run the xojo_binary-project

AddTwoDLL.h file
```C++
#include "WinHeader++.h"
#include "rb_plugin.h"

RBInteger AddTwo(RBInteger x, RBInteger y);

REALmethodDefinition TestModuleMethods[] = {
	{ (REALproc)AddTwo, REALnoImplementation, "AddTwo(x as integer, y as integer) as integer", REALconsoleSafe },
};
```

AddTwoDLL.cpp file
```C++
#include "AddTwoDLL.h"

RBInteger AddTwo(RBInteger x, RBInteger y) {
	return x + y;
}

REALmoduleDefinition AddTwodefn = {
	kCurrentREALControlVersion,
	"AddTwoDLL", //name of module shown to user
	TestModuleMethods, //method names
	sizeof(TestModuleMethods) / sizeof(REALmethodDefinition), //size of methods
	nil, //no constants
	nil, //no properties
};

void PluginEntry(void) {
	REALRegisterModule(&AddTwodefn);
}
```

The file: AddTwoNum.dll can be downloaded and placed in the Xojo 2022 r1.1 plugin folder.

Xojo code
```xojo
Sub Pressed() Handles Pressed
  Var Answer As Integer
  Answer = AddTwoDLL.AddTwo(4,9)
  Label1.Text = Answer.ToString
End Sub
```
