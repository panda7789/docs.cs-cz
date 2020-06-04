---
title: 'Postupy: Zobrazení dostupných sériových portů'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: e7a9166f1879ed0850ca893bed307a0318298bbb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84401820"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Postupy: Zobrazení dostupných sériových portů v jazyce Visual Basic

V tomto tématu se dozvíte, jak pomocí nástroje `My.Computer.Ports` Zobrazit dostupné sériové porty počítače v Visual Basic.  
  
 Pokud chcete uživateli dovolit vybrat, který port se má použít, názvy sériových portů se umístí do <xref:System.Windows.Forms.ListBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  

 Tento příklad projde všemi řetězci, které `My.Computer.Ports.SerialPortNames` vrátí vlastnost. Tyto řetězce jsou názvy dostupných sériových portů v počítači.  
  
 Obvykle uživatel vybere, který sériový port by měla aplikace používat ze seznamu dostupných portů. V tomto příkladu jsou názvy sériových portů uloženy v <xref:System.Windows.Forms.ListBox> ovládacím prvku. Další informace naleznete v tématu [ovládací prvek ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**. Další informace naleznete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  

 Tento příklad vyžaduje:  
  
- Odkaz na projekt System. Windows. Forms. dll.  
  
- Přístup ke členům <xref:System.Windows.Forms> oboru názvů. Přidejte `Imports` příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- , Aby formulář měl <xref:System.Windows.Forms.ListBox> ovládací prvek s názvem `ListBox1` .  
  
## <a name="robust-programming"></a>Robustní programování  

 Nemusíte používat <xref:System.Windows.Forms.ListBox> ovládací prvek k zobrazení dostupných názvů sériového portu. Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiný ovládací prvek. Pokud aplikace nepotřebuje od uživatele odpověď, můžete <xref:System.Windows.Forms.TextBox> k zobrazení informací použít ovládací prvek.  
  
> [!NOTE]
> Názvy portů vrácené nástrojem `My.Computer.Ports.SerialPortNames` můžou být při spuštění ve Windows 98 nesprávné. Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, jako je například `Try...Catch...Finally` příkaz nebo `Using` příkaz, při použití názvů portů k otevření portů.  
  
## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Postupy: Vytáčení čísel na modemech připojených k sériovým portům](how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Posílání řetězců na sériové porty](how-to-send-strings-to-serial-ports.md)
- [Postupy: Příjem řetězců ze sériových portů](how-to-receive-strings-from-serial-ports.md)
