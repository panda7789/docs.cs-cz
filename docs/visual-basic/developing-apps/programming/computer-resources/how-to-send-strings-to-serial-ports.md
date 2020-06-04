---
title: 'Postupy: Posílání řetězců na sériové porty'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: f78df9cf1bd75432ea645c4dcc06498915ceee49
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84360290"
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic

V tomto tématu se dozvíte, jak pomocí nástroje `My.Computer.Ports` odesílat řetězce na sériové porty počítače v Visual Basic.  
  
## <a name="example"></a>Příklad  

 Tento příklad odešle řetězec na sériový port COM1. V počítači možná budete muset použít jiný sériový port.  
  
 Použijte `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using`Blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku. Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku nebo v rámci `Try...Catch...Finally` bloku.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A>Metoda odesílá data do sériového portu.  
  
 [!code-vb[VbVbalrMyComputer#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#33)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
- V tomto příkladu se předpokládá, že počítač používá `COM1` .  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento příklad předpokládá, že počítač používá `COM1` ; pro větší flexibilitu by měl kód uživateli dovolit vybrat požadovaný sériový port ze seznamu dostupných portů. Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](how-to-show-available-serial-ports.md).  
  
 Tento příklad používá `Using` blok k ujištění, že aplikace uzavře port, i když vyvolá výjimku. Další informace naleznete v tématu [using – příkaz](../../../language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](how-to-show-available-serial-ports.md)
