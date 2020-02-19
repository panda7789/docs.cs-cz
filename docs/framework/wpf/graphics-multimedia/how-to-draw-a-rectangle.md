---
title: 'Postupy: Vykreslení obdélníku'
ms.date: 03/30/2017
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
ms.openlocfilehash: 95191e9d90bc2ac32902399125d9a51192e897bf
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452932"
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="71bcf-102">Postupy: Vykreslení obdélníku</span><span class="sxs-lookup"><span data-stu-id="71bcf-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="71bcf-103">Tento příklad ukazuje, jak vykreslit obdélník pomocí elementu <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="71bcf-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="71bcf-104">Chcete-li nakreslit obdélník, vytvořte prvek <xref:System.Windows.Shapes.Rectangle> a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="71bcf-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="71bcf-105">Chcete-li malovat uvnitř obdélníku, nastavte jeho <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="71bcf-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="71bcf-106">Chcete-li obdélník obsloužit jako obrys, použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> a vlastnosti <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>.</span><span class="sxs-lookup"><span data-stu-id="71bcf-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="71bcf-107">Chcete-li dát obdélník zaoblené rohy, určete volitelné <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a vlastnosti <xref:System.Windows.Shapes.Rectangle.RadiusY%2A>.</span><span class="sxs-lookup"><span data-stu-id="71bcf-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="71bcf-108">Vlastnosti <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> nastavují poloměry osy x a y na elipse, která se používá k zaoblení rohů obdélníku.</span><span class="sxs-lookup"><span data-stu-id="71bcf-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="71bcf-109">V následujícím příkladu jsou vykresleny dva prvky <xref:System.Windows.Shapes.Rectangle> v <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="71bcf-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="71bcf-110">První obdélník má <xref:System.Windows.Media.Brushes.Blue%2A> vnitřní.</span><span class="sxs-lookup"><span data-stu-id="71bcf-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="71bcf-111">Druhý obdélník má <xref:System.Windows.Media.Brushes.Blue%2A> vnitřek, <xref:System.Windows.Media.Brushes.Black%2A> osnovu a zaoblené rohy.</span><span class="sxs-lookup"><span data-stu-id="71bcf-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71bcf-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="71bcf-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="71bcf-113">Přestože tento příklad používá <xref:System.Windows.Controls.Canvas> k zahrnutí obdélníků, můžete použít prvky Rectangle (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control>, které podporují obsah, který není textový.</span><span class="sxs-lookup"><span data-stu-id="71bcf-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="71bcf-114">Obdélníky jsou zejména užitečné pro poskytování pozadí pro části <xref:System.Windows.Controls.Grid> panelů.</span><span class="sxs-lookup"><span data-stu-id="71bcf-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="71bcf-115">Příklad naleznete v [tabulce Přehled](../advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="71bcf-115">For an example, see the [Table Overview](../advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="71bcf-116">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="71bcf-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71bcf-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="71bcf-117">See also</span></span>

- <xref:System.Windows.Shapes.Rectangle>
- [<span data-ttu-id="71bcf-118">Prvky tvaru – ukázka</span><span class="sxs-lookup"><span data-stu-id="71bcf-118">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
- [<span data-ttu-id="71bcf-119">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="71bcf-119">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
- [<span data-ttu-id="71bcf-120">Přehled tabulek</span><span class="sxs-lookup"><span data-stu-id="71bcf-120">Table Overview</span></span>](../advanced/table-overview.md)
