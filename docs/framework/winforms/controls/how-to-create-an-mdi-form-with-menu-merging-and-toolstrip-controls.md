---
title: 'Postupy: Vytvoření formuláře MDI s ovládacími prvky Menu Merging a ToolStrip'
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
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7a7164dc3ebc5dbd77ad54a2bf32f9d603ed7ccf
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="27b4a-102">Postupy: Vytvoření formuláře MDI s ovládacími prvky Menu Merging a ToolStrip</span><span class="sxs-lookup"><span data-stu-id="27b4a-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="27b4a-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů podporuje více aplikací rozhraní (MDI) dokumentu a <xref:System.Windows.Forms.MenuStrip> řízení podporuje slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="27b4a-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="27b4a-104">MDI formuláře může taky <xref:System.Windows.Forms.ToolStrip> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="27b4a-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="27b4a-105">Rozsáhlá podpora pro tuto funkci v sadě Visual Studio není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="27b4a-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="27b4a-106">Viz také [návod: vytvoření formuláře MDI s Menu Merging a ToolStrip – ovládací prvky](http://msdn.microsoft.com/library/ms233676\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="27b4a-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](http://msdn.microsoft.com/library/ms233676\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27b4a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="27b4a-107">Example</span></span>  
 <span data-ttu-id="27b4a-108">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků pomocí formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="27b4a-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="27b4a-109">Formulář podporuje také s nabídkami podřízené slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="27b4a-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="27b4a-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="27b4a-110">Compiling the Code</span></span>  
 <span data-ttu-id="27b4a-111">Tento příklad kódu vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="27b4a-111">This code example requires:</span></span>  
  
-   <span data-ttu-id="27b4a-112">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="27b4a-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="27b4a-113">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="27b4a-113">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="27b4a-114">Tento příklad v sadě Visual Studio můžete také vytvořit zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="27b4a-114">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="27b4a-115">Také sssee [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="27b4a-115">Also sssee [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b4a-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="27b4a-116">See Also</span></span>  
 [<span data-ttu-id="27b4a-117">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="27b4a-117">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
