---
title: "Postupy: Vytvoření efektu přechodu použitím událostí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors of elements [WPF], changing
- rollover effect [WPF]
- element colors [WPF], changing
ms.assetid: 3b20d028-6f1c-4b25-95d2-fa68cefbdb4c
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7fc65c9342cc86d4ceebd65e91c05cc1bea464e6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-rollover-effect-using-events"></a><span data-ttu-id="6587c-102">Postupy: Vytvoření efektu přechodu použitím událostí</span><span class="sxs-lookup"><span data-stu-id="6587c-102">How to: Create a Rollover Effect Using Events</span></span>
<span data-ttu-id="6587c-103">Tento příklad ukazuje, jak změnit barvu elementu jako ukazatel myši vstoupí do a z oblasti obsazena elementu.</span><span class="sxs-lookup"><span data-stu-id="6587c-103">This example shows how to change the color of an element as the mouse pointer enters and leaves the area occupied by the element.</span></span>  
  
 <span data-ttu-id="6587c-104">V tomto příkladu se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] a soubor kódu.</span><span class="sxs-lookup"><span data-stu-id="6587c-104">This example consists of a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] file and a code-behind file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6587c-105">Tento příklad ukazuje, jak používat události, ale je doporučeným způsobem, jak dosáhnout Tento stejný účinek použití <xref:System.Windows.Trigger> ve stylu.</span><span class="sxs-lookup"><span data-stu-id="6587c-105">This example demonstrates how to use events, but the recommended way to achieve this same effect is to use a <xref:System.Windows.Trigger> in a style.</span></span> <span data-ttu-id="6587c-106">Další informace najdete v tématu [stylů a ukázka](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span><span class="sxs-lookup"><span data-stu-id="6587c-106">For more information, see [Styling and Templating](../../../../docs/framework/wpf/controls/styling-and-templating.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6587c-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="6587c-107">Example</span></span>  
 <span data-ttu-id="6587c-108">Následující [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] vytvoří uživatelské rozhraní, který se skládá z <xref:System.Windows.Controls.Border> kolem <xref:System.Windows.Controls.TextBlock>a připojí <xref:System.Windows.Input.Mouse.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> obslužné rutiny událostí k <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="6587c-108">The following [!INCLUDE[TLA2#tla_titlexaml](../../../../includes/tla2sharptla-titlexaml-md.md)] creates the user interface, which consists of <xref:System.Windows.Controls.Border> around a <xref:System.Windows.Controls.TextBlock>, and attaches the <xref:System.Windows.Input.Mouse.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers to the <xref:System.Windows.Controls.Border>.</span></span>  
  
 [!code-xaml[mouseenterMouseleave#MouseEnterLeaveSampleXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml#mouseenterleavesamplexaml)]  
  
 <span data-ttu-id="6587c-109">Následující kód vytvoří <xref:System.Windows.UIElement.MouseEnter> a <xref:System.Windows.UIElement.MouseLeave> obslužné rutiny událostí.</span><span class="sxs-lookup"><span data-stu-id="6587c-109">The following code behind creates the <xref:System.Windows.UIElement.MouseEnter> and <xref:System.Windows.UIElement.MouseLeave> event handlers.</span></span>  <span data-ttu-id="6587c-110">Pokud se ukazatel myši vstoupí <xref:System.Windows.Controls.Border>, pozadí <xref:System.Windows.Controls.Border> se změní na červený.</span><span class="sxs-lookup"><span data-stu-id="6587c-110">When the mouse pointer enters the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed to red.</span></span>  <span data-ttu-id="6587c-111">Pokud se ukazatel myši opustí <xref:System.Windows.Controls.Border>, pozadí <xref:System.Windows.Controls.Border> se změní zpět na prázdné.</span><span class="sxs-lookup"><span data-stu-id="6587c-111">When the mouse pointer leaves the <xref:System.Windows.Controls.Border>, the background of the <xref:System.Windows.Controls.Border> is changed back to white.</span></span>  
  
 [!code-csharp[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/mouseenterMouseleave/CSharp/Window1.xaml.cs#mouseenterleavesampleeventhandlers)]
 [!code-vb[mouseenterMouseleave#MouseEnterLeaveSampleEventHandlers](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/mouseenterMouseleave/VisualBasic/Window1.xaml.vb#mouseenterleavesampleeventhandlers)]
