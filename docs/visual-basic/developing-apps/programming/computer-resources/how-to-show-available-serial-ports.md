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

V tomto tématu se dozvíte `My.Computer.Ports` , jak pomocí nástroje Zobrazit dostupné sériové porty počítače v Visual Basic.  
  
 Pokud chcete uživateli dovolit vybrat, který port se má použít, názvy sériových portů se umístí do <xref:System.Windows.Forms.ListBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  

 Tento příklad projde všemi řetězci, které vrátí `My.Computer.Ports.SerialPortNames` vlastnost. Tyto řetězce jsou názvy dostupných sériových portů v počítači.  
  
 Obvykle uživatel vybere, který sériový port by měla aplikace používat ze seznamu dostupných portů. V tomto příkladu jsou názvy sériových portů uloženy v <xref:System.Windows.Forms.ListBox> ovládacím prvku. Další informace naleznete v tématu [ovládací prvek ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Tento příklad vyžaduje:  
  
- Odkaz na projekt System. Windows. Forms. dll.  
  
- Přístup ke členům <xref:System.Windows.Forms> oboru názvů. Přidejte `Imports` příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- , Aby formulář měl <xref:System.Windows.Forms.ListBox> ovládací prvek s `ListBox1`názvem.  
  
## <a name="robust-programming"></a>Robustní programování  

 Nemusíte používat <xref:System.Windows.Forms.ListBox> ovládací prvek k zobrazení dostupných názvů sériového portu. Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiný ovládací prvek. Pokud aplikace nepotřebuje od uživatele odpověď, můžete k zobrazení informací použít <xref:System.Windows.Forms.TextBox> ovládací prvek.  
  
> [!NOTE]
> Názvy portů vrácené nástrojem `My.Computer.Ports.SerialPortNames` můžou být při spuštění ve Windows 98 nesprávné. Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, `Try...Catch...Finally` jako je například `Using` příkaz nebo příkaz, při použití názvů portů k otevření portů.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Posílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
