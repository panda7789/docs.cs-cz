---
title: 'Postupy: Vytváření LineSegment v PathGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: fc7fbad1e534988a36d85c55c1b6a8249692ad67
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452081"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a><span data-ttu-id="a8b20-102">Postupy: Vytváření LineSegment v PathGeometry</span><span class="sxs-lookup"><span data-stu-id="a8b20-102">How to: Create a LineSegment in a PathGeometry</span></span>

<span data-ttu-id="a8b20-103">Tento příklad ukazuje, jak vytvořit segment čáry.</span><span class="sxs-lookup"><span data-stu-id="a8b20-103">This example shows how to create a line segment.</span></span> <span data-ttu-id="a8b20-104">Chcete-li vytvořit segment čáry, použijte třídy <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>a <xref:System.Windows.Media.LineSegment>.</span><span class="sxs-lookup"><span data-stu-id="a8b20-104">To create a line segment, use the <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, and <xref:System.Windows.Media.LineSegment> classes.</span></span>

## <a name="example"></a><span data-ttu-id="a8b20-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8b20-105">Example</span></span>

<span data-ttu-id="a8b20-106">Následující příklady nakreslí <xref:System.Windows.Media.LineSegment> z (10, 50) do (200, 70).</span><span class="sxs-lookup"><span data-stu-id="a8b20-106">The following examples draw a <xref:System.Windows.Media.LineSegment> from (10, 50) to (200, 70).</span></span> <span data-ttu-id="a8b20-107">Následující ilustrace znázorňuje výsledný <xref:System.Windows.Media.LineSegment>; bylo přidáno pozadí mřížky pro zobrazení souřadnicového systému.</span><span class="sxs-lookup"><span data-stu-id="a8b20-107">The following illustration shows the resulting <xref:System.Windows.Media.LineSegment>; a grid background was added to show the coordinate system.</span></span>

<span data-ttu-id="a8b20-108">![LineSegment v PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") LineSegment vykreslený z (10, 50) do (200, 70)</span><span class="sxs-lookup"><span data-stu-id="a8b20-108">![A LineSegment in a PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") A LineSegment drawn from (10,50) to (200,70)</span></span>

<span data-ttu-id="a8b20-109">formátu</span><span class="sxs-lookup"><span data-stu-id="a8b20-109">[xaml]</span></span>

<span data-ttu-id="a8b20-110">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete k popisu cesty použít syntaxi atributu.</span><span class="sxs-lookup"><span data-stu-id="a8b20-110">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may use attribute syntax to describe a path.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1"
  Data="M 10,50 L 200,70" />
```

<span data-ttu-id="a8b20-111">formátu</span><span class="sxs-lookup"><span data-stu-id="a8b20-111">[xaml]</span></span>

<span data-ttu-id="a8b20-112">(Všimněte si, že tato syntaxe atributu ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, což je verze <xref:System.Windows.Media.PathGeometry>s světlejší váhou.</span><span class="sxs-lookup"><span data-stu-id="a8b20-112">(Note that this attribute syntax actually creates a <xref:System.Windows.Media.StreamGeometry>, a lighter-weight version of a <xref:System.Windows.Media.PathGeometry>.</span></span> <span data-ttu-id="a8b20-113">Další informace naleznete na stránce [syntaxe označení cesty](path-markup-syntax.md) .)</span><span class="sxs-lookup"><span data-stu-id="a8b20-113">For more information, see the [Path Markup Syntax](path-markup-syntax.md) page.)</span></span>

<span data-ttu-id="a8b20-114">V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]můžete také nakreslit segment čáry pomocí syntaxe elementů objektu.</span><span class="sxs-lookup"><span data-stu-id="a8b20-114">In [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], you may also draw a line segment by using object element syntax.</span></span> <span data-ttu-id="a8b20-115">Následující příklad je ekvivalentní k předchozímu příkladu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a8b20-115">The following is equivalent to the previous [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] example.</span></span>

```xaml
<Path Stroke="Black" StrokeThickness="1">
  <Path.Data>
    <PathGeometry>
      <PathFigure StartPoint="10,50">
        <LineSegment Point="200,70" />
      </PathFigure>
    </PathGeometry>
  </Path.Data>
</Path>
```

```csharp
PathFigure myPathFigure = new PathFigure();
myPathFigure.StartPoint = new Point(10, 50);

LineSegment myLineSegment = new LineSegment();
myLineSegment.Point = new Point(200, 70);

PathSegmentCollection myPathSegmentCollection = new PathSegmentCollection();
myPathSegmentCollection.Add(myLineSegment);

myPathFigure.Segments = myPathSegmentCollection;

PathFigureCollection myPathFigureCollection = new PathFigureCollection();
myPathFigureCollection.Add(myPathFigure);

PathGeometry myPathGeometry = new PathGeometry();
myPathGeometry.Figures = myPathFigureCollection;

Path myPath = new Path();
myPath.Stroke = Brushes.Black;
myPath.StrokeThickness = 1;
myPath.Data = myPathGeometry;
```

```vb
Dim myPathFigure As New PathFigure()
myPathFigure.StartPoint = New Point(10, 50)

Dim myLineSegment As New LineSegment()
myLineSegment.Point = New Point(200, 70)

Dim myPathSegmentCollection As New PathSegmentCollection()
myPathSegmentCollection.Add(myLineSegment)

myPathFigure.Segments = myPathSegmentCollection

Dim myPathFigureCollection As New PathFigureCollection()
myPathFigureCollection.Add(myPathFigure)

Dim myPathGeometry As New PathGeometry()
myPathGeometry.Figures = myPathFigureCollection

Dim myPath As New Path()
myPath.Stroke = Brushes.Black
myPath.StrokeThickness = 1
myPath.Data = myPathGeometry
```

<span data-ttu-id="a8b20-116">Tento příklad je součástí většího vzorku. úplnou ukázku najdete v [ukázce geometrií](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span><span class="sxs-lookup"><span data-stu-id="a8b20-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/Geometry).</span></span>

## <a name="see-also"></a><span data-ttu-id="a8b20-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8b20-117">See also</span></span>

- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [<span data-ttu-id="a8b20-118">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="a8b20-118">Geometry Overview</span></span>](geometry-overview.md)
