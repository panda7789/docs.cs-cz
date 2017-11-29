---
title: "Postupy: Vykreslení lomené čáry použitím elementu lomené čáry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- connected lines [WPF]
- polylines [WPF], drawing
- graphics [WPF], polylines
- lines [WPF], connected (see polylines)
- drawing [WPF], polylines
ms.assetid: 65db8935-d047-4295-87c4-b427ff3ad293
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5fa8cafdaf7856e95129f648da1d4b4ccb2f54eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-a-polyline-by-using-the-polyline-element"></a><span data-ttu-id="99bba-102">Postupy: Vykreslení lomené čáry použitím elementu lomené čáry</span><span class="sxs-lookup"><span data-stu-id="99bba-102">How to: Draw a Polyline by Using the Polyline Element</span></span>
<span data-ttu-id="99bba-103">Tento příklad ukazuje, jak k vykreslení čar, což je pomocí řady připojené řádky, <xref:System.Windows.Shapes.Polyline> elementu.</span><span class="sxs-lookup"><span data-stu-id="99bba-103">This example shows how to draw a polyline, which is a series of connected lines, by using the <xref:System.Windows.Shapes.Polyline> element.</span></span>  
  
 <span data-ttu-id="99bba-104">Kreslení čar, vytvořit <xref:System.Windows.Shapes.Polyline> elementu a použít jeho <xref:System.Windows.Shapes.Polyline.Points%2A> vlastnosti k určení vrcholy obrazce.</span><span class="sxs-lookup"><span data-stu-id="99bba-104">To draw a polyline, create a <xref:System.Windows.Shapes.Polyline> element and use its <xref:System.Windows.Shapes.Polyline.Points%2A> property to specify the shape vertices.</span></span> <span data-ttu-id="99bba-105">Nakonec použijte <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti k popisu lomenou čáru popisují, protože řádek bez tahu neviditelná.</span><span class="sxs-lookup"><span data-stu-id="99bba-105">Finally, use the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties to describe the polyline outline because a line without a stroke is invisible.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="99bba-106">Protože <xref:System.Windows.Shapes.Polyline> element není uzavřený obrazec <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost nemá žádný vliv, i když úmyslně zavřete obrys tvaru.</span><span class="sxs-lookup"><span data-stu-id="99bba-106">Because the <xref:System.Windows.Shapes.Polyline> element is not a closed shape, the <xref:System.Windows.Shapes.Shape.Fill%2A> property has no effect, even if you deliberately close the shape outline.</span></span> <span data-ttu-id="99bba-107">K vytvoření uzavřený obrazec s <xref:System.Windows.Shapes.Shape.Fill%2A>, používat <xref:System.Windows.Shapes.Polygon> elementu.</span><span class="sxs-lookup"><span data-stu-id="99bba-107">To create a closed shape with a <xref:System.Windows.Shapes.Shape.Fill%2A>, use a <xref:System.Windows.Shapes.Polygon> element.</span></span>  
  
 <span data-ttu-id="99bba-108">Následující příklad nevykresluje dva <xref:System.Windows.Shapes.Polyline> elementy uvnitř <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="99bba-108">The following example draws two <xref:System.Windows.Shapes.Polyline> elements inside a <xref:System.Windows.Controls.Canvas>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="99bba-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="99bba-109">Example</span></span>  
 <span data-ttu-id="99bba-110">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], platná syntaxe pro body je mezerami oddělený seznam párů textový soubor s oddělovači x - a -souřadnici y.</span><span class="sxs-lookup"><span data-stu-id="99bba-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], valid syntax for points is a space-delimited list of comma-separated x- and y-coordinate pairs.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#PolylineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/polylineexample.xaml#polylineexample1)]  
  
 <span data-ttu-id="99bba-111">I když tento příklad používá <xref:System.Windows.Controls.Canvas> tak, aby obsahovala čáru lomených, můžete použít prvky lomenou čáru (a všechny ostatní elementy obrazce) s žádným <xref:System.Windows.Controls.Panel> nebo <xref:System.Windows.Controls.Control> bez textového obsahu, která podporuje.</span><span class="sxs-lookup"><span data-stu-id="99bba-111">Although this example uses a <xref:System.Windows.Controls.Canvas> to contain the polylines, you can use polyline elements (and all the other shape elements) with any <xref:System.Windows.Controls.Panel> or <xref:System.Windows.Controls.Control> that supports non-text content.</span></span>  
  
 <span data-ttu-id="99bba-112">Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v části [ukázka elementy tvaru](http://go.microsoft.com/fwlink/?LinkID=160037).</span><span class="sxs-lookup"><span data-stu-id="99bba-112">This example is part of a larger sample; for the complete sample, see [Shape Elements Sample](http://go.microsoft.com/fwlink/?LinkID=160037).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bba-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="99bba-113">See Also</span></span>  
 <xref:System.Windows.Shapes.Polyline>  
 <xref:System.Windows.Shapes.Polygon>  
 <xref:System.Windows.Shapes.Shape>  
 [<span data-ttu-id="99bba-114">Ukázka elementy obrazce</span><span class="sxs-lookup"><span data-stu-id="99bba-114">Shape Elements Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=160037)  
 [<span data-ttu-id="99bba-115">Tvarů a základní kreslení v přehledu WPF</span><span class="sxs-lookup"><span data-stu-id="99bba-115">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
