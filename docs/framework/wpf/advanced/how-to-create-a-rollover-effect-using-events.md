---
title: 'Postupy: Vytvoření efektu přechodu použitím událostí'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
ms.openlocfilehash: 806056397200fa5c567e83227499ba721544f523
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005177"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="90695-102">Postupy: Vytvoření efektu přechodu použitím událostí</span><span class="sxs-lookup"><span data-stu-id="90695-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="90695-103">Tento příklad ukazuje, jak změnit barvu prvku jako ukazatel myši do umístění a ponechání oblasti obsazené prvkem.</span><span class="sxs-lookup"><span data-stu-id="90695-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="90695-104">Tento příklad se skládá ze souboru [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a souboru kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="90695-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90695-105">Tento příklad ukazuje, jak použít události, ale doporučený způsob dosažení stejného efektu je použití <xref:System.Windows.Trigger> ve stylu.</span><span class="sxs-lookup"><span data-stu-id="90695-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="90695-106">Další informace najdete v tématu [stylování a šablonování](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="90695-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="90695-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="90695-107">Example</span></span>  
 <span data-ttu-id="90695-108">Následující kód XAML vytvoří uživatelské rozhraní, které se skládá z <xref:System.Windows.Controls.Border> kolem <xref:System.Windows.Controls.TextBlock> a připojí obslužné rutiny událostí <xref:System.Windows.Input.Mouse.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> k <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="90695-108">The following XAML creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="90695-109">Následující kód na pozadí vytvoří obslužné rutiny událostí <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave>.</span><span class="sxs-lookup"><span data-stu-id="90695-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="90695-110">Když ukazatel myši vstoupí do <xref:System.Windows.Controls.Border>, pozadí <xref:System.Windows.Controls.Border> se změní na červenou.</span><span class="sxs-lookup"><span data-stu-id="90695-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="90695-111">Když ukazatel myši opustí <xref:System.Windows.Controls.Border>, pozadí <xref:System.Windows.Controls.Border> se změní zpět na bílou.</span><span class="sxs-lookup"><span data-stu-id="90695-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
