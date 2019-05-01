---
title: 'Postupy: Vytvoření LineSegment v PathGeometry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- line segments [WPF], creating
- graphics [WPF], line segments
ms.assetid: 0155ed47-a20d-49a7-a306-186d8e07fbc4
ms.openlocfilehash: a50c98ccc3f6d517e0917cb774af4d49d2bfa7a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054546"
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a>Postupy: Vytvoření LineSegment v PathGeometry

Tento příklad ukazuje, jak vytvořit úsek čáry. Chcete-li vytvořit úsek čáry, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.LineSegment> třídy.

## <a name="example"></a>Příklad

Následující příklady nakreslit <xref:System.Windows.Media.LineSegment> z (10, 50) na (200, 70). Následující obrázek znázorňuje výsledný <xref:System.Windows.Media.LineSegment>; mřížky na pozadí byla přidána do souřadnicový systém zobrazení.

![LineSegment v PathFigure](./media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment") A LineSegment vykreslovány z (10,50) (200,70)

[xaml]

V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít syntaxi atributů k popisu cesty.

```xaml
<Path Stroke="Black" StrokeThickness="1"
  Data="M 10,50 L 200,70" />
```

[xaml]

(Všimněte si, že tato syntaxe atributu ve skutečnosti vytváří <xref:System.Windows.Media.StreamGeometry>, nenáročný verzi <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [syntaxe značek cesty](path-markup-syntax.md) stránky.)

V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], mohou také nakreslit úsek čáry pomocí syntaxe elementu objektu. Tady je ekvivalentní předchozí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.

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

V tomto příkladu je součástí větší ukázky; úplnou ukázku najdete v tématu [geometrie ukázka](https://go.microsoft.com/fwlink/?LinkID=159989).

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.PathFigure>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Media.GeometryDrawing>
- <xref:System.Windows.Shapes.Path>
- [Přehled geometrie](geometry-overview.md)
