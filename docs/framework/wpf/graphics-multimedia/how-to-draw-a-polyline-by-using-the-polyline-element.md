---
title: 'Postupy: Vykreslení lomené čáry pomocí elementu lomené čáry'
ms.date: 03/30/2017
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
ms.openlocfilehash: fb5220082989a9d0a22c4998bb79c0a196067e7e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934960"
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="475ed-102">Postupy: Vykreslení lomené čáry pomocí elementu lomené čáry</span><span class="sxs-lookup"><span data-stu-id="475ed-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="475ed-103">Tento příklad ukazuje, jak vykreslit lomenou čáru, což je řada propojených řádků pomocí <xref:System.Windows.Shapes.Polyline> elementu.</span><span class="sxs-lookup"><span data-stu-id="475ed-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="475ed-104">Chcete-li nakreslit lomenou <xref:System.Windows.Shapes.Polyline> čáru, vytvořte element <xref:System.Windows.Shapes.Polyline.Points%2A> a použijte jeho vlastnost k určení vrcholů tvaru.</span><span class="sxs-lookup"><span data-stu-id="475ed-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="475ed-105">Nakonec pomocí <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastností a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> popište obrys lomené čáry, protože čára bez tahu není viditelná.</span><span class="sxs-lookup"><span data-stu-id="475ed-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="475ed-106">Vzhledem k <xref:System.Windows.Shapes.Polyline> tomu, že element není uzavřený obrazec <xref:System.Windows.Shapes.Shape.Fill%2A> , vlastnost nemá žádný vliv, i když záměrně uzavřete obrys tvaru.</span><span class="sxs-lookup"><span data-stu-id="475ed-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="475ed-107">Chcete-li vytvořit uzavřený obrazec <xref:System.Windows.Shapes.Shape.Fill%2A>pomocí, <xref:System.Windows.Shapes.Polygon> použijte element.</span><span class="sxs-lookup"><span data-stu-id="475ed-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="475ed-108">Následující příklad kreslí dva <xref:System.Windows.Shapes.Polyline> prvky <xref:System.Windows.Controls.Canvas>uvnitř.</span><span class="sxs-lookup"><span data-stu-id="475ed-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="475ed-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="475ed-109">Example</span></span>  
 <span data-ttu-id="475ed-110">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]nástroji je platná syntaxe pro body oddělená mezerami oddělenými čárkami oddělené páry x-a y-souřadnic.</span><span class="sxs-lookup"><span data-stu-id="475ed-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="475ed-111">I když tento příklad používá <xref:System.Windows.Controls.Canvas> a obsahuje lomené čáry, můžete použít prvky lomené čáry (a všechny ostatní prvky obrazce) s jakýmkoli <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje obsah, který není textový.</span><span class="sxs-lookup"><span data-stu-id="475ed-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="475ed-112">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="475ed-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="475ed-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="475ed-113">See also</span></span>

- <xref:System.Windows.Shapes.Polyline>
- <xref:System.Windows.Shapes.Polygon>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="475ed-114">Prvky tvaru – ukázka</span><span class="sxs-lookup"><span data-stu-id="475ed-114">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)
- [<span data-ttu-id="475ed-115">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="475ed-115">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
