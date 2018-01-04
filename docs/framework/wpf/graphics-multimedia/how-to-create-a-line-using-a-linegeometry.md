---
title: "Postupy: Vytvoření čáry použitím LineGeometry"
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
helpviewer_keywords: graphics [WPF], lines
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 487a5ffaf952450c6196f5fe0d00fd249177b054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-line-using-a-linegeometry"></a><span data-ttu-id="cec0c-102">Postupy: Vytvoření čáry použitím LineGeometry</span><span class="sxs-lookup"><span data-stu-id="cec0c-102">How to: Create a Line Using a LineGeometry</span></span>
<span data-ttu-id="cec0c-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.LineGeometry> třída k popisu řádku.</span><span class="sxs-lookup"><span data-stu-id="cec0c-103">This example shows how to use the <xref:System.Windows.Media.LineGeometry> class to describe a line.</span></span> <span data-ttu-id="cec0c-104">A <xref:System.Windows.Media.LineGeometry> je definován jeho počáteční a koncové body.</span><span class="sxs-lookup"><span data-stu-id="cec0c-104">A <xref:System.Windows.Media.LineGeometry> is defined by its start and end points.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cec0c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="cec0c-105">Example</span></span>  
 <span data-ttu-id="cec0c-106">Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.LineGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cec0c-106">The following example shows how to create and render a <xref:System.Windows.Media.LineGeometry>.</span></span>  <span data-ttu-id="cec0c-107">A <xref:System.Windows.Shapes.Path> element slouží k vykreslení řádku.</span><span class="sxs-lookup"><span data-stu-id="cec0c-107">A <xref:System.Windows.Shapes.Path> element is used to render the line.</span></span>  <span data-ttu-id="cec0c-108">Vzhledem k tomu, že má řádek žádné oblasti <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Shape.Fill%2A> není zadán; místo toho <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> vlastnosti se používají.</span><span class="sxs-lookup"><span data-stu-id="cec0c-108">Since a line has no area, the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Shape.Fill%2A> is not specified; instead the <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> properties are used.</span></span>  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 <span data-ttu-id="cec0c-109">![Objekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span><span class="sxs-lookup"><span data-stu-id="cec0c-109">![A LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")</span></span>  
<span data-ttu-id="cec0c-110">Objekt LineGeometry čerpají z (10,20) na (100,130)</span><span class="sxs-lookup"><span data-stu-id="cec0c-110">A LineGeometry drawn from (10,20) to (100,130)</span></span>  
  
 <span data-ttu-id="cec0c-111">Třídy dalších jednoduchý geometrie zahrnují <xref:System.Windows.Media.LineGeometry> a <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cec0c-111">Other simple geometry classes include <xref:System.Windows.Media.LineGeometry> and <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="cec0c-112">Tyto geometrie, jakož i složitější těch, můžete také vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo <xref:System.Windows.Media.StreamGeometry>.</span><span class="sxs-lookup"><span data-stu-id="cec0c-112">These geometries, as well as more complex ones, can also be created using a <xref:System.Windows.Media.PathGeometry> or <xref:System.Windows.Media.StreamGeometry>.</span></span> <span data-ttu-id="cec0c-113">Další informace najdete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="cec0c-113">For more information, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cec0c-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="cec0c-114">See Also</span></span>  
 [<span data-ttu-id="cec0c-115">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="cec0c-115">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="cec0c-116">Vytvoření složeného tvaru</span><span class="sxs-lookup"><span data-stu-id="cec0c-116">Create a Composite Shape</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [<span data-ttu-id="cec0c-117">Vytvoření tvaru pomocí PathGeometry</span><span class="sxs-lookup"><span data-stu-id="cec0c-117">Create a Shape by Using a PathGeometry</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
