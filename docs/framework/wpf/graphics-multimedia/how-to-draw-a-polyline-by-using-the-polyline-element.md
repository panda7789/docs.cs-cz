---
title: 'Postupy: Vykreslení lomené čáry použitím elementu lomené čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: 6698141bcaa3b0fd5f5b9cf66bcab1be1f4ea2f0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452958"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="fdcb0-102">Postupy: Vykreslení lomené čáry použitím elementu lomené čáry</span><span class="sxs-lookup"><span data-stu-id="fdcb0-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="fdcb0-103">Tento příklad ukazuje, jak nakreslit lomenou čáru, což je řada propojených řádků pomocí prvku <xref:System.Windows.Shapes.Polyline>.</span><span class="sxs-lookup"><span data-stu-id="fdcb0-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="fdcb0-104">Chcete-li nakreslit lomenou čáru, vytvořte <xref:System.Windows.Shapes.Polyline> element a použijte jeho vlastnost <xref:System.Windows.Shapes.Polyline.Points%2A> k určení vrcholů tvaru.</span><span class="sxs-lookup"><span data-stu-id="fdcb0-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="fdcb0-105">Nakonec pomocí vlastností <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> popište obrys lomené čáry, protože čára bez tahu není viditelná.</span><span class="sxs-lookup"><span data-stu-id="fdcb0-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fdcb0-106">Vzhledem k tomu, že <xref:System.Windows.Shapes.Polyline> element není uzavřený obrazec, vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A> nemá žádný vliv, i když záměrně uzavřete obrys tvaru.</span><span class="sxs-lookup"><span data-stu-id="fdcb0-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="fdcb0-107">Chcete-li vytvořit uzavřený obrazec pomocí <xref:System.Windows.Shapes.Shape.Fill%2A>, použijte prvek <xref:System.Windows.Shapes.Polygon>.</span><span class="sxs-lookup"><span data-stu-id="fdcb0-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="fdcb0-108">Následující příklad kreslí dva prvky <xref:System.Windows.Shapes.Polyline> v rámci <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="fdcb0-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdcb0-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="fdcb0-109">Example</span></span>  
 <span data-ttu-id="fdcb0-110">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]je platná syntaxe pro body oddělená mezerami čárkami oddělený seznam párů souřadnic x a y.</span><span class="sxs-lookup"><span data-stu-id="fdcb0-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="fdcb0-111">Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> k tomu, aby obsahovala lomené čáry, můžete použít prvky lomené čáry (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control>, které podporují obsah, který není textový.</span><span class="sxs-lookup"><span data-stu-id="fdcb0-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="fdcb0-112">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="fdcb0-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdcb0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="fdcb0-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="fdcb0-114">Prvky tvaru – ukázka</span><span class="sxs-lookup"><span data-stu-id="fdcb0-114">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="fdcb0-115">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="fdcb0-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
