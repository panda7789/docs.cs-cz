---
title: 'Postupy: Vytáčení čísel na modemech připojených k sériovým portům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345641"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Postupy: Vytáčení modemů připojených k sériovým portům v jazyce Visual Basic

This topic describes how to use `My.Computer.Ports` to dial a modem in Visual Basic.  
  
 Typically, the modem is connected to one of the serial ports on the computer. For your application to communicate with the modem, it must send commands to the appropriate serial port.  
  
### <a name="to-dial-a-modem"></a>To dial a modem  
  
1. Determine which serial port the modem is connected to. This example assumes the modem is on COM1.  
  
2. Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     The `Using` block allows the application to close the serial port even if it generates an exception. All code that manipulates the serial port should appear within this block, or within a `Try...Catch...Finally` block.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Set the `DtrEnable` property to indicate that the computer is ready to accept an incoming transmission from the modem.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Send the dial command and the phone number to the modem through the serial port by means of the <xref:System.IO.Ports.SerialPort.Write%2A> method.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 This code example is also available as an IntelliSense code snippet. In the code snippet picker, it is located in **Connectivity and Networking**. For more information, see [Code Snippets](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 This example requires a reference to the <xref:System?displayProperty=nameWithType> namespace.  
  
## <a name="robust-programming"></a>Robustní programování  

 This example assumes the modem is connected to COM1. We recommend that your code allow the user to select the desired serial port from a list of available ports. For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 This example uses a `Using` block to make sure that the application closes the port even if it throws an exception. For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 In this example, the application disconnects the serial port after it dials the modem. Realistically, you will want to transfer data to and from the modem. For more information, see [How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
