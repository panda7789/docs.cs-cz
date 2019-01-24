---
title: 'Postupy: Vytvoření čáry použitím LineGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: fbf44f627ede0fe3bdf7e629728a1e3b858fd30e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54690563"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="2a3ee-102">Postupy: Vytvoření čáry použitím LineGeometry</span><span class="sxs-lookup"><span data-stu-id="2a3ee-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="2a3ee-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LineGeometry> tříd k popisu řádku.</span><span class="sxs-lookup"><span data-stu-id="2a3ee-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="2a3ee-104">A <xref:System.Windows.Media.LineGeometry> je definován tak, že jeho počáteční a koncové body.</span><span class="sxs-lookup"><span data-stu-id="2a3ee-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2a3ee-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a3ee-105">Example</span></span>  
 <span data-ttu-id="2a3ee-106">Následující příklad ukazuje, jak vytvořit a vykreslování <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="2a3ee-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="2a3ee-107">A <xref:System.Windows.Shapes.Path> element slouží k vykreslení řádku.</span><span class="sxs-lookup"><span data-stu-id="2a3ee-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="2a3ee-108">Protože řádku nemá žádné oblasti <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Shape.Fill%2A> nezadáte; místo toho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti jsou používány.</span><span class="sxs-lookup"><span data-stu-id="2a3ee-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="2a3ee-109">![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="2a3ee-109">![A LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="2a3ee-110">LineGeometry vykreslovány z (10,20) (100,130)</span><span class="sxs-lookup"><span data-stu-id="2a3ee-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="2a3ee-111">Zahrnout další jednoduché geometrické třídy <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="2a3ee-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="2a3ee-112">Tyto geometrie, jakož i složitější ty lze také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="2a3ee-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="2a3ee-113">Další informace najdete v tématu [přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2a3ee-113">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a3ee-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a3ee-114">See also</span></span>
- [<span data-ttu-id="2a3ee-115">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="2a3ee-115">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [<span data-ttu-id="2a3ee-116">Vytvoření složeného tvaru</span><span class="sxs-lookup"><span data-stu-id="2a3ee-116">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)
- [<span data-ttu-id="2a3ee-117">Vytvoření tvaru pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="2a3ee-117">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
