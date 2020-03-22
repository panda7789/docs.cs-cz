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

Toto téma popisuje `My.Computer.Ports` použití pro příjem řetězců ze sériových portů počítače v jazyce Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Příjem řetězců ze sériového portu  
  
1. Inicializovat návratový řetězec.  
  
     [!code-vb[VbVbalrMyComputer#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#38)]  
  
2. Určete, který sériový port by měl poskytovat řetězce. Tento příklad předpokládá, `COM1`že je .  
  
3. Pomocí `My.Computer.Ports.OpenSerialPort` metody získat odkaz na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     Blok `Try...Catch...Finally` umožňuje aplikaci zavřít sériový port i v případě, že generuje výjimku. Veškerý kód, který manipuluje se sériovým portem, by se měl objevit v tomto bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#39)]  
  
4. Vytvořte `Do` smyčku pro čtení řádků textu, dokud nebudou k dispozici žádné další řádky.  
  
     [!code-vb[VbVbalrMyComputer#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#40)]  
  
5. Pomocí <xref:System.IO.Ports.SerialPort.ReadLine> této metody můžete číst další dostupný řádek textu ze sériového portu.  
  
     [!code-vb[VbVbalrMyComputer#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#41)]  
  
6. Pomocí `If` příkazu určete, zda <xref:System.IO.Ports.SerialPort.ReadLine> metoda vrátí `Nothing` (což znamená, že není k dispozici žádný další text). Pokud se `Nothing`vrátí , `Do` ukončete smyčku.  
  
     [!code-vb[VbVbalrMyComputer#42](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#42)]  
  
7. Přidejte `Else` blok `If` do příkazu pro zpracování případu, pokud je řetězec skutečně přečten. Blok připojí řetězec ze sériového portu k vratný řetězec.  
  
     [!code-vb[VbVbalrMyComputer#43](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#43)]  
  
8. Vraťte řetězec.  
  
     [!code-vb[VbVbalrMyComputer#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#44)]  
  
## <a name="example"></a>Příklad  

 [!code-vb[VbVbalrMyComputer#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#37)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn v **konektivitě a síti**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Tento příklad předpokládá, že `COM1`počítač používá .  
  
## <a name="robust-programming"></a>Robustní programování  

 Tento příklad předpokládá, že `COM1`počítač používá . Pro větší flexibilitu by měl kód umožnit uživateli vybrat požadovaný sériový port ze seznamu dostupných portů. Další informace naleznete v [tématu How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad `Try...Catch...Finally` používá blok ujistěte se, že aplikace zavře port a zachytit všechny výjimky časového výpadku. Další informace naleznete v [tématu Try... Chytit... Finally prohlášení](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
