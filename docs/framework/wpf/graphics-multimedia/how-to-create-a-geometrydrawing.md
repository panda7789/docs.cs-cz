---
title: "Postupy: Vytvoření objektu GeometryDrawing"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31417a3eeee2c1e61674c43558c2799705797c35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="b21e0-102">Postupy: Vytvoření objektu GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="b21e0-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="b21e0-103">Tento příklad ukazuje, jak vytvořit a zobrazit <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="b21e0-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="b21e0-104">A <xref:System.Windows.Media.GeometryDrawing> umožňuje vytvářet obrazce s výplň a tou druhou je tím, že přidružíte <xref:System.Windows.Media.Pen> a <xref:System.Windows.Media.Brush> s <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="b21e0-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="b21e0-105"><xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Popisuje strukturu tvaru, <xref:System.Windows.Media.GeometryDrawing.Brush%2A> popisuje výplň obrazce a <xref:System.Windows.Media.GeometryDrawing.Pen%2A> popisuje obrysu obrazce.</span><span class="sxs-lookup"><span data-stu-id="b21e0-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b21e0-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b21e0-106">Example</span></span>  
 <span data-ttu-id="b21e0-107">Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> k vykreslení obrazce.</span><span class="sxs-lookup"><span data-stu-id="b21e0-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="b21e0-108">Tvar, který je popsán <xref:System.Windows.Media.GeometryGroup> a dvě <xref:System.Windows.Media.EllipseGeometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="b21e0-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="b21e0-109">Vykreslení vnitřního tvaru s <xref:System.Windows.Media.LinearGradientBrush> a jeho obrys vykreslením s <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span><span class="sxs-lookup"><span data-stu-id="b21e0-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="b21e0-110"><xref:System.Windows.Media.GeometryDrawing> Se zobrazí pomocí <xref:System.Windows.Media.ImageDrawing> a <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="b21e0-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="b21e0-111">Následující obrázek znázorňuje výsledná <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="b21e0-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="b21e0-112">![Objekt GeometryDrawing sestávající ze dvou výpustky](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="b21e0-112">![A GeometryDrawing of two ellipses](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="b21e0-113">Chcete-li vytvořit složitější kresby, můžete kombinovat více kreslení objektů do jedné složené kreslení pomocí <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="b21e0-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b21e0-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="b21e0-114">See Also</span></span>  
 <xref:System.Windows.Media.DrawingGroup>  
 [<span data-ttu-id="b21e0-115">Přehled nakreslených objektů</span><span class="sxs-lookup"><span data-stu-id="b21e0-115">Drawing Objects Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [<span data-ttu-id="b21e0-116">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="b21e0-116">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="b21e0-117">Vytvoření kompozitní kresby</span><span class="sxs-lookup"><span data-stu-id="b21e0-117">Create a Composite Drawing</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)
