---
title: 'Postupy: Vytáčení čísel na modemech připojených k sériovým portům'
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

Toto téma popisuje, jak použít `My.Computer.Ports` k vytočení modemu v Visual Basic.  
  
 Modem je obvykle připojen k jednomu ze sériových portů v počítači. Aby vaše aplikace komunikovala s modemem, musí odeslat příkazy do příslušného sériového portu.  
  
### <a name="to-dial-a-modem"></a>Vytočit modem  
  
1. Určete, ke kterému sériovému portu je modem připojen. Tento příklad předpokládá, že je modem na portu COM1.  
  
2. Použijte `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using` Blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku. Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku nebo `Try...Catch...Finally` v rámci bloku.  
  
     [!code-vb[VbVbalrMyComputer#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#28)]  
  
3. Nastavte `DtrEnable` vlastnost tak, aby označovala, že je počítač připravený přijmout příchozí přenos z modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#29)]  
  
4. Odešlete příkaz k vytočení a telefonní číslo modemu přes sériový port pomocí <xref:System.IO.Ports.SerialPort.Write%2A> metody.  
  
     [!code-vb[VbVbalrMyComputer#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#30)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbVbalrMyComputer#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#27)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Tento příklad vyžaduje odkaz na <xref:System?displayProperty=nameWithType> obor názvů.  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento příklad předpokládá, že modem je připojen k portu COM1. Doporučujeme, aby váš kód mohl uživateli vybrat požadovaný sériový port ze seznamu dostupných portů. Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad používá `Using` blok k ujištění, že aplikace uzavře port, i když vyvolá výjimku. Další informace naleznete v tématu [using – příkaz](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 V tomto příkladu aplikace po připojení modemu odpojí sériový port. Realisticky budete chtít přenést data do a z modemu. Další informace najdete v tématu [Postupy: příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
