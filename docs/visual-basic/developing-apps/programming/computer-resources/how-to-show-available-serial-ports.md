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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345578"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic

Toto téma popisuje, jak použít `My.Computer.Ports` k zobrazení dostupných sériových portů počítače v Visual Basic.  
  
 Pokud chcete uživateli dovolit vybrat, který port se má použít, názvy sériových portů se umístí do ovládacího prvku <xref:System.Windows.Forms.ListBox>.  
  
## <a name="example"></a>Příklad  

 Tento příklad projde všemi řetězci, které vrací vlastnost `My.Computer.Ports.SerialPortNames`. Tyto řetězce jsou názvy dostupných sériových portů v počítači.  
  
 Obvykle uživatel vybere, který sériový port by měla aplikace používat ze seznamu dostupných portů. V tomto příkladu jsou názvy sériových portů uloženy v ovládacím prvku <xref:System.Windows.Forms.ListBox>. Další informace naleznete v tématu [ovládací prvek ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Tento příklad vyžaduje:  
  
- Odkaz na projekt System. Windows. Forms. dll.  
  
- Přístup k členům oboru názvů <xref:System.Windows.Forms>. Pokud plně nekvalifikujete názvy členů v kódu, přidejte `Imports` příkaz. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- Má-li formulář <xref:System.Windows.Forms.ListBox> ovládací prvek s názvem `ListBox1`.  
  
## <a name="robust-programming"></a>Robustní programování  

 K zobrazení dostupných názvů sériového portu není nutné používat ovládací prvek <xref:System.Windows.Forms.ListBox>. Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiný ovládací prvek. Pokud aplikace nepotřebuje odpověď od uživatele, můžete k zobrazení informací použít ovládací prvek <xref:System.Windows.Forms.TextBox>.  
  
> [!NOTE]
> Názvy portů vrácené `My.Computer.Ports.SerialPortNames` můžou být při spuštění ve Windows 98 nesprávné. Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, jako je například příkaz `Try...Catch...Finally` nebo příkaz `Using` při použití názvů portů k otevření portů.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
