---
title: 'Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 4105139e159783cf0197f4e56c82001835077cbf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559458"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="5b75d-102">Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku</span><span class="sxs-lookup"><span data-stu-id="5b75d-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="5b75d-103">Tento příklad ukazuje, jak k vykreslení uzavřený obrazec pomocí <xref:System.Windows.Shapes.Polygon> elementu.</span><span class="sxs-lookup"><span data-stu-id="5b75d-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="5b75d-104">Kreslení uzavřený obrazec, vytvoření <xref:System.Windows.Shapes.Polygon> elementu a použít jeho <xref:System.Windows.Shapes.Polygon.Points%2A> vlastnosti k určení vrcholy obrazce.</span><span class="sxs-lookup"><span data-stu-id="5b75d-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="5b75d-105">Řádek automaticky vykreslením, který se připojuje první a poslední bod.</span><span class="sxs-lookup"><span data-stu-id="5b75d-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="5b75d-106">Nakonec zadejte <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="5b75d-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b75d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="5b75d-107">Example</span></span>  
 <span data-ttu-id="5b75d-108">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], platná syntaxe pro body je mezerami oddělený seznam párů textový soubor s oddělovači x - a -souřadnici y.</span><span class="sxs-lookup"><span data-stu-id="5b75d-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="5b75d-109">I když tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala polygonů, můžete použít elementy mnohoúhelníku (a všechny ostatní elementy obrazce) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> bez textového obsahu, která podporuje.</span><span class="sxs-lookup"><span data-stu-id="5b75d-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="5b75d-110">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="5b75d-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>
