---
title: 'Postupy: Zobrazení dostupných sériových portů'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345578"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic

Toto téma popisuje, `My.Computer.Ports` jak zobrazit dostupné sériové porty počítače v jazyce Visual Basic.  
  
 Chcete-li uživateli povolit výběr portu, který má použít, jsou názvy sériových portů umístěny do ovládacího <xref:System.Windows.Forms.ListBox> prvku.  
  
## <a name="example"></a>Příklad  

 Tento příklad smyčky přes všechny řetězce, které vrátí `My.Computer.Ports.SerialPortNames` vlastnost. Tyto řetězce jsou názvy dostupných sériových portů v počítači.  
  
 Uživatel obvykle vybere sériový port, který má aplikace použít, ze seznamu dostupných portů. V tomto příkladu jsou názvy <xref:System.Windows.Forms.ListBox> sériových portů uloženy v ovládacím prvku. Další informace naleznete v tématu [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu IntelliSense. Ve výběru fragmentu kódu je umístěn v **konektivitě a síti**. Další informace naleznete v [tématu Fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Tento příklad vyžaduje:  
  
- Odkaz na soubor System.Windows.Forms.dll.  
  
- Přístup k členům <xref:System.Windows.Forms> oboru názvů. Přidejte `Imports` příkaz, pokud nejste plně kvalifikační jména členů ve vašem kódu. Další informace naleznete [v tématu Imports Statement (Obor názvů.NET a Typ).](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)  
  
- Že formulář má <xref:System.Windows.Forms.ListBox> ovládací `ListBox1`prvek s názvem .  
  
## <a name="robust-programming"></a>Robustní programování  

 Není třeba použít <xref:System.Windows.Forms.ListBox> ovládací prvek k zobrazení dostupných názvů sériových portů. Místo toho můžete <xref:System.Windows.Forms.ComboBox> použít nebo jiný ovládací prvek. Pokud aplikace nepotřebuje odpověď od uživatele, můžete použít <xref:System.Windows.Forms.TextBox> ovládací prvek k zobrazení informací.  
  
> [!NOTE]
> Názvy portů `My.Computer.Ports.SerialPortNames` vrácené může být nesprávné při spuštění v systému Windows 98. Chcete-li zabránit chybám aplikace, použijte `Try...Catch...Finally` zpracování `Using` výjimek, jako je například příkaz nebo příkaz, při použití názvů portů k otevření portů.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
