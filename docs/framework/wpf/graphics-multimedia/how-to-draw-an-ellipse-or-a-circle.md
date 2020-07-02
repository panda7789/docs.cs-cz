---
title: 'Postupy: Vykreslení elipsy nebo kruhu'
description: Naučte se, jak nakreslit elipsu nebo kroužek s volbami pro tloušťku obrysu a vnitřní barvu v Windows Presentation Foundation (WPF).
ms.date: 03/30/2017
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
ms.openlocfilehash: afa0e7d2af42aaee39dca164f23b1a1cacf430ca
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853566"
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="dd502-103">Postupy: Vykreslení elipsy nebo kruhu</span><span class="sxs-lookup"><span data-stu-id="dd502-103">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="dd502-104">Tento příklad ukazuje, jak kreslit elipsy a kroužky pomocí <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="dd502-104">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="dd502-105">Chcete-li nakreslit elipsu, vytvořte <xref:System.Windows.Shapes.Ellipse> element a určete jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="dd502-105">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="dd502-106">Použijte jeho <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost k určení <xref:System.Windows.Media.Brush> , která se používá k vykreslování vnitřku elipsy.</span><span class="sxs-lookup"><span data-stu-id="dd502-106">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="dd502-107">Použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnost k určení <xref:System.Windows.Media.Brush> , který slouží k vykreslování obrysu elipsy.</span><span class="sxs-lookup"><span data-stu-id="dd502-107">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="dd502-108"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>Vlastnost určuje tloušťku obrysu elipsy.</span><span class="sxs-lookup"><span data-stu-id="dd502-108">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="dd502-109">Chcete-li nakreslit kruh, je nutné, aby byl <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> <xref:System.Windows.Shapes.Ellipse> prvek a elementu rovny navzájem.</span><span class="sxs-lookup"><span data-stu-id="dd502-109">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="dd502-110">Následující příklad kreslí čtyři <xref:System.Windows.Shapes.Ellipse> prvky v rámci <xref:System.Windows.Controls.Canvas> .</span><span class="sxs-lookup"><span data-stu-id="dd502-110">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd502-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd502-111">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="dd502-112">I když tento příklad používá a <xref:System.Windows.Controls.Canvas> obsahuje tři tečky, můžete použít prvky elipsy (a všechny ostatní prvky obrazce) s libovolným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> , který podporuje obsah, který není textový.</span><span class="sxs-lookup"><span data-stu-id="dd502-112">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="dd502-113">Tento příklad je součástí většího vzorku; kompletní ukázku naleznete v tématu [Ukázka prvků tvaru](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span><span class="sxs-lookup"><span data-stu-id="dd502-113">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd502-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd502-114">See also</span></span>

- <xref:System.Windows.Shapes.Ellipse>
- <xref:System.Windows.Shapes.Shape>
- [<span data-ttu-id="dd502-115">Prvky tvaru – ukázka</span><span class="sxs-lookup"><span data-stu-id="dd502-115">Shape Elements Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ShapeElements)
