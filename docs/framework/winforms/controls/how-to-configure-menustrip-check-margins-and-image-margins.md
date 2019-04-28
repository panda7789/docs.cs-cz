---
title: 'Postupy: Konfigurace okrajů pro zaškrtnutí a okrajů pro obrázek ovládacího prvku MenuStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
ms.openlocfilehash: 09de1a9ca4be1c4ebfb0e13e800c09753bd04f11
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61747004"
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="805a4-102">Postupy: Konfigurace okrajů pro zaškrtnutí a okrajů pro obrázek ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="805a4-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="805a4-103">Můžete přizpůsobit <xref:System.Windows.Forms.MenuStrip> nastavením <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> a <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> vlastnosti v různých kombinacích.</span><span class="sxs-lookup"><span data-stu-id="805a4-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="805a4-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="805a4-104">Example</span></span>  
 <span data-ttu-id="805a4-105">Následující příklad kódu ukazuje, jak nastavit a přizpůsobit <xref:System.Windows.Forms.ContextMenuStrip> zkontrolujte okrajů a okrajů obrázků.</span><span class="sxs-lookup"><span data-stu-id="805a4-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="805a4-106">Postup je stejný pro <xref:System.Windows.Forms.ContextMenuStrip> nebo <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="805a4-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="805a4-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="805a4-107">Compiling the Code</span></span>  
 <span data-ttu-id="805a4-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="805a4-108">This example requires:</span></span>  
  
- <span data-ttu-id="805a4-109">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="805a4-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="805a4-110">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="805a4-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="805a4-111">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="805a4-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="805a4-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="805a4-112">See also</span></span>

- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ContextMenuStrip>
- <xref:System.Windows.Forms.ToolStripDropDown>
- [<span data-ttu-id="805a4-113">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="805a4-113">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
- [<span data-ttu-id="805a4-114">Postupy: Povolení okrajů pro zaškrtnutí a okrajů obrázků v ovládacích prvcích ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="805a4-114">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
