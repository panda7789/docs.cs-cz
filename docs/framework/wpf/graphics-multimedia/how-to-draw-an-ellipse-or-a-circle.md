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
ms.openlocfilehash: 5f17615da4907cba6e25b68f2f934602c2f8a390
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452919"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="97f9d-102">Postupy: Vykreslení elipsy nebo kruhu</span><span class="sxs-lookup"><span data-stu-id="97f9d-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="97f9d-103">Tento příklad ukazuje, jak kreslit elipsy a kroužky pomocí elementu <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="97f9d-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="97f9d-104">Chcete-li nakreslit elipsu, vytvořte prvek <xref:System.Windows.Shapes.Ellipse> a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="97f9d-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="97f9d-105">Použijte jeho vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A> k určení <xref:System.Windows.Media.Brush>, který se používá k malování vnitřku elipsy.</span><span class="sxs-lookup"><span data-stu-id="97f9d-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="97f9d-106">Pomocí vlastnosti <xref:System.Windows.Shapes.Shape.Stroke%2A> určete <xref:System.Windows.Media.Brush>, která se používá k vykreslování obrysu elipsy.</span><span class="sxs-lookup"><span data-stu-id="97f9d-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="97f9d-107">Vlastnost <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> určuje tloušťku obrysu elipsy.</span><span class="sxs-lookup"><span data-stu-id="97f9d-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="97f9d-108">Chcete-li nakreslit kruh, nastavte <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> elementu <xref:System.Windows.Shapes.Ellipse> se vzájemně rovnají.</span><span class="sxs-lookup"><span data-stu-id="97f9d-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="97f9d-109">Následující příklad kreslí čtyři <xref:System.Windows.Shapes.Ellipse> prvky v rámci <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="97f9d-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="97f9d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="97f9d-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="97f9d-111">Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> k tomu, aby obsahoval tři tečky, můžete použít elipsové elementy (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control>, které podporují obsah, který není textový.</span><span class="sxs-lookup"><span data-stu-id="97f9d-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="97f9d-112">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="97f9d-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97f9d-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="97f9d-113">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="97f9d-114">Prvky tvaru – ukázka</span><span class="sxs-lookup"><span data-stu-id="97f9d-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
