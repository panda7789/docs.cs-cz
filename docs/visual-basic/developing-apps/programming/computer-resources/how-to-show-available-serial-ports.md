---
title: "Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1dc12d8ad4c27eff346ccb6a7f5fd2ae3bd76701
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic
Toto téma popisuje postup použití `My.Computer.Ports` k zobrazení dostupných sériových portů počítače v [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
 Povolit uživatelům vyberte port, který chcete použít, jsou umístěny názvy sériových portů v <xref:System.Windows.Forms.ListBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Tento příklad cyklicky prochází přes všechny řetězce, `My.Computer.Ports.SerialPortNames` vrátí vlastnost. Tyto řetězce jsou názvy dostupných sériových portů v počítači.  
  
 Obvykle se uživatel vybere ze seznamu dostupných portů sériový port, který by aplikace měla použít. V tomto příkladu jsou uložené názvy sériových portů v <xref:System.Windows.Forms.ListBox> ovládacího prvku. Další informace najdete v tématu [ListBox – ovládací prvek](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 Tento příklad kódu je také k dispozici jako IntelliSense fragment kódu. V Sběrač fragmentů kódu je umístěn v **připojení a sítě**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Projekt odkazuje na System.Windows.Forms.dll.  
  
-   Přístup k členům <xref:System.Windows.Forms> oboru názvů. Přidat `Imports` příkaz, pokud jste nejsou kvalifikující plně názvy členů v kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
-   S svého formuláře <xref:System.Windows.Forms.ListBox> ovládací prvek s názvem `ListBox1`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Není nutné použít <xref:System.Windows.Forms.ListBox> řízení, pokud chcete zobrazit názvy dostupné sériového portu. Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiného ovládacího prvku. Pokud aplikace není nutné odpověď od uživatele, můžete použít <xref:System.Windows.Forms.TextBox> ovládací prvek pro zobrazení informací.  
  
> [!NOTE]
>  Názvy port vrácené `My.Computer.Ports.SerialPortNames` může být nesprávný při spuštění v systému Windows 98. Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, například `Try...Catch...Finally` příkaz nebo `Using` při otevření portů pomocí názvu port.  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [Postupy: vytáčení modemů připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [Postupy: odesílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [Postupy: příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
