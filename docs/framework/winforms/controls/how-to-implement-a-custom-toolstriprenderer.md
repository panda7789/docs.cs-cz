---
title: "Postupy: Implementace vlastního prvku ToolStripRenderer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: c66fd3f7-2377-4553-8f1b-006527f08f32
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ecd8953d6fe2e4a22e6c3b5fcc294855ef3a1c8a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="15574-102">Postupy: Implementace vlastního prvku ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="15574-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="15574-103">Můžete přizpůsobit vzhled <xref:System.Windows.Forms.ToolStrip> řízení implementací třídu odvozenou z <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="15574-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="15574-104">To vám dává flexibilitu při vytváření vzhledu, která se liší od vzhled zadaný <xref:System.Windows.Forms.ToolStripProfessionalRenderer> a <xref:System.Windows.Forms.ToolStripSystemRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="15574-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="15574-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="15574-105">Example</span></span>  
 <span data-ttu-id="15574-106">Následující příklad kódu ukazuje, jak implementovat vlastní <xref:System.Windows.Forms.ToolStripRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="15574-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="15574-107">V tomto příkladu `GridStrip` ovládací prvek implementuje stavebnice klouzavé dlaždice, který umožňuje uživatelům přesunutí dlaždice v rozložení tabulky a vytvořit bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="15574-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="15574-108">Vlastní <xref:System.Windows.Forms.ToolStrip> řízení uspořádá jeho <xref:System.Windows.Forms.ToolStripButton> ovládacích prvků v rozložení mřížky.</span><span class="sxs-lookup"><span data-stu-id="15574-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="15574-109">Rozložení obsahuje jeden prázdné buňky, do kterého může uživatel Vysuňte přiléhající dlaždice pomocí operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="15574-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="15574-110">Jsou vyznačené dlaždice, které může uživatel přesunout.</span><span class="sxs-lookup"><span data-stu-id="15574-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="15574-111">`GridStripRenderer` Třída přizpůsobí tři aspekty `GridStrip` vzhledu ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="15574-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
-   <span data-ttu-id="15574-112">`GridStrip`ohraničení</span><span class="sxs-lookup"><span data-stu-id="15574-112">`GridStrip` border</span></span>  
  
-   <span data-ttu-id="15574-113"><xref:System.Windows.Forms.ToolStripButton>ohraničení</span><span class="sxs-lookup"><span data-stu-id="15574-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
-   <span data-ttu-id="15574-114"><xref:System.Windows.Forms.ToolStripButton>bitové kopie</span><span class="sxs-lookup"><span data-stu-id="15574-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15574-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="15574-115">Compiling the Code</span></span>  
 <span data-ttu-id="15574-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="15574-116">This example requires:</span></span>  
  
-   <span data-ttu-id="15574-117">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="15574-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="15574-118">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="15574-118">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="15574-119">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="15574-119">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="15574-120">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="15574-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15574-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="15574-121">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="15574-122">ToolStrip – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15574-122">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
