---
title: "Postupy: Vykreslení obdélníku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- drawing [WPF], rectangles
- graphics [WPF], rectangles
- rectangles [WPF], drawing
ms.assetid: beeb57ef-fab5-4446-a38a-1588f97b4c2f
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 58f29783e48aa7173010ffec6a65f9ac1d8a2b62
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-rectangle"></a><span data-ttu-id="9476d-102">Postupy: Vykreslení obdélníku</span><span class="sxs-lookup"><span data-stu-id="9476d-102">How to: Draw a Rectangle</span></span>
<span data-ttu-id="9476d-103">Tento příklad ukazuje, jak k vykreslení obdélníku pomocí <xref:System.Windows.Shapes.Rectangle> elementu.</span><span class="sxs-lookup"><span data-stu-id="9476d-103">This example shows how to draw a rectangle by using the <xref:System.Windows.Shapes.Rectangle> element.</span></span>  
  
 <span data-ttu-id="9476d-104">Kreslení obdélníku, vytvoření <xref:System.Windows.Shapes.Rectangle> elementu a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="9476d-104">To draw a rectangle, create a <xref:System.Windows.Shapes.Rectangle> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="9476d-105">Chcete-li malovat uvnitř obdélníku, nastavte jeho <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="9476d-105">To paint the inside of the rectangle, set its <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="9476d-106">Rámeček přehled, použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9476d-106">To give the rectangle an outline, use its <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties.</span></span>  
  
 <span data-ttu-id="9476d-107">Umožnit rámeček zaoblenými hranami, zadejte nepovinný <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9476d-107">To give the rectangle rounded corners, specify the optional <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties.</span></span> <span data-ttu-id="9476d-108"><xref:System.Windows.Shapes.Rectangle.RadiusX%2A> a <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> nastavit vlastnosti osy x a y poloměr se třemi tečkami, kterého má být zaokrouhleno rozích rámeček.</span><span class="sxs-lookup"><span data-stu-id="9476d-108">The <xref:System.Windows.Shapes.Rectangle.RadiusX%2A> and <xref:System.Windows.Shapes.Rectangle.RadiusY%2A> properties set the x-axis and y-axis radii of the ellipse that is used to round the corners of the rectangle.</span></span>  
  
 <span data-ttu-id="9476d-109">V následujícím příkladu dvě <xref:System.Windows.Shapes.Rectangle> elementy jsou vykreslovány <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="9476d-109">In the following example, two <xref:System.Windows.Shapes.Rectangle> elements are drawn in a <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="9476d-110">Má první rámeček <xref:System.Windows.Media.Brushes.Blue%2A> vnitřních.</span><span class="sxs-lookup"><span data-stu-id="9476d-110">The first rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior.</span></span> <span data-ttu-id="9476d-111">Druhý rámeček má <xref:System.Windows.Media.Brushes.Blue%2A> vnitřních, <xref:System.Windows.Media.Brushes.Black%2A> outline a zaoblenými hranami.</span><span class="sxs-lookup"><span data-stu-id="9476d-111">The second rectangle has a <xref:System.Windows.Media.Brushes.Blue%2A> interior, a <xref:System.Windows.Media.Brushes.Black%2A> outline, and rounded corners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9476d-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="9476d-112">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#Rectangle1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/rectangleexample.xaml#rectangle1)]  
  
 <span data-ttu-id="9476d-113">I když tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala obdélníků, můžete použít elementy obdélníku (a všechny ostatní elementy obrazce) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> bez textového obsahu, která podporuje.</span><span class="sxs-lookup"><span data-stu-id="9476d-113">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the rectangles, you can use rectangle elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span> <span data-ttu-id="9476d-114">Ve skutečnosti jsou obzvláště užitečná pro zajištění pozadí části obdélníků <xref:System.Windows.Controls.Grid> panelů.</span><span class="sxs-lookup"><span data-stu-id="9476d-114">In fact, rectangles are particularly useful for providing backgrounds for portions of <xref:System.Windows.Controls.Grid> panels.</span></span> <span data-ttu-id="9476d-115">Příklad, naleznete v části [tabulky přehled](../../../../docs/framework/wpf/advanced/table-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9476d-115">For an example, see the [Table Overview](../../../../docs/framework/wpf/advanced/table-overview.md).</span></span>  
  
 <span data-ttu-id="9476d-116">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="9476d-116">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9476d-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9476d-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Rectangle>  
 [<span data-ttu-id="9476d-118">Ukázka elementy obrazce</span><span class="sxs-lookup"><span data-stu-id="9476d-118">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="9476d-119">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="9476d-119">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [<span data-ttu-id="9476d-120">Přehled tabulky</span><span class="sxs-lookup"><span data-stu-id="9476d-120">Table Overview</span></span>](../../../../docs/framework/wpf/advanced/table-overview.md)
