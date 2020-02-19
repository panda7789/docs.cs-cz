---
title: 'Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 324a5623ee658789b8600a43a89ce26cab7cd6cd
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452971"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="6dd5a-102">Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku</span><span class="sxs-lookup"><span data-stu-id="6dd5a-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="6dd5a-103">Tento příklad ukazuje, jak nakreslit uzavřený obrazec pomocí elementu <xref:System.Windows.Shapes.Polygon>.</span><span class="sxs-lookup"><span data-stu-id="6dd5a-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="6dd5a-104">Chcete-li nakreslit uzavřený obrazec, vytvořte <xref:System.Windows.Shapes.Polygon> element a použijte jeho vlastnost <xref:System.Windows.Shapes.Polygon.Points%2A> k určení vrcholů tvaru.</span><span class="sxs-lookup"><span data-stu-id="6dd5a-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="6dd5a-105">Čára se automaticky vykreslí, aby propojuje první a poslední bod.</span><span class="sxs-lookup"><span data-stu-id="6dd5a-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="6dd5a-106">Nakonec zadejte <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="6dd5a-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6dd5a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="6dd5a-107">Example</span></span>  
 <span data-ttu-id="6dd5a-108">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]je platná syntaxe pro body oddělená mezerami čárkami oddělený seznam párů souřadnic x a y.</span><span class="sxs-lookup"><span data-stu-id="6dd5a-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="6dd5a-109">Přestože příklad používá <xref:System.Windows.Controls.Canvas> k zahrnutí mnohoúhelníků, můžete použít mnohoúhelníkové elementy (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control>, které podporují obsah, který není textový.</span><span class="sxs-lookup"><span data-stu-id="6dd5a-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="6dd5a-110">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="6dd5a-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>
