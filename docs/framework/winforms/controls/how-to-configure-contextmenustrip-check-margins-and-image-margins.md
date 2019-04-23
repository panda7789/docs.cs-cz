---
title: 'Postupy: Konfigurace okrajů pro zaškrtnutí a okrajů pro obrázek ovládacího prvku ContextMenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [Windows Forms], configuring check and image margins
- ContextMenuStrips [Windows Forms], configuring check and image margins
- margins [Windows Forms], setting check and image in Windows Forms ContextMenuStrips
ms.assetid: 3391c4c2-0c9e-4aa4-9492-13ff7644bdf2
ms.openlocfilehash: 0e78ed960904baaead8e8d23b51c97cf2edfd4ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189628"
---
# <a name="how-to-configure-contextmenustrip-check-margins-and-image-margins"></a><span data-ttu-id="3f927-102">Postupy: Konfigurace okrajů pro zaškrtnutí a okrajů pro obrázek ovládacího prvku ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="3f927-102">How to: Configure ContextMenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="3f927-103">Můžete přizpůsobit <xref:System.Windows.Forms.ContextMenuStrip> nastavením <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> a <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> vlastnosti v různých kombinacích.</span><span class="sxs-lookup"><span data-stu-id="3f927-103">You can customize a <xref:System.Windows.Forms.ContextMenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3f927-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3f927-104">Example</span></span>  
 <span data-ttu-id="3f927-105">Následující příklad kódu ukazuje, jak nastavit a přizpůsobit <xref:System.Windows.Forms.ContextMenuStrip> zkontrolujte a okrajů obrázků.</span><span class="sxs-lookup"><span data-stu-id="3f927-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check and image margins.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3f927-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3f927-106">Compiling the Code</span></span>  
 <span data-ttu-id="3f927-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="3f927-107">This example requires:</span></span>  
  
-   <span data-ttu-id="3f927-108">Odkazy na sestavení System.Design System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="3f927-108">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="3f927-109">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3f927-109">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="3f927-110">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="3f927-110">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f927-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3f927-111">See also</span></span>

- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="3f927-112">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="3f927-112">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="3f927-113">Postupy: Povolení okrajů pro zaškrtnutí a okrajů obrázků v ovládacích prvcích ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="3f927-113">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
