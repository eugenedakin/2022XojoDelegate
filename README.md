# 2022XojoDelegate
Create a Delegate for programming graphics using Xojo 2022 r2

This is the code to make a delegate to draw a stick person
  - Compatible with Windows 11
  - Xojo IDE: 2022 r2
  - Xojo API: API 2
  - Level: Advanced
  
  Youtube video:
[![Xojo Plugin Creation from Scratch](https://github.com/eugenedakin/2022XojoDelegate/blob/main/DelegateDrawing.png)](https://youtu.be/jGfHhRTlrNY)

Instructions:
- Install Xojo 2022 r 2
- Run the xojo_binary-project

Delegate
```Xojo
Public Sub StickDrawDelegate(g as Graphics)
```

Pressed Button1 Action event
```Xojo
Sub Pressed() Handles Pressed
  //Make a new picture
  Var pic As New Picture(ImageViewer1.Width, ImageViewer1.Height)
  
  //Create a new variable
  Var d As StickDrawDelegate
  
  //Get address and invoke each item
  d = AddressOf DrawHead
  d.Invoke(pic.Graphics)
  
  d = AddressOf DrawBody
  d.Invoke(pic.Graphics)
  
  d = AddressOf DrawArms
  d.Invoke(pic.Graphics)
  
  d = AddressOf DrawLegs
  d.Invoke(pic.Graphics)
  
  //Show the drawn picture in the imageviewer
  ImageViewer1.Image = pic
End Sub
```

DrawArms Method
```Xojo
Public Sub DrawArms(g as Graphics)
  g.PenSize = 2
  g.DrawingColor = RGB(100, 100, 5)
  
  //Draw right arm
  g.drawline(125,125,150,150)
  
  //Draw left arm
  g.drawline(125,125,100,150)
End Sub
```
