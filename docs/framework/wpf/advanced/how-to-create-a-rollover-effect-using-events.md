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
ms.openlocfilehash: 87740a215136863199d962a2704cf691f27fc3bc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776646"
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="750e1-102">Postupy: Vytvoření efektu přechodu použitím událostí</span><span class="sxs-lookup"><span data-stu-id="750e1-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="750e1-103">Tento příklad ukazuje, jak změnit barvu elementu a ukazatel myši přejde do opustí zabraná elementu.</span><span class="sxs-lookup"><span data-stu-id="750e1-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="750e1-104">Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor a soubor kódu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="750e1-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="750e1-105">Tento příklad ukazuje, jak pomocí událostí, ale je doporučeným způsobem, jak tohoto stejného efektu dosáhnete tak použití <xref:System.Windows.Trigger> ve stylu.</span><span class="sxs-lookup"><span data-stu-id="750e1-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="750e1-106">Další informace najdete v tématu [styly a šablony](../controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="750e1-106">For more information, see [Styling and Templating](../controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="750e1-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="750e1-107">Example</span></span>  
 <span data-ttu-id="750e1-108">Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá z <xref:System.Windows.Controls.Border> kolem <xref:System.Windows.Controls.TextBlock>a připojí <xref:System.Windows.Input.Mouse.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> obslužných rutin událostí k <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="750e1-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="750e1-109">Následující kód vytvoří <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> obslužných rutin událostí.</span><span class="sxs-lookup"><span data-stu-id="750e1-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="750e1-110">Pokud kurzor myši vstoupí <xref:System.Windows.Controls.Border>, na pozadí <xref:System.Windows.Controls.Border> se změní na červený.</span><span class="sxs-lookup"><span data-stu-id="750e1-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="750e1-111">Pokud kurzor myši opustí <xref:System.Windows.Controls.Border>, na pozadí <xref:System.Windows.Controls.Border> se změní zpět na bílou.</span><span class="sxs-lookup"><span data-stu-id="750e1-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](~/samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
