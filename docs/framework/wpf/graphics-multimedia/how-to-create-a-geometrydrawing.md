---
title: 'Postupy: Vytvoření objektu GeometryDrawing'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], renderable
- renderable shapes [WPF]
- graphics [WPF], GeometryDrawing class
- classes [WPF], GeometryDrawing
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
ms.openlocfilehash: f5cdcfdb68ad8030bcbd6c689f45a8baddd000e1
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179787"
---
# <a name="how-to-create-a-geometrydrawing"></a><span data-ttu-id="bbc09-102">Postupy: Vytvoření objektu GeometryDrawing</span><span class="sxs-lookup"><span data-stu-id="bbc09-102">How to: Create a GeometryDrawing</span></span>
<span data-ttu-id="bbc09-103">Tento příklad ukazuje, jak vytvořit a zobrazit <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="bbc09-103">This example shows how to create and display a <xref:System.Windows.Media.GeometryDrawing>.</span></span> <span data-ttu-id="bbc09-104">A <xref:System.Windows.Media.GeometryDrawing> umožňuje vytvoření tvaru pomocí výplň a osnovy tím, že přidružíte <xref:System.Windows.Media.Pen> a <xref:System.Windows.Media.Brush> s <xref:System.Windows.Media.Geometry>.</span><span class="sxs-lookup"><span data-stu-id="bbc09-104">A <xref:System.Windows.Media.GeometryDrawing> enables you to create shape with a fill and an outline by associating a <xref:System.Windows.Media.Pen> and a <xref:System.Windows.Media.Brush> with a <xref:System.Windows.Media.Geometry>.</span></span> <span data-ttu-id="bbc09-105"><xref:System.Windows.Media.GeometryDrawing.Geometry%2A> Popisuje strukturu obrazce <xref:System.Windows.Media.GeometryDrawing.Brush%2A> popisuje vyplnění obrazce a <xref:System.Windows.Media.GeometryDrawing.Pen%2A> popisuje obrysu obrazce.</span><span class="sxs-lookup"><span data-stu-id="bbc09-105">The <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> describes the shape's structure, the <xref:System.Windows.Media.GeometryDrawing.Brush%2A> describes the shape's fill, and the <xref:System.Windows.Media.GeometryDrawing.Pen%2A> describes the shape's outline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbc09-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bbc09-106">Example</span></span>  
 <span data-ttu-id="bbc09-107">Následující příklad používá <xref:System.Windows.Media.GeometryDrawing> k vykreslení obrazce.</span><span class="sxs-lookup"><span data-stu-id="bbc09-107">The following example uses a <xref:System.Windows.Media.GeometryDrawing> to render a shape.</span></span> <span data-ttu-id="bbc09-108">Tvar je popsán <xref:System.Windows.Media.GeometryGroup> a dva <xref:System.Windows.Media.EllipseGeometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="bbc09-108">The shape is described by a <xref:System.Windows.Media.GeometryGroup> and two <xref:System.Windows.Media.EllipseGeometry> objects.</span></span> <span data-ttu-id="bbc09-109">Vnitřní obrazce vymalováním s <xref:System.Windows.Media.LinearGradientBrush> a obrysu je vykreslen pomocí <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span><span class="sxs-lookup"><span data-stu-id="bbc09-109">The shape's interior is painted with a <xref:System.Windows.Media.LinearGradientBrush> and its outline is drawn with a <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen>.</span></span> <span data-ttu-id="bbc09-110"><xref:System.Windows.Media.GeometryDrawing> Se zobrazí pomocí <xref:System.Windows.Media.ImageDrawing> a <xref:System.Windows.Controls.Image> elementu.</span><span class="sxs-lookup"><span data-stu-id="bbc09-110">The <xref:System.Windows.Media.GeometryDrawing> is displayed using an <xref:System.Windows.Media.ImageDrawing> and an <xref:System.Windows.Controls.Image> element.</span></span>  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xaml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 <span data-ttu-id="bbc09-111">Následující obrázek znázorňuje výsledný <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="bbc09-111">The following illustration shows the resulting <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="bbc09-112">![GeometryDrawing dvě symbol tří teček](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span><span class="sxs-lookup"><span data-stu-id="bbc09-112">![A GeometryDrawing of two ellipses](./media/graphicsmm-geodraw.jpg "graphicsmm_geodraw")</span></span>  
  
 <span data-ttu-id="bbc09-113">Chcete-li vytvořit složitější kreslení, můžete kombinovat více nakreslených objektů do jedné složeného kreslení pomocí <xref:System.Windows.Media.DrawingGroup>.</span><span class="sxs-lookup"><span data-stu-id="bbc09-113">To create more complex drawings, you can combine multiple drawing objects into a single composite drawing using a <xref:System.Windows.Media.DrawingGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbc09-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bbc09-114">See also</span></span>

- <xref:System.Windows.Media.DrawingGroup>
- [<span data-ttu-id="bbc09-115">Přehled vykreslovaných objektů</span><span class="sxs-lookup"><span data-stu-id="bbc09-115">Drawing Objects Overview</span></span>](drawing-objects-overview.md)
- [<span data-ttu-id="bbc09-116">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="bbc09-116">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="bbc09-117">Vytvoření kompozitní kresby</span><span class="sxs-lookup"><span data-stu-id="bbc09-117">Create a Composite Drawing</span></span>](how-to-create-a-composite-drawing.md)
