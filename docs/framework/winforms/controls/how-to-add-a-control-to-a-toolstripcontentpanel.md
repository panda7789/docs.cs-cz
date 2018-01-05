---
title: "Postupy: Přidání ovládacího prvku do ToolStripContentPanel"
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
helpviewer_keywords: ToolStripContentPanel [Windows Forms], adding controls
ms.assetid: fa410960-bf1a-42fc-80e8-f2e27fb3dbb8
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e513505dbc25f2eebe8c3ba8353622b3c284297
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-control-to-a-toolstripcontentpanel"></a><span data-ttu-id="9ebcd-102">Postupy: Přidání ovládacího prvku do ToolStripContentPanel</span><span class="sxs-lookup"><span data-stu-id="9ebcd-102">How to: Add a Control to a ToolStripContentPanel</span></span>
<span data-ttu-id="9ebcd-103">Prostřednictvím kódu programu můžete přidat jeden nebo více ovládacích prvků k <xref:System.Windows.Forms.ToolStripContentPanel>.</span><span class="sxs-lookup"><span data-stu-id="9ebcd-103">You can programmatically add one or more controls to a <xref:System.Windows.Forms.ToolStripContentPanel>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9ebcd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ebcd-104">Example</span></span>  
 <span data-ttu-id="9ebcd-105">Následující příklad kódu ukazuje, jak přidat <xref:System.Windows.Forms.RichTextBox> k <xref:System.Windows.Forms.ToolStripContentPanel>.</span><span class="sxs-lookup"><span data-stu-id="9ebcd-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.RichTextBox> to a <xref:System.Windows.Forms.ToolStripContentPanel>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStripContainer/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ebcd-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9ebcd-106">Compiling the Code</span></span>  
 <span data-ttu-id="9ebcd-107">Tento příklad kódu vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9ebcd-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="9ebcd-108">Odkazy na systém, System.Data a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="9ebcd-108">References to the System, System.Data and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="9ebcd-109">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9ebcd-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="9ebcd-110">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="9ebcd-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="9ebcd-111">Viz také [postupy: zkompilování a spuštění příklad kódu dokončení Windows Forms pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) nebo [ToolStripContainer úloh dialogové okno](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="9ebcd-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ebcd-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="9ebcd-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContentPanel>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="9ebcd-113">Ovládací prvek ToolStripContainer</span><span class="sxs-lookup"><span data-stu-id="9ebcd-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [<span data-ttu-id="9ebcd-114">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9ebcd-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
