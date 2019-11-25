---
title: 'Postupy: Zobrazení dostupných sériových portů'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345578"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic

This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.  
  
 To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.  
  
## <a name="example"></a>Příklad  

 This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns. These strings are the names of the available serial ports on the computer.  
  
 Typically, a user selects which serial port the application should use from the list of available ports. In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control. For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 This code example is also available as an IntelliSense code snippet. In the code snippet picker, it is located in **Connectivity and Networking**. For more information, see [Code Snippets](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 This example requires:  
  
- A project reference to System.Windows.Forms.dll.  
  
- Access to the members of the <xref:System.Windows.Forms> namespace. Add an `Imports` statement if you are not fully qualifying member names in your code. For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.  
  
## <a name="robust-programming"></a>Robustní programování  

 You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names. Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control. If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.  
  
> [!NOTE]
> The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98. To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
