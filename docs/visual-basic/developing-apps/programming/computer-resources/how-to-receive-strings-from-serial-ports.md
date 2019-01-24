---
title: 'Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: f87ff7e621d241a94dae444bc156502ee86b36b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521605"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic
Toto téma popisuje způsob použití `My.Computer.Ports` pro příjem řetězců ze sériových portů počítače v jazyce Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Pro příjem řetězců ze sériových portů  
  
1.  Inicializujte vráceného řetězce.  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  Určení, které sériového portu by měla poskytnout řetězce. Tento příklad předpokládá, že je `COM1`.  
  
3.  Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` Bloku umožňuje, aby aplikace zavřete sériového portu, i v případě, že vygeneruje výjimku. Veškerý kód, který provádí úpravy sériového portu by se zobrazit v rámci tohoto bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  Vytvoření `Do` smyčky pro čtení řádků textu, dokud nejsou k dispozici žádné další řádky.  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  Použití <xref:System.IO.Ports.SerialPort.ReadLine> metodu za účelem čtení další dostupný řádek textu ze sériového portu.  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  Použití `If` příkaz k určení, zda <xref:System.IO.Ports.SerialPort.ReadLine> vrátí metoda `Nothing` (což znamená, že žádné další text je k dispozici). Pokud se nevrátí `Nothing`, ukončete `Do` smyčky.  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  Přidat `Else` bloku `If` příkaz pro zpracování případu, pokud je ve skutečnosti čtení řetězce. Blok připojí řetězec ze sériového portu, který má vráceného řetězce.  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  Vrátí řetězec.  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad předpokládá, že počítač používá `COM1`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad předpokládá, že počítač používá `COM1`. Pro větší flexibilitu by měl kód umožnit uživateli vybrat požadovanou sériového portu ze seznamu dostupných portů. Další informace najdete v tématu [jak: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad používá `Try...Catch...Finally` blok k Ujistěte se, že aplikace zavře port a zachytit žádné výjimky časového limitu. Další informace najdete v tématu [zkuste... Catch... Příkaz finally](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Odesílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
