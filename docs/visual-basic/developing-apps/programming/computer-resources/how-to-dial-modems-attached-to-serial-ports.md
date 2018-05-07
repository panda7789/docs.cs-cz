---
title: 'Postupy: Vytáčení modemů připojených k sériovým portům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: 6bef611b96c8c86a6eaf2802840e96769cd6fa34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Postupy: Vytáčení modemů připojených k sériovým portům v jazyce Visual Basic
Toto téma popisuje postup použití `My.Computer.Ports` k vytáčení modemu v jazyce Visual Basic.  
  
 Obvykle je modemu připojené k jednomu ze sériových portů v počítači. Pro aplikace komunikovat s modem se musí odesílat příkazy k příslušnému sériového portu.  
  
### <a name="to-dial-a-modem"></a>K vytáčení modemu  
  
1.  Určí, které sériového portu, který je připojen k. Tento příklad předpokládá, že je zapnutý COM1 modem.  
  
2.  Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using` Bloku umožňuje aplikaci zavřete sériového portu i v případě, že vygeneruje výjimka. Všechny kód, který zpracovává sériového portu by se měla objevit v rámci tohoto bloku nebo uvnitř `Try...Catch...Finally` bloku.  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  Nastavte `DtrEnable` vlastnost k označení, že je počítač připraven k přijetí příchozího přenosu z modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  Příkaz dial a telefonní číslo poslat modemu prostřednictvím sériového portu prostřednictvím <xref:System.IO.Ports.SerialPort.Write%2A> metoda.  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **připojení a sítě**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje odkaz na <xref:System?displayProperty=nameWithType> oboru názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad předpokládá, že je připojen k COM1. Doporučujeme vám, že váš kód umožňují uživateli vybrat ze seznamu dostupných portů požadovaných sériového portu. Další informace najdete v tématu [postupy: zobrazení k dispozici sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad používá `Using` bloku a ujistěte se, že aplikace zavře port i v případě, že vyhodí výjimku. Další informace najdete v tématu [pomocí příkazu](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 V tomto příkladu aplikace odpojí sériového portu po vytočení modemu. Reálně můžete k přenosu dat do a z modemu. Další informace najdete v tématu [postupy: příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)  
 [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
