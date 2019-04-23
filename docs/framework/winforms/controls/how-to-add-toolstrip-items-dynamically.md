---
title: 'Postupy: Dynamické přidávání položek ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
ms.openlocfilehash: d84b62005554479d227778f513e72594322791a3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59124927"
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="ce6c5-102">Postupy: Dynamické přidávání položek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce6c5-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="ce6c5-103">Můžete dynamicky naplnění kolekce položek nabídky <xref:System.Windows.Forms.ToolStrip> řídit, kdy se otevře v nabídce.</span><span class="sxs-lookup"><span data-stu-id="ce6c5-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ce6c5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ce6c5-104">Example</span></span>  
 <span data-ttu-id="ce6c5-105">Následující příklad kódu ukazuje, jak dynamicky přidat položky, které chcete <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="ce6c5-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="ce6c5-106">Tento příklad také ukazuje, jak znovu použít stejné <xref:System.Windows.Forms.ContextMenuStrip> pro tři různé ovládací prvky ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="ce6c5-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="ce6c5-107">V příkladu <xref:System.Windows.Forms.ToolStripDropDown.Opening> obslužná rutina události naplní kolekci položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="ce6c5-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="ce6c5-108"><xref:System.Windows.Forms.ToolStripDropDown.Opening> Zkontroluje obslužné rutiny události <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> vlastnosti a přidá <xref:System.Windows.Forms.ToolStripItem> popisující správy zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="ce6c5-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ce6c5-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ce6c5-109">Compiling the Code</span></span>  
 <span data-ttu-id="ce6c5-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="ce6c5-110">This example requires:</span></span>  
  
-   <span data-ttu-id="ce6c5-111">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="ce6c5-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="ce6c5-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="ce6c5-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="ce6c5-113">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="ce6c5-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce6c5-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ce6c5-114">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripItem>
- <xref:System.Windows.Forms.ToolStripMenuItem>
- <xref:System.Windows.Forms.ToolStripDropDownButton>
- [<span data-ttu-id="ce6c5-115">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="ce6c5-115">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
