---
title: 'Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, retrieving strings
- strings [Visual Basic], retrieving from serial ports
- My.Resources object
ms.assetid: 8371ce2c-e1c7-476b-a86d-9afc2614b6b7
ms.openlocfilehash: 9d71a725aeea684e27479a5d55728151426c4a52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588944"
---
# <a name="how-to-receive-strings-from-serial-ports-in-visual-basic"></a>Postupy: Příjem řetězců ze sériových portů v jazyce Visual Basic
Toto téma popisuje postup použití `My.Computer.Ports` pro příjem řetězců ze sériových portů počítače v jazyce Visual Basic.  
  
### <a name="to-receive-strings-from-the-serial-port"></a>Pro příjem řetězců ze sériových portů  
  
1.  Inicializujte vrácený řetězec.  
  
     [!code-vb[VbVbalrMyComputer#38](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_1.vb)]  
  
2.  Určete, které sériového portu by mělo poskytovat řetězce. Tento příklad předpokládá, že je `COM1`.  
  
3.  Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
     `Try...Catch...Finally` Bloku umožňuje aplikaci zavřete sériového portu i v případě, že vygeneruje výjimka. Všechny kód, který zpracovává sériového portu musí nacházet v tomto bloku.  
  
     [!code-vb[VbVbalrMyComputer#39](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_2.vb)]  
  
4.  Vytvoření `Do` smyčky pro čtení řádků textu, dokud nejsou k dispozici žádné další řádky.  
  
     [!code-vb[VbVbalrMyComputer#40](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_3.vb)]  
  
5.  Použití <xref:System.IO.Ports.SerialPort.ReadLine> metoda přečíst další řádky textu z sériového portu.  
  
     [!code-vb[VbVbalrMyComputer#41](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_4.vb)]  
  
6.  Použijte `If` příkaz k určení, zda <xref:System.IO.Ports.SerialPort.ReadLine> metoda vrátí `Nothing` (což znamená žádný další text je k dispozici). Pokud vrátit `Nothing`, ukončete `Do` smyčky.  
  
     [!code-vb[VbVbalrMyComputer#42](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_5.vb)]  
  
7.  Přidat `Else` zablokujte `If` příkaz k zpracování případu, pokud je řetězec ve skutečnosti pro čtení. Blok připojí řetězec z sériového portu, který má návratový řetězec.  
  
     [!code-vb[VbVbalrMyComputer#43](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_6.vb)]  
  
8.  Vrátí řetězec.  
  
     [!code-vb[VbVbalrMyComputer#44](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_7.vb)]  
  
## <a name="example"></a>Příklad  
 [!code-vb[VbVbalrMyComputer#37](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-receive-strings-from-serial-ports_8.vb)]  
  
 Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **připojení a sítě**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad předpokládá, že počítač používá `COM1`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad předpokládá, že počítač používá `COM1`. Pro větší flexibilitu by měl kód umožnit uživateli vybrat ze seznamu dostupných portů požadovaných sériového portu. Další informace najdete v tématu [postupy: zobrazení k dispozici sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad používá `Try...Catch...Finally` bloku, abyste měli jistotu, že aplikace zavře port a zachytával všechny výjimky časový limit. Další informace najdete v tématu [zkuste... Catch... Finally – příkaz](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
