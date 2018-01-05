---
title: "Postupy: Vykreslení elipsy nebo kruhu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ellipses [WPF], drawing
- circles [WPF], drawing
- drawing circles [WPF]
- drawing ellipses [WPF]
- graphics [WPF], drawing circles
- graphics [WPF], drawing ellipses
ms.assetid: 99763b8c-bfc8-44be-8231-8a70daf5481a
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8f03fd8cea706e2927ed8e14b4f89a94a208e266
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-an-ellipse-or-a-circle"></a><span data-ttu-id="72a25-102">Postupy: Vykreslení elipsy nebo kruhu</span><span class="sxs-lookup"><span data-stu-id="72a25-102">How to: Draw an Ellipse or a Circle</span></span>
<span data-ttu-id="72a25-103">Tento příklad ukazuje, jak k vykreslení tři tečky a kroužky pomocí <xref:System.Windows.Shapes.Ellipse> elementu.</span><span class="sxs-lookup"><span data-stu-id="72a25-103">This example shows how to draw ellipses and circles by using the <xref:System.Windows.Shapes.Ellipse> element.</span></span> <span data-ttu-id="72a25-104">Kreslení elipsy, vytvořit <xref:System.Windows.Shapes.Ellipse> elementu a zadejte jeho <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="72a25-104">To draw an ellipse, create an <xref:System.Windows.Shapes.Ellipse> element and specify its <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="72a25-105">Použijte jeho <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnosti k určení, <xref:System.Windows.Media.Brush> sloužící k vyplnění vnitřku se třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="72a25-105">Use its <xref:System.Windows.Shapes.Shape.Fill%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the interior of the ellipse.</span></span> <span data-ttu-id="72a25-106">Použijte jeho <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnosti k určení, <xref:System.Windows.Media.Brush> sloužící k vyplnění obrys se třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="72a25-106">Use its <xref:System.Windows.Shapes.Shape.Stroke%2A> property to specify the <xref:System.Windows.Media.Brush> that is used to paint the outline of the ellipse.</span></span> <span data-ttu-id="72a25-107"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A> Vlastnost určuje Tloušťka obrysu třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="72a25-107">The <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> property specifies the thickness of the ellipse outline.</span></span>  
  
 <span data-ttu-id="72a25-108">Kreslení kruh, zkontrolujte <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> z <xref:System.Windows.Shapes.Ellipse> element rovna navzájem.</span><span class="sxs-lookup"><span data-stu-id="72a25-108">To draw a circle, make the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> of the <xref:System.Windows.Shapes.Ellipse> element equal to each other.</span></span>  
  
 <span data-ttu-id="72a25-109">Následující příklad nevykresluje čtyři <xref:System.Windows.Shapes.Ellipse> elementů v rámci <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="72a25-109">The following example draws four <xref:System.Windows.Shapes.Ellipse> elements within a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72a25-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="72a25-110">Example</span></span>  
 [!code-xaml[drawingwithshapeelements#EllipseExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/ellipseexample.xaml#ellipseexample1)]  
  
 <span data-ttu-id="72a25-111">I když tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala na symbol tří teček, můžete použít prvky třemi tečkami (a všechny ostatní elementy obrazce) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> bez textového obsahu, která podporuje.</span><span class="sxs-lookup"><span data-stu-id="72a25-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the ellipses, you can use ellipse elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="72a25-112">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="72a25-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72a25-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="72a25-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Ellipse>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="72a25-114">Ukázka elementy obrazce</span><span class="sxs-lookup"><span data-stu-id="72a25-114">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)
