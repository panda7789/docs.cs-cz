---
title: 'Postupy: Příjem řetězců ze sériových portů'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345602"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic

Toto téma popisuje, jak používat `My.Computer.Ports` k přijímání řetězců ze sériových portů počítače v Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Příjem řetězců ze sériového portu  
  
1. Inicializujte návratový řetězec.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Určete, který sériový port by měl poskytnout řetězce. Tento příklad předpokládá, že `COM1`je.  
  
3. Použijte `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` Blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku. Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. Vytvoří `Do` smyčku pro čtení řádků textu, dokud nebudou k dispozici žádné další řádky.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. Použijte <xref:System.IO.Ports.SerialPort.ReadLine> metodu pro čtení dalšího dostupného řádku textu ze sériového portu.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. Použijte `If` příkaz k určení, <xref:System.IO.Ports.SerialPort.ReadLine> zda metoda vrátí `Nothing` (což znamená, že není k dispozici žádný další text). Pokud se vrátí `Nothing`, ukončete `Do` smyčku.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. Přidejte `Else` blok do `If` příkazu pro zpracování případu, pokud je řetězec skutečně čten. Blok připojí řetězec ze sériového portu do návratového řetězce.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Vrátí řetězec.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 V tomto příkladu se předpokládá, že `COM1`počítač používá.  
  
## <a name="robust-programming"></a>Robustní programování  

 V tomto příkladu se předpokládá, že `COM1`počítač používá. Pro větší flexibilitu by měl kód uživateli dovolit vybrat požadovaný sériový port ze seznamu dostupných portů. Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 V `Try...Catch...Finally` tomto příkladu se používá blok k ujištění, že aplikace zavírá port a zachytává všechny výjimky časového limitu. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
