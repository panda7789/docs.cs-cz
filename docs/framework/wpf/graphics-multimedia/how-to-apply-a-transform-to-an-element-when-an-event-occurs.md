---
title: 'Postupy: Použití transformace na element při výskytu události'
ms.date: 03/30/2017
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
ms.openlocfilehash: 8f04db274432c0e89c6839bef825976c8a2f853c
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64630754"
---
# <a name="how-to-apply-a-transform-to-an-element-when-an-event-occurs"></a><span data-ttu-id="7ec9d-102">Postupy: Použití transformace na element při výskytu události</span><span class="sxs-lookup"><span data-stu-id="7ec9d-102">How to: Apply a Transform to an Element When an Event Occurs</span></span>
<span data-ttu-id="7ec9d-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.ScaleTransform> při výskytu události.</span><span class="sxs-lookup"><span data-stu-id="7ec9d-103">This example shows how to apply a <xref:System.Windows.Media.ScaleTransform> when an event occurs.</span></span> <span data-ttu-id="7ec9d-104">Pojem, který je znázorněna zde je stejný, který používáte pro použití jiné typy transformací.</span><span class="sxs-lookup"><span data-stu-id="7ec9d-104">The concept that is shown here is the same that you use for applying other types of transformations.</span></span> <span data-ttu-id="7ec9d-105">Další informace o dostupných typech transformace, najdete v článku <xref:System.Windows.Media.Transform> třídy nebo [transformuje přehled](transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="7ec9d-105">For more information about the available types of transformations, see the <xref:System.Windows.Media.Transform> class or [Transforms Overview](transforms-overview.md).</span></span>  
  
 <span data-ttu-id="7ec9d-106">Použití transformace na element v některém z těchto způsobů:</span><span class="sxs-lookup"><span data-stu-id="7ec9d-106">You can apply a transform to an element in either of these two ways:</span></span>  
  
- <span data-ttu-id="7ec9d-107">Pokud tak učiníte *není* má transformaci, která ovlivňují rozložení, použijte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost elementu.</span><span class="sxs-lookup"><span data-stu-id="7ec9d-107">If you do *not* want the transform to affect layout, use the <xref:System.Windows.UIElement.RenderTransform%2A> property of the element.</span></span>  
  
- <span data-ttu-id="7ec9d-108">Pokud chcete transformací, která má být ovlivněn rozložení, použijte <xref:System.Windows.FrameworkElement.LayoutTransform%2A> vlastnost elementu.</span><span class="sxs-lookup"><span data-stu-id="7ec9d-108">If you do want the transform to affect layout, use the <xref:System.Windows.FrameworkElement.LayoutTransform%2A> property of the element.</span></span>  
  
 <span data-ttu-id="7ec9d-109">Následující příklad se vztahuje <xref:System.Windows.Media.ScaleTransform> k <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost tlačítka.</span><span class="sxs-lookup"><span data-stu-id="7ec9d-109">The following example applies a <xref:System.Windows.Media.ScaleTransform> to the <xref:System.Windows.UIElement.RenderTransform%2A> property of a button.</span></span> <span data-ttu-id="7ec9d-110">Když se ukazatel myši přesune na tlačítko <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti <xref:System.Windows.Media.ScaleTransform> jsou nastaveny na `2`, což způsobí, že tlačítko větší.</span><span class="sxs-lookup"><span data-stu-id="7ec9d-110">When the mouse moves over the button, the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties of the <xref:System.Windows.Media.ScaleTransform> are set to `2`, which causes the button to become larger.</span></span> <span data-ttu-id="7ec9d-111">Pokud ukazatel myši pohybuje, vypnutí tlačítka, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> jsou nastaveny na `1`, což způsobí, že tlačítko vrátit na původní velikost.</span><span class="sxs-lookup"><span data-stu-id="7ec9d-111">When the mouse moves off the button, <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> are set to `1`, which causes the button to return to its original size.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ec9d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7ec9d-112">Example</span></span>  
 [!code-xaml[ButtonTransform#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml#1)]  
  
 [!code-csharp[ButtonTransform#1cb](~/samples/snippets/csharp/VS_Snippets_Wpf/ButtonTransform/CSharp/ButtonTransformExample.xaml.cs#1cb)]
 [!code-vb[ButtonTransform#1cb](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ButtonTransform/VisualBasic/ButtonTransformExample.xaml.vb#1cb)]  
  
## <a name="see-also"></a><span data-ttu-id="7ec9d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ec9d-113">See also</span></span>

- <xref:System.Windows.Media.Transform>
- <xref:System.Windows.Media.ScaleTransform>
- [<span data-ttu-id="7ec9d-114">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="7ec9d-114">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="7ec9d-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="7ec9d-115">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="7ec9d-116">Přehled směrovaných událostí</span><span class="sxs-lookup"><span data-stu-id="7ec9d-116">Routed Events Overview</span></span>](../advanced/routed-events-overview.md)
