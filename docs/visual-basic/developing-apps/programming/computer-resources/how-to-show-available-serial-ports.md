---
title: 'Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: 58f4d629500223ccc6690912b5e261eebc17c6b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603804"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic
Toto téma popisuje způsob použití `My.Computer.Ports` k zobrazení dostupných sériových portů v počítači v jazyce Visual Basic.  
  
 Umožňuje uživateli vybrat port, který chcete použít názvy sériových portů jsou umístěny v <xref:System.Windows.Forms.ListBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu cyklickému všechny řetězce, který `My.Computer.Ports.SerialPortNames` vrátí vlastnost. Tyto řetězce jsou názvy dostupných sériových portů v počítači.  
  
 Obvykle uživatel vybere ze seznamu dostupných portů který sériový port aplikace musí používat. V tomto příkladu jsou názvy sériových portů. uložené v <xref:System.Windows.Forms.ListBox> ovládacího prvku. Další informace najdete v tématu [ListBox – ovládací prvek](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 Tento příklad kódu je také dostupný jako fragment kódu technologie IntelliSense. V dialogu pro výběr fragmentu kódu je umístěn v **připojení a sítě**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Odkaz na System.Windows.Forms.dll.  
  
-   Přístup k členům <xref:System.Windows.Forms> oboru názvů. Přidat `Imports` příkazu, pokud jste nejsou kvalifikaci plně názvy členů ve vašem kódu. Další informace najdete v tématu [příkaz Imports (Namespace .NET a typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
-   Obsahující formulář <xref:System.Windows.Forms.ListBox> ovládací prvek s názvem `ListBox1`.  
  
## <a name="robust-programming"></a>Robustní programování  
 Není nutné používat <xref:System.Windows.Forms.ListBox> ovládací prvek pro zobrazení názvy dostupných sériových portů. Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiný ovládací prvek. Pokud aplikace nepotřebuje odpověď od uživatele, můžete použít <xref:System.Windows.Forms.TextBox> ovládací prvek pro zobrazení informací.  
  
> [!NOTE]
>  Názvy port vrácené `My.Computer.Ports.SerialPortNames` může být nesprávné při spuštění na Windows 98. Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, například `Try...Catch...Finally` příkazu nebo `Using` prohlášení, při použití názvu port otevřít porty.  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Odesílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
