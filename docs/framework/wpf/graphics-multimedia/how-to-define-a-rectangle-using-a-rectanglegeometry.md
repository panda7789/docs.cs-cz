---
title: 'Postupy: Definice obdélníku pomocí RectangleGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
ms.openlocfilehash: 146ca7017ee38ad5c1065e59662ac441e7bfbfe2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075793"
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a><span data-ttu-id="abb79-102">Postupy: Definice obdélníku pomocí RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="abb79-102">How to: Define a Rectangle Using a RectangleGeometry</span></span>
<span data-ttu-id="abb79-103">Tento příklad popisuje způsob použití <xref:System.Windows.Media.RectangleGeometry> tříd k popisu obdélníku.</span><span class="sxs-lookup"><span data-stu-id="abb79-103">This example describes how to use the <xref:System.Windows.Media.RectangleGeometry> class to describe a rectangle.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abb79-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="abb79-104">Example</span></span>  
 <span data-ttu-id="abb79-105">Následující příklad ukazuje, jak vytvořit a vykreslování <xref:System.Windows.Media.RectangleGeometry>.</span><span class="sxs-lookup"><span data-stu-id="abb79-105">The following example shows how to create and render a <xref:System.Windows.Media.RectangleGeometry>.</span></span>  <span data-ttu-id="abb79-106">Relativní pozice a rozměry obdélníku jsou definovány <xref:System.Windows.Rect> struktury.</span><span class="sxs-lookup"><span data-stu-id="abb79-106">The relative position and the dimensions of the rectangle are defined by a <xref:System.Windows.Rect> structure.</span></span> <span data-ttu-id="abb79-107">Relativní pozice je `50,50` a výška a šířka jsou obě `25` Vytvoření čtverce.</span><span class="sxs-lookup"><span data-stu-id="abb79-107">The relative position is `50,50` and the height and the width are both `25` creating a square.</span></span> <span data-ttu-id="abb79-108">Vnitřní obdélníku je vybarvené <xref:System.Windows.Media.Brushes.LemonChiffon%2A> štětce a jeho osnovy vymalováním s <xref:System.Windows.Media.Brushes.Black%2A> od ruky s tloušťkou `1`.</span><span class="sxs-lookup"><span data-stu-id="abb79-108">The rectangle's interior is painted with a <xref:System.Windows.Media.Brushes.LemonChiffon%2A> brush and its outline is painted with a <xref:System.Windows.Media.Brushes.Black%2A> stroke with a thickness of `1`.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 <span data-ttu-id="abb79-109">![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span><span class="sxs-lookup"><span data-stu-id="abb79-109">![A RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")</span></span>  
<span data-ttu-id="abb79-110">RectangleGeometry</span><span class="sxs-lookup"><span data-stu-id="abb79-110">RectangleGeometry</span></span>  
  
 <span data-ttu-id="abb79-111">Přestože tento příklad používá <xref:System.Windows.Shapes.Path> elementu k vykreslení <xref:System.Windows.Media.RectangleGeometry>, existuje mnoho způsobů použití <xref:System.Windows.Media.RectangleGeometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="abb79-111">Although this example used a <xref:System.Windows.Shapes.Path> element to render the <xref:System.Windows.Media.RectangleGeometry>, there are many other ways to use <xref:System.Windows.Media.RectangleGeometry> objects.</span></span> <span data-ttu-id="abb79-112">Například <xref:System.Windows.Media.RectangleGeometry> slouží k určení <xref:System.Windows.UIElement.Clip%2A> z <xref:System.Windows.UIElement> nebo <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> z <xref:System.Windows.Media.GeometryDrawing>.</span><span class="sxs-lookup"><span data-stu-id="abb79-112">For example, a <xref:System.Windows.Media.RectangleGeometry> can be used to specify the <xref:System.Windows.UIElement.Clip%2A> of a <xref:System.Windows.UIElement> or the <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> of a <xref:System.Windows.Media.GeometryDrawing>.</span></span>  
  
 <span data-ttu-id="abb79-113">Zahrnout další jednoduché geometrické třídy <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="abb79-113">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="abb79-114">Tyto geometrie, jakož i složitější ty lze také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="abb79-114">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="abb79-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abb79-115">See also</span></span>

- [<span data-ttu-id="abb79-116">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="abb79-116">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="abb79-117">Vytvoření složeného tvaru</span><span class="sxs-lookup"><span data-stu-id="abb79-117">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="abb79-118">Vytvoření tvaru pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="abb79-118">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
