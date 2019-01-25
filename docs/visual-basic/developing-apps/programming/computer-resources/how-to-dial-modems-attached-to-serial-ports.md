---
title: 'Postupy: Vytáčení čísel na modemech připojených k sériovým portům v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- modems [Visual Basic], dialing
- serial ports [Visual Basic], dialing
- My.Computer.Ports object
ms.assetid: 3834db40-f431-45f1-b671-dc91787164b6
ms.openlocfilehash: db99f94d27235a7c9dca4fc5339854a39147b585
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54490610"
---
# <a name="how-to-dial-modems-attached-to-serial-ports-in-visual-basic"></a>Postupy: Vytáčení čísel na modemech připojených k sériovým portům v jazyce Visual Basic
Toto téma popisuje způsob použití `My.Computer.Ports` vytáčení modemů v jazyce Visual Basic.  
  
 Obvykle modemu je připojený k jednomu ze sériových portů v počítači. Pro vaši aplikaci ke komunikaci s modemem se musí odesílat příkazy na odpovídající sériového portu.  
  
### <a name="to-dial-a-modem"></a>Chcete-li vytočte modemu  
  
1.  Určete, které sériového portu, který je připojen k. Tento příklad předpokládá, že je zapnutý COM1 modem.  
  
2.  Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Using` Bloku umožňuje, aby aplikace zavřete sériového portu, i v případě, že vygeneruje výjimku. Veškerý kód, který provádí úpravy sériového portu by se měla objevit v rámci tohoto bloku nebo v rámci `Try...Catch...Finally` bloku.  
  
     [!code-vb[VbVbalrMyComputer#28](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_1.vb)]  
  
3.  Nastavte `DtrEnable` vlastnost umožňující označit, že je počítač připravený k přijetí příchozího přenosu od modemu.  
  
     [!code-vb[VbVbalrMyComputer#29](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_2.vb)]  
  
4.  Odeslat volání příkazu a telefonní číslo přes sériový port prostřednictvím modemu <xref:System.IO.Ports.SerialPort.Write%2A> metody.  
  
     [!code-vb[VbVbalrMyComputer#30](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_3.vb)]  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrMyComputer#27](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-dial-modems-attached-to-serial-ports_4.vb)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje odkaz na <xref:System?displayProperty=nameWithType> oboru názvů.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad předpokládá, že je připojen k COM1. Doporučujeme vám, že váš kód umožnit uživateli vybrat požadovanou sériového portu ze seznamu dostupných portů. Další informace najdete v tématu [jak: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad používá `Using` blok k Ujistěte se, že aplikace zavře portu i v případě, že dojde k výjimce. Další informace najdete v tématu [příkazu Using](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
 V tomto příkladu aplikace odpojí sériového portu po vytočí modemu. Reálně můžete k přenosu dat do a z modemu. Další informace najdete v tématu [jak: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Odesílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
