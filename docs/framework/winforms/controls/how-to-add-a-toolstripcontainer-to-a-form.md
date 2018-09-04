---
title: 'Postupy: Přidání ToolStripContainer do formuláře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
ms.openlocfilehash: 0e3a766c8238d7388ee95ecda5c60836ed944e05
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43513182"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a>Postupy: Přidání ToolStripContainer do formuláře
Můžete programově přidat <xref:System.Windows.Forms.ToolStripContainer> do formuláře Windows a přidejte do ní ovládací prvky.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu ukazuje, jak přidat <xref:System.Windows.Forms.ToolStripContainer> a <xref:System.Windows.Forms.ToolStrip> do formulářů Windows, jak přidat položky do <xref:System.Windows.Forms.ToolStrip>a jak přidat <xref:System.Windows.Forms.ToolStrip> k <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad kódu vyžaduje:  
  
-   Odkazy na sestavení System.Drawing System.Text slouží a System.Windows.Forms.  
  
 Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  Viz také [postupy: kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) nebo [úkoly ToolStripContainer – dialogové okno](https://msdn.microsoft.com/library/ms233647\(v=vs.110\)).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [Ovládací prvek ToolStripContainer](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
