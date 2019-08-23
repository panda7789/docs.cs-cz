---
title: 'Postupy: Zobrazit dostupné sériové porty v Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: e8e0f6d63f7135c3bbe24ee6426cd714f2eb275f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956913"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a>Postupy: Zobrazit dostupné sériové porty v Visual Basic
V tomto tématu se dozvíte `My.Computer.Ports` , jak pomocí nástroje Zobrazit dostupné sériové porty počítače v Visual Basic.  
  
 Pokud chcete uživateli dovolit vybrat, který port se má použít, názvy sériových portů se umístí do <xref:System.Windows.Forms.ListBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Tento příklad projde všemi řetězci, které `My.Computer.Ports.SerialPortNames` vrátí vlastnost. Tyto řetězce jsou názvy dostupných sériových portů v počítači.  
  
 Obvykle uživatel vybere, který sériový port by měla aplikace používat ze seznamu dostupných portů. V tomto příkladu jsou názvy sériových portů uloženy v <xref:System.Windows.Forms.ListBox> ovládacím prvku. Další informace naleznete v tématu [ovládací prvek ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 Tento příklad kódu je také k dispozici jako fragment kódu technologie IntelliSense. Ve výběru fragmentu kódu se nachází v **Možnosti připojení a sítě**. Další informace najdete v tématu [fragmenty kódu](/visualstudio/ide/code-snippets).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkaz na projekt System. Windows. Forms. dll.  
  
- Přístup ke členům <xref:System.Windows.Forms> oboru názvů. `Imports` Přidejte příkaz, pokud ve svém kódu plně nekvalifikujete názvy členů. Další informace naleznete v tématu [příkaz Imports (obor názvů a typ rozhraní .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  
  
- , Aby formulář měl <xref:System.Windows.Forms.ListBox> ovládací prvek s názvem. `ListBox1`  
  
## <a name="robust-programming"></a>Robustní programování  
 Nemusíte používat <xref:System.Windows.Forms.ListBox> ovládací prvek k zobrazení dostupných názvů sériového portu. Místo toho můžete použít <xref:System.Windows.Forms.ComboBox> nebo jiný ovládací prvek. Pokud aplikace nepotřebuje od uživatele odpověď, můžete k zobrazení informací použít <xref:System.Windows.Forms.TextBox> ovládací prvek.  
  
> [!NOTE]
> Názvy portů vrácené nástrojem `My.Computer.Ports.SerialPortNames` můžou být při spuštění ve Windows 98 nesprávné. Chcete-li zabránit chybám aplikace, použijte zpracování výjimek, `Try...Catch...Finally` jako je například `Using` příkaz nebo příkaz, při použití názvů portů k otevření portů.  
  
## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [Postupy: Vytočit modemy připojené k sériovým portům](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [Postupy: Odesílání řetězců na sériové porty](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [Postupy: Přijímání řetězců ze sériových portů](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
