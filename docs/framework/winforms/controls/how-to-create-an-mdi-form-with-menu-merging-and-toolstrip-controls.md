---
title: 'Postupy: Vytvoření formuláře MDI s ovládacími prvky Menu Merging a ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripPanel control [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 64992ed9-44af-4baf-b45f-863e6ab35711
ms.openlocfilehash: 0edcc27968c55908cda0e881ed66f83323316711
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591302"
---
# <a name="how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls"></a><span data-ttu-id="45c9c-102">Postupy: Vytvoření formuláře MDI s ovládacími prvky Menu Merging a ToolStrip</span><span class="sxs-lookup"><span data-stu-id="45c9c-102">How to: Create an MDI Form with Menu Merging and ToolStrip Controls</span></span>
<span data-ttu-id="45c9c-103"><xref:System.Windows.Forms?displayProperty=nameWithType> Obor názvů podporuje více dokumentů aplikace (MDI interface) a <xref:System.Windows.Forms.MenuStrip> ovládací prvek podporuje slučování nabídek.</span><span class="sxs-lookup"><span data-stu-id="45c9c-103">The <xref:System.Windows.Forms?displayProperty=nameWithType> namespace supports multiple document interface (MDI) applications, and the <xref:System.Windows.Forms.MenuStrip> control supports menu merging.</span></span> <span data-ttu-id="45c9c-104">MDI formuláře můžete také <xref:System.Windows.Forms.ToolStrip> ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="45c9c-104">MDI forms can also <xref:System.Windows.Forms.ToolStrip> controls.</span></span>  
  
 <span data-ttu-id="45c9c-105">Není k dispozici rozsáhlou podporu pro tuto funkci v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45c9c-105">There is extensive support for this feature in Visual Studio.</span></span>  
  
 <span data-ttu-id="45c9c-106">Viz také [názorný postup: Vytvoření formuláře MDI s ovládacími prvky ToolStrip a slučování nabídek](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span><span class="sxs-lookup"><span data-stu-id="45c9c-106">Also see [Walkthrough: Creating an MDI Form with Menu Merging and ToolStrip Controls](walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="45c9c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="45c9c-107">Example</span></span>  
 <span data-ttu-id="45c9c-108">Následující příklad kódu ukazuje, jak používat <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků formuláře MDI.</span><span class="sxs-lookup"><span data-stu-id="45c9c-108">The following code example demonstrates how to use <xref:System.Windows.Forms.ToolStripPanel> controls with an MDI form.</span></span> <span data-ttu-id="45c9c-109">Formulář podporuje také s nabídkami podřízené slučováním nabídek.</span><span class="sxs-lookup"><span data-stu-id="45c9c-109">The form also supports menu merging with child menus.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.MdiForm#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.MdiForm/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="45c9c-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="45c9c-110">Compiling the Code</span></span>  
 <span data-ttu-id="45c9c-111">Tento příklad kódu vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="45c9c-111">This code example requires:</span></span>  
  
- <span data-ttu-id="45c9c-112">Odkazy na sestavení System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="45c9c-112">References to the System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45c9c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45c9c-113">See also</span></span>

- [<span data-ttu-id="45c9c-114">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="45c9c-114">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
