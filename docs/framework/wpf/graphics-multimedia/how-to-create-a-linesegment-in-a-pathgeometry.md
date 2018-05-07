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
ms.openlocfilehash: 1cfa9275a2a4508c153cf6ab7ed1c6126b1ee92c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-linesegment-in-a-pathgeometry"></a>Postupy: Vytváření LineSegment v PathGeometry
Tento příklad ukazuje postup vytvoření úsek čáry. Chcete-li vytvořit segment čáry, použijte <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.PathFigure>, a <xref:System.Windows.Media.LineSegment> třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklady kreslení <xref:System.Windows.Media.LineSegment> z (10, 50) na (200, 70). Následující obrázek znázorňuje výsledná <xref:System.Windows.Media.LineSegment>; pozadí tabulky byla přidána do zobrazit souřadnicový systém.  
  
 ![LineSegment v PathFigure](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-pathgeometrylinesegment.png "graphicsmm_pathgeometrylinesegment")  
Objekt LineSegment čerpají z (10,50) na (200,70)  
  
 [xaml]  
  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete použít syntaxi atribut popisující cestu.  
  
```xaml  
<Path Stroke="Black" StrokeThickness="1"    
  Data="M 10,50 L 200,70" />  
```  
  
 [xaml]  
  
 (Všimněte si, že tento atribut syntaxe ve skutečnosti vytvoří <xref:System.Windows.Media.StreamGeometry>, světlejšího váhy verzi <xref:System.Windows.Media.PathGeometry>. Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md) stránky.)  
  
 V [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], úsek čáry může také kreslení pomocí syntaxe element objektu. Tady je ekvivalentem předchozího [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] příklad.  
  
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
  
 Tato ukázka je součástí větší ukázky; Kompletní příklad, najdete v článku [geometrie ukázka](http://go.microsoft.com/fwlink/?LinkID=159989).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.PathFigure>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Media.GeometryDrawing>  
 <xref:System.Windows.Shapes.Path>  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
