---
title: "Postupy: Přidání ToolStripContainer do formuláře"
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
- toolbars [Windows Forms], built-in rafting
- ToolStrip control [Windows Forms], built-in rafting
- ToolStripContainer control [Windows Forms], adding to Windows Forms
ms.assetid: d0f55095-a833-453e-be5a-644906d75d54
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5a4089bc6f8ded2c2856318d11b8277811d118c3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-toolstripcontainer-to-a-form"></a><span data-ttu-id="63b57-102">Postupy: Přidání ToolStripContainer do formuláře</span><span class="sxs-lookup"><span data-stu-id="63b57-102">How to: Add a ToolStripContainer to a Form</span></span>
<span data-ttu-id="63b57-103">Prostřednictvím kódu programu můžete přidat <xref:System.Windows.Forms.ToolStripContainer> na formuláři Windows a jeho naplnění ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="63b57-103">You can programmatically add a <xref:System.Windows.Forms.ToolStripContainer> to a Windows Form and populate it with controls.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63b57-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="63b57-104">Example</span></span>  
 <span data-ttu-id="63b57-105">Následující příklad kódu ukazuje, jak přidat <xref:System.Windows.Forms.ToolStripContainer> a <xref:System.Windows.Forms.ToolStrip> do Windows Forms postup přidání položky do <xref:System.Windows.Forms.ToolStrip>a postup přidání <xref:System.Windows.Forms.ToolStrip> k <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> z <xref:System.Windows.Forms.ToolStripContainer>.</span><span class="sxs-lookup"><span data-stu-id="63b57-105">The following code example demonstrates how to add a <xref:System.Windows.Forms.ToolStripContainer> and a <xref:System.Windows.Forms.ToolStrip> to a Windows Forms, how to add items to the <xref:System.Windows.Forms.ToolStrip>, and how to add the <xref:System.Windows.Forms.ToolStrip> to the <xref:System.Windows.Forms.ToolStripContainer.TopToolStripPanel%2A> of the <xref:System.Windows.Forms.ToolStripContainer>.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/cs/form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStripContainer2#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/system.windows.forms.toolstripcontainer2/vb/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="63b57-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="63b57-106">Compiling the Code</span></span>  
 <span data-ttu-id="63b57-107">Tento příklad kódu vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="63b57-107">This code example requires:</span></span>  
  
-   <span data-ttu-id="63b57-108">Odkazy na sestavení System.Drawing System.Text a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="63b57-108">References to the System.Drawing, System.Text, and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="63b57-109">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="63b57-109">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="63b57-110">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="63b57-110">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="63b57-111">Viz také [postupy: zkompilování a spuštění příklad kódu dokončení Windows Forms pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) nebo [ToolStripContainer úloh dialogové okno](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="63b57-111">See also [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)) or [ToolStripContainer Tasks Dialog Box](http://msdn.microsoft.com/library/ms233647\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63b57-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="63b57-112">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [<span data-ttu-id="63b57-113">ToolStripContainer – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="63b57-113">ToolStripContainer Control</span></span>](../../../../docs/framework/winforms/controls/toolstripcontainer-control.md)  
 [<span data-ttu-id="63b57-114">ToolStrip – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="63b57-114">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
