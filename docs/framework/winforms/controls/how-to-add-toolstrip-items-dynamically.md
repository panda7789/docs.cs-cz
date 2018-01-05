---
title: "Postupy: Dynamické přidávání položek ToolStrip"
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
- ContextMenuStrip control [Windows Forms]
- toolbars [Windows Forms], adding items dynamically
- ToolStrip control [Windows Forms]
ms.assetid: 0e8dea56-5f46-408b-914d-7e360341a234
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6aa995643d4b7a00e4d7663a9ce1b8b519250074
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-toolstrip-items-dynamically"></a><span data-ttu-id="eea0d-102">Postupy: Dynamické přidávání položek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="eea0d-102">How to: Add ToolStrip Items Dynamically</span></span>
<span data-ttu-id="eea0d-103">Kolekce položek nabídky jej můžete naplnit dynamicky <xref:System.Windows.Forms.ToolStrip> řízení, když se otevře v nabídce.</span><span class="sxs-lookup"><span data-stu-id="eea0d-103">You can dynamically populate the menu item collection of a <xref:System.Windows.Forms.ToolStrip> control when the menu opens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eea0d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="eea0d-104">Example</span></span>  
 <span data-ttu-id="eea0d-105">Následující příklad kódu ukazuje, jak dynamicky přidat položky do <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="eea0d-105">The following code example demonstrates how to dynamically add items to a <xref:System.Windows.Forms.ContextMenuStrip> control.</span></span> <span data-ttu-id="eea0d-106">Tento příklad také ukazuje, jak použít stejný <xref:System.Windows.Forms.ContextMenuStrip> pro tři různé ovládací prvky na formuláři.</span><span class="sxs-lookup"><span data-stu-id="eea0d-106">The example also shows how to reuse the same <xref:System.Windows.Forms.ContextMenuStrip> for three different controls on the form.</span></span>  
  
 <span data-ttu-id="eea0d-107">V příkladu <xref:System.Windows.Forms.ToolStripDropDown.Opening> obslužné rutiny události naplní kolekce položek nabídky.</span><span class="sxs-lookup"><span data-stu-id="eea0d-107">In the example, an <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler populates the menu item collection.</span></span> <span data-ttu-id="eea0d-108"><xref:System.Windows.Forms.ToolStripDropDown.Opening> Prozkoumá obslužné rutiny události <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> a <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> vlastnosti a přidá <xref:System.Windows.Forms.ToolStripItem> popisující zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="eea0d-108">The <xref:System.Windows.Forms.ToolStripDropDown.Opening> event handler examines the <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A?displayProperty=nameWithType> and <xref:System.Windows.Forms.ToolStripItem.OwnerItem%2A?displayProperty=nameWithType> properties and adds a <xref:System.Windows.Forms.ToolStripItem> describing the source control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#40)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eea0d-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="eea0d-109">Compiling the Code</span></span>  
 <span data-ttu-id="eea0d-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="eea0d-110">This example requires:</span></span>  
  
-   <span data-ttu-id="eea0d-111">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="eea0d-111">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="eea0d-112">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="eea0d-112">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="eea0d-113">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="eea0d-113">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eea0d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="eea0d-114">See Also</span></span>  
 <xref:System.Windows.Forms.ContextMenuStrip>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 <xref:System.Windows.Forms.ToolStripDropDownButton>  
 [<span data-ttu-id="eea0d-115">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="eea0d-115">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
