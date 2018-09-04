---
title: 'Postupy: Vykreslení obdélníku'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 5f65bd11976817fe3f4d3e5d016f820a249769c3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43506151"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="cffb8-102">Postupy: Vykreslení obdélníku</span><span class="sxs-lookup"><span data-stu-id="cffb8-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="cffb8-103">Tento příklad ukazuje, jak nakreslit obdélník s použitím <xref:System.Windows.Shapes.Rectangle> elementu.</span><span class="sxs-lookup"><span data-stu-id="cffb8-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="cffb8-104">Chcete-li nakreslit obdélník, vytvořte <xref:System.Windows.Shapes.Rectangle> element a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="cffb8-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="cffb8-105">Má Vymalovat vnitřní obdélníku, nastavte jeho <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="cffb8-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="cffb8-106">Obdélník osnovy, použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cffb8-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="cffb8-107">Abyste obdélník zaoblené rohy, zadejte nepovinný <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cffb8-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="cffb8-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> nastaveny vlastnosti osy x a y poloměr elipsy, který se používá k Zakulacení rohů obdélníku.</span><span class="sxs-lookup"><span data-stu-id="cffb8-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="cffb8-109">V následujícím příkladu dvě <xref:System.Windows.Shapes.Rectangle> prvky jsou vykreslovány <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="cffb8-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="cffb8-110">Má první obdélník <xref:System.Windows.Media.Brushes.Blue%2A> vnitřní.</span><span class="sxs-lookup"><span data-stu-id="cffb8-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="cffb8-111">Je druhý obdélník <xref:System.Windows.Media.Brushes.Blue%2A> vnitřní, <xref:System.Windows.Media.Brushes.Black%2A> osnovy a zaoblené rohy.</span><span class="sxs-lookup"><span data-stu-id="cffb8-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cffb8-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="cffb8-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="cffb8-113">Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala obdélníky, můžete použít prvky obdélník (a všechny ostatní prvky tvar) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje netextový obsah.</span><span class="sxs-lookup"><span data-stu-id="cffb8-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="cffb8-114">Ve skutečnosti jsou obzvláště užitečná pozadí pro části obdélníky <xref:System.Windows.Controls.Grid> panelů.</span><span class="sxs-lookup"><span data-stu-id="cffb8-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="cffb8-115">Příklad najdete v tématu [Přehled tabulek](../../../../docs/framework/wpf/advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cffb8-115">For an example, see the [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="cffb8-116">V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [ukázka prvky tvar](https://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="cffb8-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cffb8-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="cffb8-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Rectangle>  
 [<span data-ttu-id="cffb8-118">Ukázka elementy obrazce</span><span class="sxs-lookup"><span data-stu-id="cffb8-118">Shape Elements Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="cffb8-119">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="cffb8-119">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="cffb8-120">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="cffb8-120">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
