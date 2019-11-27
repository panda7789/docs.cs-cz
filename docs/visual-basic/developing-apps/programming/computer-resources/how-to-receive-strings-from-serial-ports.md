---
title: 'Postupy: Příjem řetězců ze sériových portů'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: afd19877d053cb414f08761cda4e461d88f9e21c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345602"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic

Toto téma popisuje, jak použít `My.Computer.Ports` k přijímání řetězců ze sériových portů počítače v Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Příjem řetězců ze sériového portu  
  
1. Inicializujte návratový řetězec.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Určete, který sériový port by měl poskytnout řetězce. V tomto příkladu se předpokládá, že je `COM1`.  
  
3. K získání odkazu na port použijte metodu `My.Computer.Ports.OpenSerialPort`. Další informace najdete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` blok umožňuje aplikaci zavřít sériový port, i když generuje výjimku. Veškerý kód, který zpracovává sériový port, by měl být uveden v rámci tohoto bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. Vytvořte smyčku `Do` pro čtení řádků textu, dokud nejsou k dispozici žádné další řádky.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. Pomocí metody <xref:System.IO.Ports.SerialPort.ReadLine> si můžete přečíst další dostupný řádek textu ze sériového portu.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. Pomocí příkazu `If` určete, zda <xref:System.IO.Ports.SerialPort.ReadLine> metoda vrátí `Nothing` (což znamená, že není k dispozici žádný další text). Pokud vrátí `Nothing`, ukončete smyčku `Do`.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. Přidejte do příkazu `If` blok `Else` pro zpracování případu, pokud je řetězec skutečně čten. Blok připojí řetězec ze sériového portu do návratového řetězce.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Vrátí řetězec.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Tento příklad předpokládá, že počítač používá `COM1`.  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento příklad předpokládá, že počítač používá `COM1`. Pro větší flexibilitu by měl kód uživateli dovolit vybrat požadovaný sériový port ze seznamu dostupných portů. Další informace najdete v tématu [Postup: zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 V tomto příkladu se používá blok `Try...Catch...Finally` k ujištění, že aplikace zavírá port a zachytává všechny výjimky časového limitu. Další informace najdete v tématu [Try... Zachytit... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
