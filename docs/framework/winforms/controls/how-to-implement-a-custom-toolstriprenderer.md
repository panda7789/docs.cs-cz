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
ms.workload: dotnet
ms.openlocfilehash: 2a717f951e7e804a9f0e06cb51458d7d691632c4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-a-custom-toolstriprenderer"></a><span data-ttu-id="7c541-102">Postupy: Implementace vlastního prvku ToolStripRenderer</span><span class="sxs-lookup"><span data-stu-id="7c541-102">How to: Implement a Custom ToolStripRenderer</span></span>
<span data-ttu-id="7c541-103">Můžete přizpůsobit vzhled <xref:System.Windows.Forms.ToolStrip> řízení implementací třídu odvozenou z <xref:System.Windows.Forms.ToolStripRenderer>.</span><span class="sxs-lookup"><span data-stu-id="7c541-103">You can customize the appearance of a <xref:System.Windows.Forms.ToolStrip> control by implementing a class that derives from <xref:System.Windows.Forms.ToolStripRenderer>.</span></span> <span data-ttu-id="7c541-104">To vám dává flexibilitu při vytváření vzhledu, která se liší od vzhled zadaný <xref:System.Windows.Forms.ToolStripProfessionalRenderer> a <xref:System.Windows.Forms.ToolStripSystemRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="7c541-104">This gives you the flexibility to create an appearance that differs from the appearance provided the <xref:System.Windows.Forms.ToolStripProfessionalRenderer> and <xref:System.Windows.Forms.ToolStripSystemRenderer> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c541-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c541-105">Example</span></span>  
 <span data-ttu-id="7c541-106">Následující příklad kódu ukazuje, jak implementovat vlastní <xref:System.Windows.Forms.ToolStripRenderer> třídy.</span><span class="sxs-lookup"><span data-stu-id="7c541-106">The following code example demonstrates how to implement a custom <xref:System.Windows.Forms.ToolStripRenderer> class.</span></span> <span data-ttu-id="7c541-107">V tomto příkladu `GridStrip` ovládací prvek implementuje stavebnice klouzavé dlaždice, který umožňuje uživatelům přesunutí dlaždice v rozložení tabulky a vytvořit bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="7c541-107">In this example, the `GridStrip` control implements a sliding-tile puzzle, which allows the user to move tiles in a table layout to form an image.</span></span> <span data-ttu-id="7c541-108">Vlastní <xref:System.Windows.Forms.ToolStrip> řízení uspořádá jeho <xref:System.Windows.Forms.ToolStripButton> ovládacích prvků v rozložení mřížky.</span><span class="sxs-lookup"><span data-stu-id="7c541-108">A custom <xref:System.Windows.Forms.ToolStrip> control arranges its <xref:System.Windows.Forms.ToolStripButton> controls in a grid layout.</span></span> <span data-ttu-id="7c541-109">Rozložení obsahuje jeden prázdné buňky, do kterého může uživatel Vysuňte přiléhající dlaždice pomocí operace přetažení myší.</span><span class="sxs-lookup"><span data-stu-id="7c541-109">The layout contains one empty cell, into which the user can slide an adjacent tile by using a drag-and-drop operation.</span></span> <span data-ttu-id="7c541-110">Jsou vyznačené dlaždice, které může uživatel přesunout.</span><span class="sxs-lookup"><span data-stu-id="7c541-110">Tiles that the user can move are highlighted.</span></span>  
  
 <span data-ttu-id="7c541-111">`GridStripRenderer` Třída přizpůsobí tři aspekty `GridStrip` vzhledu ovládacího prvku:</span><span class="sxs-lookup"><span data-stu-id="7c541-111">The `GridStripRenderer` class customizes three aspects of the `GridStrip` control's appearance:</span></span>  
  
-   <span data-ttu-id="7c541-112">`GridStrip`ohraničení</span><span class="sxs-lookup"><span data-stu-id="7c541-112">`GridStrip` border</span></span>  
  
-   <span data-ttu-id="7c541-113"><xref:System.Windows.Forms.ToolStripButton>ohraničení</span><span class="sxs-lookup"><span data-stu-id="7c541-113"><xref:System.Windows.Forms.ToolStripButton> border</span></span>  
  
-   <span data-ttu-id="7c541-114"><xref:System.Windows.Forms.ToolStripButton>bitové kopie</span><span class="sxs-lookup"><span data-stu-id="7c541-114"><xref:System.Windows.Forms.ToolStripButton> image</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/CS/GridStrip.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.GridStrip#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.GridStrip/VB/GridStrip.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c541-115">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7c541-115">Compiling the Code</span></span>  
 <span data-ttu-id="7c541-116">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7c541-116">This example requires:</span></span>  
  
-   <span data-ttu-id="7c541-117">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7c541-117">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="7c541-118">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7c541-118">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7c541-119">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="7c541-119">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="7c541-120">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7c541-120">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c541-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c541-121">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripRenderer>  
 <xref:System.Windows.Forms.ToolStripProfessionalRenderer>  
 <xref:System.Windows.Forms.ToolStripSystemRenderer>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="7c541-122">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="7c541-122">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
