---
title: "Postupy: Použití transformace na element při výskytu události"
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
- graphics [WPF], transformations as event responses
- properties [WPF], LayoutTransform
- transformations as event responses [WPF]
- properties [WPF], RenderTransform
- LayoutTransform property [WPF]
ms.assetid: 71e4327e-ca57-444c-a3cf-09fb381491a0
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2e58e49ecc852b87d03d4112208354e608248984
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="bc0c5-102">Postupy: Použití transformace na element při výskytu události</span><span class="sxs-lookup"><span data-stu-id="bc0c5-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="bc0c5-103">Tento příklad ukazuje, jak se má použít <xref:System.Windows.Media.ScaleTransform> při výskytu události.</span><span class="sxs-lookup"><span data-stu-id="bc0c5-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="bc0c5-104">Koncept, které se zobrazí tady je stejný, který používáte pro použití jiné typy transformace.</span><span class="sxs-lookup"><span data-stu-id="bc0c5-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="bc0c5-105">Další informace o dostupných typech transformace najdete v tématu <xref:System.Windows.Media.Transform> třídy nebo [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="bc0c5-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
 <span data-ttu-id="bc0c5-106">Můžete provést transformace pro element v některém z těchto dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="bc0c5-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
-   <span data-ttu-id="bc0c5-107">V takovém případě *není* má transformace ovlivňují rozložení, použijte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.</span><span class="sxs-lookup"><span data-stu-id="bc0c5-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
-   <span data-ttu-id="bc0c5-108">Pokud chcete transformaci, která ovlivňují rozložení, použijte <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost elementu.</span><span class="sxs-lookup"><span data-stu-id="bc0c5-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="bc0c5-109">Následující příklad se vztahuje <xref:System.Windows.Media.ScaleTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="bc0c5-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="bc0c5-110">Při přesunu na tlačítko myši <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti <xref:System.Windows.Media.ScaleTransform> jsou nastaveny na `2`, což způsobí, že tlačítko na velikost větší.</span><span class="sxs-lookup"><span data-stu-id="bc0c5-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="bc0c5-111">Při přesunu vypnout na tlačítko myši <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> jsou nastaveny na `1`, což způsobí, že na tlačítko Obnovit původní velikost.</span><span class="sxs-lookup"><span data-stu-id="bc0c5-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc0c5-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc0c5-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="bc0c5-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc0c5-113">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="bc0c5-114">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="bc0c5-114">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="bc0c5-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="bc0c5-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="bc0c5-116">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="bc0c5-116">Routed Events Overview</span></span>](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
