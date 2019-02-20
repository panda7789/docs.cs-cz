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
ms.openlocfilehash: 47279c5e8fa24accca36280f9a97200982a1451a
ms.sourcegitcommit: acd8ed14fe94e9d4e3a7fb685fe83d05e941073c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2019
ms.locfileid: "56441798"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="193d3-102">Postupy: Přidání ToolStripContainer do formuláře</span><span class="sxs-lookup"><span data-stu-id="193d3-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="193d3-103">Můžete programově přidat <xref:System.Windows.Forms.ToolStripContainer> do formuláře Windows a přidejte do ní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="193d3-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="193d3-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="193d3-104">Example</span></span>  
 <span data-ttu-id="193d3-105">Následující příklad kódu ukazuje, jak přidat <xref:System.Windows.Forms.ToolStripContainer> a <xref:System.Windows.Forms.ToolStrip> do formulářů Windows, jak přidat položky do <xref:System.Windows.Forms.ToolStrip>a jak přidat <xref:System.Windows.Forms.ToolStrip> k <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="193d3-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="193d3-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="193d3-106">Compiling the Code</span></span>  
 <span data-ttu-id="193d3-107">Tento příklad kódu vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="193d3-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="193d3-108">Odkazy na sestavení System.Drawing System.Text slouží a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="193d3-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="193d3-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="193d3-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="193d3-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="193d3-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="193d3-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="193d3-111">See also</span></span>
- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="193d3-112">Ovládací prvek ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="193d3-112">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)
- [<span data-ttu-id="193d3-113">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="193d3-113">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
