---
title: 'Postupy: Vytvoření čáry pomocí LineGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
ms.openlocfilehash: f8c334a54f78aec7af91064a447fd18f23dcfbdc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59123055"
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="96b70-102">Postupy: Vytvoření čáry pomocí LineGeometry</span><span class="sxs-lookup"><span data-stu-id="96b70-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="96b70-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LineGeometry> tříd k popisu řádku.</span><span class="sxs-lookup"><span data-stu-id="96b70-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="96b70-104">A <xref:System.Windows.Media.LineGeometry> je definován tak, že jeho počáteční a koncové body.</span><span class="sxs-lookup"><span data-stu-id="96b70-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96b70-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="96b70-105">Example</span></span>  
 <span data-ttu-id="96b70-106">Následující příklad ukazuje, jak vytvořit a vykreslování <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="96b70-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="96b70-107">A <xref:System.Windows.Shapes.Path> element slouží k vykreslení řádku.</span><span class="sxs-lookup"><span data-stu-id="96b70-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="96b70-108">Protože řádku nemá žádné oblasti <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Shape.Fill%2A> nezadáte; místo toho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti jsou používány.</span><span class="sxs-lookup"><span data-stu-id="96b70-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="96b70-109">![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="96b70-109">![A LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="96b70-110">LineGeometry vykreslovány z (10,20) (100,130)</span><span class="sxs-lookup"><span data-stu-id="96b70-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="96b70-111">Zahrnout další jednoduché geometrické třídy <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="96b70-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="96b70-112">Tyto geometrie, jakož i složitější ty lze také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="96b70-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="96b70-113">Další informace najdete v tématu [přehled geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="96b70-113">For more information, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96b70-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96b70-114">See also</span></span>

- [<span data-ttu-id="96b70-115">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="96b70-115">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="96b70-116">Vytvoření složeného tvaru</span><span class="sxs-lookup"><span data-stu-id="96b70-116">Create a Composite Shape</span></span>](how-to-create-a-composite-shape.md)
- [<span data-ttu-id="96b70-117">Vytvoření tvaru pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="96b70-117">Create a Shape by Using a PathGeometry</span></span>](how-to-create-a-shape-by-using-a-pathgeometry.md)
