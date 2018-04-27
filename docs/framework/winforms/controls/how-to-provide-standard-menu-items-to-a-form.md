---
title: 'Postupy: Zajištění standardních položek nabídky pro formulář'
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
- menu items [Windows Forms], standard
- ToolStrip control [Windows Forms]
ms.assetid: 75db9126-e70c-4e81-921d-b83c0a4a9f50
caps.latest.revision: 7
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 99cdb4971f13ca96a7592a7c718e0898485e8cec
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-provide-standard-menu-items-to-a-form"></a><span data-ttu-id="8eaf6-102">Postupy: Zajištění standardních položek nabídky pro formulář</span><span class="sxs-lookup"><span data-stu-id="8eaf6-102">How to: Provide Standard Menu Items to a Form</span></span>
<span data-ttu-id="8eaf6-103">Můžete zadat standardní nabídky svých formulářů s <xref:System.Windows.Forms.MenuStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8eaf6-103">You can provide a standard menu for your forms with the <xref:System.Windows.Forms.MenuStrip> control.</span></span>  
  
 <span data-ttu-id="8eaf6-104">Je rozsáhlá podpora pro tuto funkci v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="8eaf6-104">There is extensive support for this feature in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].</span></span>  
  
 <span data-ttu-id="8eaf6-105">Viz také [návod: poskytnutí standardních položek nabídky do formuláře](http://msdn.microsoft.com/library/ms233662\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8eaf6-105">Also see [Walkthrough: Providing Standard Menu Items to a Form](http://msdn.microsoft.com/library/ms233662\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8eaf6-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8eaf6-106">Example</span></span>  
 <span data-ttu-id="8eaf6-107">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.MenuStrip> řízení vytvořit formulář s standardní nabídky.</span><span class="sxs-lookup"><span data-stu-id="8eaf6-107">The following code example demonstrates how to use a <xref:System.Windows.Forms.MenuStrip> control to create a form with a standard menu.</span></span> <span data-ttu-id="8eaf6-108">Výběr položek nabídky se zobrazí v <xref:System.Windows.Forms.StatusStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="8eaf6-108">Menu item selections are displayed in a <xref:System.Windows.Forms.StatusStrip> control.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8eaf6-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8eaf6-109">Compiling the Code</span></span>  
 <span data-ttu-id="8eaf6-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="8eaf6-110">This example requires:</span></span>  
  
-   <span data-ttu-id="8eaf6-111">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="8eaf6-111">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="8eaf6-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="8eaf6-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="8eaf6-113">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="8eaf6-113">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="8eaf6-114">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="8eaf6-114">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8eaf6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="8eaf6-115">See Also</span></span>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [<span data-ttu-id="8eaf6-116">Ovládací prvek MenuStrip</span><span class="sxs-lookup"><span data-stu-id="8eaf6-116">MenuStrip Control</span></span>](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
