---
title: "Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95c67b344572d21f418cbc14d350e6ff28611bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a>Postupy: Odesílání řetězců na sériové porty v jazyce Visual Basic
Toto téma popisuje postup použití `My.Computer.Ports` k odesílání řetězců na sériové porty počítače v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
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
 [Postupy: vytáčení modemů připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Postupy: zobrazení dostupných sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)
