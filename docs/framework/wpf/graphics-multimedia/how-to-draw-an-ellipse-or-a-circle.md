---
title: 'Postupy: Vykreslení elipsy nebo kruhu'
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: ddeada8619d1b6c8970f1efb7cca1bc98773d0c5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44207041"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="e6de4-102">Postupy: Vykreslení elipsy nebo kruhu</span><span class="sxs-lookup"><span data-stu-id="e6de4-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="e6de4-103">Tento příklad ukazuje, jak pomocí vykreslení elipsy nebo kruhu <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="e6de4-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="e6de4-104">Chcete-li nakreslit elipsu, vytvořte <xref:System.Windows.Shapes.Ellipse> element a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6de4-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="e6de4-105">Použití jeho <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnosti a určit tak <xref:System.Windows.Media.Brush> , který se používá k vyplnění vnitřku elipsy.</span><span class="sxs-lookup"><span data-stu-id="e6de4-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="e6de4-106">Použití jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnosti a určit tak <xref:System.Windows.Media.Brush> , který slouží k vykreslení osnovy na tři tečky.</span><span class="sxs-lookup"><span data-stu-id="e6de4-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="e6de4-107"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Vlastnost určuje tloušťku obrysu elipsy.</span><span class="sxs-lookup"><span data-stu-id="e6de4-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="e6de4-108">Pokud chcete nakreslit kruh, ujistěte se, <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Shapes.Ellipse> prvek s hodnotou k sobě navzájem.</span><span class="sxs-lookup"><span data-stu-id="e6de4-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="e6de4-109">Následující příklad nakreslí čtyři <xref:System.Windows.Shapes.Ellipse> elementů v rámci <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="e6de4-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6de4-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6de4-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="e6de4-111">Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> obsahovat symbol tří teček, můžete použít prvky tři tečky (a všechny ostatní prvky tvar) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje netextový obsah.</span><span class="sxs-lookup"><span data-stu-id="e6de4-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="e6de4-112">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="e6de4-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6de4-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6de4-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="e6de4-114">Ukázka elementy obrazce</span><span class="sxs-lookup"><span data-stu-id="e6de4-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
