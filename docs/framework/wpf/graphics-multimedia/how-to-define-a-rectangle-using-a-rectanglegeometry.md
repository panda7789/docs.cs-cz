---
title: "Postupy: Definice obdélníku pomocí RectangleGeometry"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 678d6f36c02c63825782b9f1c860285450a6a9f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a><span data-ttu-id="e4a17-102">Postupy: Definice obdélníku pomocí RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="e4a17-102">How to: Define a Rectangle Using a RectangleGeometry</span></span>
<span data-ttu-id="e4a17-103">Tento příklad popisuje postup použití <xref:System.Windows.Media.RectangleGeometry> třída k popisu obdélníku.</span><span class="sxs-lookup"><span data-stu-id="e4a17-103">This example describes how to use the <xref:System.Windows.Media.RectangleGeometry> class to describe a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4a17-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4a17-104">Example</span></span>  
 <span data-ttu-id="e4a17-105">Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e4a17-105">The following example shows how to create and render a <xref:System.Windows.Media.RectangleGeometry>.</span></span>  <span data-ttu-id="e4a17-106">Definované relativní pozici a dimenze obdélníku <xref:System.Windows.Rect> struktury.</span><span class="sxs-lookup"><span data-stu-id="e4a17-106">The relative position and the dimensions of the rectangle are defined by a <xref:System.Windows.Rect> structure.</span></span> <span data-ttu-id="e4a17-107">Je relativní pozici `50,50` a výška a šířka jsou obě `25` vytváření čtverce.</span><span class="sxs-lookup"><span data-stu-id="e4a17-107">The relative position is `50,50` and the height and the width are both `25` creating a square.</span></span> <span data-ttu-id="e4a17-108">Vykreslení obdélníku interior s <xref:System.Windows.Media.Brushes.LemonChiffon%2A> štětce a jeho přehled vykreslením s <xref:System.Windows.Media.Brushes.Black%2A> tahu s tloušťkou `1`.</span><span class="sxs-lookup"><span data-stu-id="e4a17-108">The rectangle's interior is painted with a <xref:System.Windows.Media.Brushes.LemonChiffon%2A> brush and its outline is painted with a <xref:System.Windows.Media.Brushes.Black%2A> stroke with a thickness of `1`.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 <span data-ttu-id="e4a17-109">![Objekt RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span><span class="sxs-lookup"><span data-stu-id="e4a17-109">![A RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span></span>  
<span data-ttu-id="e4a17-110">RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="e4a17-110">RectangleGeometry</span></span>  
  
 <span data-ttu-id="e4a17-111">I když tento příklad používá <xref:System.Windows.Shapes.Path> element k vykreslení <xref:System.Windows.Media.RectangleGeometry>, existuje mnoho způsobů použití <xref:System.Windows.Media.RectangleGeometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="e4a17-111">Although this example used a <xref:System.Windows.Shapes.Path> element to render the <xref:System.Windows.Media.RectangleGeometry>, there are many other ways to use <xref:System.Windows.Media.RectangleGeometry> objects.</span></span> <span data-ttu-id="e4a17-112">Například <xref:System.Windows.Media.RectangleGeometry> lze použít k určení <xref:System.Windows.UIElement.Clip%2A> z <xref:System.Windows.UIElement> nebo <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> z <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="e4a17-112">For example, a <xref:System.Windows.Media.RectangleGeometry> can be used to specify the <xref:System.Windows.UIElement.Clip%2A> of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> of a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="e4a17-113">Třídy dalších jednoduchý geometrie zahrnují <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e4a17-113">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="e4a17-114">Tyto geometrie, jakož i složitější těch, můžete také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e4a17-114">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a17-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4a17-115">See Also</span></span>  
 [<span data-ttu-id="e4a17-116">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="e4a17-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="e4a17-117">Vytváření kompozitních tvaru</span><span class="sxs-lookup"><span data-stu-id="e4a17-117">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="e4a17-118">Vytvoření obrazce pomocí Objekt PathGeometry</span><span class="sxs-lookup"><span data-stu-id="e4a17-118">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
