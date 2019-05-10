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
ms.openlocfilehash: 6b35baac09ac47a25cc55877b2c94628f1b57111
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624064"
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="de6a0-102">Postupy: Přidání ToolStripContainer do formuláře</span><span class="sxs-lookup"><span data-stu-id="de6a0-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="de6a0-103">Můžete programově přidat <xref:System.Windows.Forms.ToolStripContainer> do formuláře Windows a přidejte do ní ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="de6a0-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="de6a0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="de6a0-104">Example</span></span>  
 <span data-ttu-id="de6a0-105">Následující příklad kódu ukazuje, jak přidat <xref:System.Windows.Forms.ToolStripContainer> a <xref:System.Windows.Forms.ToolStrip> do formulářů Windows, jak přidat položky do <xref:System.Windows.Forms.ToolStrip>a jak přidat <xref:System.Windows.Forms.ToolStrip> k <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="de6a0-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="de6a0-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="de6a0-106">Compiling the Code</span></span>  
 <span data-ttu-id="de6a0-107">Tento příklad kódu vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="de6a0-107">This code example requires:</span></span>  
  
- <span data-ttu-id="de6a0-108">Odkazy na sestavení System.Drawing System.Text slouží a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="de6a0-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="de6a0-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="de6a0-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="de6a0-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="de6a0-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="de6a0-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="de6a0-111">See also</span></span>

- <xref:System.Windows.Forms.ToolStripContainer>
- [<span data-ttu-id="de6a0-112">Ovládací prvek ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="de6a0-112">ToolStripContainer Control</span></span>](toolstripcontainer-control.md)
- [<span data-ttu-id="de6a0-113">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="de6a0-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
