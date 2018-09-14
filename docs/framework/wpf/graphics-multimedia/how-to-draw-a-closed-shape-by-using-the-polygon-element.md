---
title: 'Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], Polygon elements
- closed shapes [WPF], drawing with Polygon elements
- Polygon elements [WPF]
- drawing [WPF], closed shapes with Polygon elements
ms.assetid: 4b0ca008-29ce-48dd-8bc3-f3a20ffca6a6
ms.openlocfilehash: 89c78877e196e803f6b4139ffcfa2b4def1a07d7
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521171"
---
# <a name="how-to-draw-a-closed-shape-by-using-the-polygon-element"></a><span data-ttu-id="be2f5-102">Postupy: Vykreslení zavřeného tvaru použitím mnohoúhelníku</span><span class="sxs-lookup"><span data-stu-id="be2f5-102">How to: Draw a Closed Shape by Using the Polygon Element</span></span>
<span data-ttu-id="be2f5-103">Tento příklad ukazuje způsob vykreslení zavřeného tvaru použitím <xref:System.Windows.Shapes.Polygon> elementu.</span><span class="sxs-lookup"><span data-stu-id="be2f5-103">This example shows how to draw a closed shape by using the <xref:System.Windows.Shapes.Polygon> element.</span></span> <span data-ttu-id="be2f5-104">Vykreslení zavřeného tvaru, vytvořit <xref:System.Windows.Shapes.Polygon> elementu a použijte jeho <xref:System.Windows.Shapes.Polygon.Points%2A> vlastnosti a určit tak vrcholů obrazce.</span><span class="sxs-lookup"><span data-stu-id="be2f5-104">To draw a closed shape, create a <xref:System.Windows.Shapes.Polygon> element and use its <xref:System.Windows.Shapes.Polygon.Points%2A> property to specify the vertices of a shape.</span></span> <span data-ttu-id="be2f5-105">Řádek je automaticky vykreslit, která se připojuje první a poslední bod.</span><span class="sxs-lookup"><span data-stu-id="be2f5-105">A line is automatically drawn that connects the first and last points.</span></span> <span data-ttu-id="be2f5-106">Nakonec zadejte <xref:System.Windows.Shapes.Shape.Fill%2A>, <xref:System.Windows.Shapes.Shape.Stroke%2A>, nebo obojí.</span><span class="sxs-lookup"><span data-stu-id="be2f5-106">Finally, specify a <xref:System.Windows.Shapes.Shape.Fill%2A>, a <xref:System.Windows.Shapes.Shape.Stroke%2A>, or both.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be2f5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="be2f5-107">Example</span></span>  
 <span data-ttu-id="be2f5-108">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], platnou syntaxi pro body je mezerami oddělený seznam párů oddělených čárkou x a y souřadnice.</span><span class="sxs-lookup"><span data-stu-id="be2f5-108">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolygonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polygonexample.xaml#polygonexample1)]  
  
 <span data-ttu-id="be2f5-109">Ačkoli v příkladu se používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala polygonů, můžete použít elementy mnohoúhelníku (a všechny ostatní prvky tvar) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje netextový obsah.</span><span class="sxs-lookup"><span data-stu-id="be2f5-109">Although the example uses a <xref:System.Windows.Controls.Canvas> to contain the polygons, you can use polygon elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="be2f5-110">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="be2f5-110">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>
