---
title: 'Postupy: Vytáčení čísel na modemech připojených k sériovým portům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: febec0a8579d34f8ff59066da5b5aa59c1cce6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345641"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Postupy: Vytáčení modemů připojených k sériovým portům v jazyce Visual Basic

Toto téma popisuje `My.Computer.Ports` použití k vytáčení modemu v jazyce Visual Basic.  
  
 Modem je obvykle připojen k jednomu ze sériových portů v počítači. Aby aplikace komunikovala s modemem, musí odesílat příkazy na příslušný sériový port.  
  
### <a name="to-dial-a-modem"></a>Vytáčení modemu  
  
1. Určete, ke kterému sériovému portu je modem připojen. Tento příklad předpokládá, že modem je na COM1.  
  
2. Pomocí `My.Computer.Ports.OpenSerialPort` metody získat odkaz na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Blok `Using` umožňuje aplikaci zavřít sériový port i v případě, že generuje výjimku. Veškerý kód, který manipuluje se sériovým portem, `Try...Catch...Finally` by se měl objevit v tomto bloku nebo v rámci bloku.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Nastavte `DtrEnable` vlastnost označující, že počítač je připraven přijmout příchozí přenos z modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Pomocí metody odešlete příkaz vytáčení a telefonní <xref:System.IO.Ports.SerialPort.Write%2A> číslo modemu prostřednictvím sériového portu.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn v **konektivitě a síti**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Tento příklad vyžaduje odkaz <xref:System?displayProperty=nameWithType> na obor názvů.  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento příklad předpokládá, že modem je připojen k com1. Doporučujeme, aby váš kód umožnit uživateli vybrat požadovaný sériový port ze seznamu dostupných portů. Další informace naleznete v [tématu How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad `Using` používá blok a ujistěte se, že aplikace zavře port, i když vyvolá výjimku. Další informace naleznete [v tématu Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 V tomto příkladu aplikace odpojí sériový port po vytáčení modemu. Realisticky budete chtít přenášet data do modemu a z modemu. Další informace naleznete v [tématu How to: Receive Strings From Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
