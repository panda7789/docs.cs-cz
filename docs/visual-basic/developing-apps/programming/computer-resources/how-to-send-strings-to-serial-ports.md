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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345590"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic

V tomto tématu se dozvíte, jak pomocí `My.Computer.Ports` odeslat řetězce na sériové porty počítače v Visual Basic.  
  
## <a name="example"></a>Příklad  

 Tento příklad odešle řetězec na sériový port COM1. V počítači možná budete muset použít jiný sériový port.  
  
 K získání odkazu na port použijte metodu `My.Computer.Ports.OpenSerialPort`. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using` blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku. Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku nebo v rámci `Try...Catch...Finally`ho bloku.  
  
 Metoda <xref:System.IO.Ports.SerialPort.WriteLine%2A> odesílá data do sériového portu.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- Tento příklad předpokládá, že počítač používá `COM1`.  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento příklad předpokládá, že počítač používá `COM1`; pro větší flexibilitu by měl kód uživateli dovolit vybrat požadovaný sériový port ze seznamu dostupných portů. Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 V tomto příkladu se používá blok `Using` k zajištění toho, že aplikace uzavře port, i když vyvolá výjimku. Další informace naleznete v tématu [using – příkaz](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
