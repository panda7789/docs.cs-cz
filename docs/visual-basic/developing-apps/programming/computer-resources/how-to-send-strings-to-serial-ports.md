---
title: 'Postupy: Odesílání řetězců na sériové porty'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: b2051451142a7818a3b7d1bc564c5ae36b2579fe
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345590"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic

Toto téma popisuje `My.Computer.Ports` použití k odesílání řetězců do sériových portů počítače v jazyce Visual Basic.  
  
## <a name="example"></a>Příklad  

 Tento příklad odešle řetězec do sériového portu COM1. V počítači může být nutné použít jiný sériový port.  
  
 Pomocí `My.Computer.Ports.OpenSerialPort` metody získat odkaz na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 Blok `Using` umožňuje aplikaci zavřít sériový port i v případě, že generuje výjimku. Veškerý kód, který manipuluje se sériovým portem, `Try...Catch...Finally` by se měl objevit v tomto bloku nebo v rámci bloku.  
  
 Metoda <xref:System.IO.Ports.SerialPort.WriteLine%2A> odešle data do sériového portu.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Tento příklad předpokládá, že `COM1`počítač používá .  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento příklad předpokládá, že `COM1`počítač používá ; pro větší flexibilitu by měl kód umožnit uživateli vybrat požadovaný sériový port ze seznamu dostupných portů. Další informace naleznete v [tématu How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad `Using` používá blok a ujistěte se, že aplikace zavře port, i když vyvolá výjimku. Další informace naleznete [v tématu Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
