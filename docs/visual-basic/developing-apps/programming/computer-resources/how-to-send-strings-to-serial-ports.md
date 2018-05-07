---
title: 'Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
ms.openlocfilehash: a00306407cfe880ebc915d74a753109cc9696f6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic
Toto téma popisuje postup použití `My.Computer.Ports` k odesílání řetězců na sériové porty počítače v jazyce Visual Basic.  
  
## <a name="example"></a>Příklad  
 Tento příklad odešle řetězec COM1 sériového portu. Musíte použít jiný sériového portu v počítači.  
  
 Použití `My.Computer.Ports.OpenSerialPort` metodu k získání odkazu na port. Další informace naleznete v tématu <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.  
  
 `Using` Bloku umožňuje aplikaci zavřete sériového portu i v případě, že vygeneruje výjimka. Všechny kód, který zpracovává sériového portu by se měla objevit v rámci tohoto bloku nebo uvnitř `Try...Catch...Finally` bloku.  
  
 <xref:System.IO.Ports.SerialPort.WriteLine%2A> Metoda odešle data do sériového portu.  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
  
-   Tento příklad předpokládá, že počítač používá `COM1`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento příklad předpokládá, že počítač používá `COM1`; pro větší flexibilitu, tento kód by měl umožní uživateli vybrat ze seznamu dostupných portů požadovaných sériového portu. Další informace najdete v tématu [postupy: zobrazení k dispozici sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).  
  
 Tento příklad používá `Using` bloku a ujistěte se, že aplikace zavře port i v případě, že vyhodí výjimku. Další informace najdete v tématu [pomocí příkazu](../../../../visual-basic/language-reference/statements/using-statement.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Postupy: Zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
