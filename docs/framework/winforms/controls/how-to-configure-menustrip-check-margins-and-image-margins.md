---
title: 'Postupy: Konfigurace okrajů pro zaškrtnutí a okrajů pro obrázek ovládacího prvku MenuStrip'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- margins [Windows Forms], setting in MenuStrip controls
- menus [Windows Forms], setting margins
- MenuStrip control [Windows Forms], configuring check and image margins
ms.assetid: 45a9075d-4bea-4ce2-9b2c-7619aa39f8ce
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f138d3a145e5cbbcff23d531970b5d5d71864dc2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-configure-menustrip-check-margins-and-image-margins"></a><span data-ttu-id="43b48-102">Postupy: Konfigurace okrajů pro zaškrtnutí a okrajů pro obrázek ovládacího prvku MenuStrip</span><span class="sxs-lookup"><span data-stu-id="43b48-102">How to: Configure MenuStrip Check Margins and Image Margins</span></span>
<span data-ttu-id="43b48-103">Můžete přizpůsobit <xref:System.Windows.Forms.MenuStrip> nastavením <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> a <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> vlastnosti v různých kombinacích.</span><span class="sxs-lookup"><span data-stu-id="43b48-103">You can customize a <xref:System.Windows.Forms.MenuStrip> by setting the <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowImageMargin%2A> and <xref:System.Windows.Forms.ToolStripDropDownMenu.ShowCheckMargin%2A> properties in various combinations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43b48-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="43b48-104">Example</span></span>  
 <span data-ttu-id="43b48-105">Následující příklad kódu ukazuje, jak nastavit a přizpůsobit <xref:System.Windows.Forms.ContextMenuStrip> Zkontrolujte okraje a okrajů obrázků.</span><span class="sxs-lookup"><span data-stu-id="43b48-105">The following code example demonstrates how to set and customize the <xref:System.Windows.Forms.ContextMenuStrip> check margins and image margins.</span></span> <span data-ttu-id="43b48-106">Postup je stejný pro <xref:System.Windows.Forms.ContextMenuStrip> nebo <xref:System.Windows.Forms.MenuStrip>.</span><span class="sxs-lookup"><span data-stu-id="43b48-106">The procedure is the same for a <xref:System.Windows.Forms.ContextMenuStrip> or a <xref:System.Windows.Forms.MenuStrip>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#60)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="43b48-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="43b48-107">Compiling the Code</span></span>  
 <span data-ttu-id="43b48-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="43b48-108">This example requires:</span></span>  
  
-   <span data-ttu-id="43b48-109">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="43b48-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="43b48-110">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="43b48-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="43b48-111">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="43b48-111">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="43b48-112">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="43b48-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43b48-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="43b48-113">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.ToolStripDropDown>  
 [<span data-ttu-id="43b48-114">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="43b48-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [<span data-ttu-id="43b48-115">Postupy: Povolení okrajů pro zaškrtnutí a okrajů obrázků v ovládacích prvcích ContextMenuStrip</span><span class="sxs-lookup"><span data-stu-id="43b48-115">How to: Enable Check Margins and Image Margins in ContextMenuStrip Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-check-margins-and-image-margins-in-contextmenustrip-controls.md)
