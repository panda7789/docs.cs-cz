---
title: Přehled geometrie
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- geometry classes [WPF]
- graphics [WPF], geometry classes
ms.assetid: 9fba8934-98b7-4af6-82f6-f4ef887f963a
ms.openlocfilehash: f4f109b51ed566d1996b0c59b4ecbe51caa022cc
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179995"
---
# <a name="geometry-overview"></a>Přehled geometrie
Tento přehled popisuje způsob použití [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> tříd k popisu obrazce. V tomto tématu jsou také uvedeny rozdíly mezi <xref:System.Windows.Media.Geometry> objekty a <xref:System.Windows.Shapes.Shape> elementy.  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Co je geometrii?  
 <xref:System.Windows.Media.Geometry> Třídy a třídy, které jsou odvozeny z něj, jako například <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, a <xref:System.Windows.Media.CombinedGeometry>, umožňují popsat geometrie 2D obrazce. Tyto popisy geometrické mají mnoho účelů, odpovídající definující tvar k vykreslení na obrazovku nebo definování oblastí spuštění testu a Galerie. Geometrii můžete použít i k definování cestu k animace.  
  
 <xref:System.Windows.Media.Geometry> objekty mohou být jednoduché, například obdélníků a kruhy nebo složený, vytvoření ze dvou nebo více geometrické objekty.  Složitější geometrie lze vytvořit pomocí <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> třídy, které umožňují popsat oblouky a křivky.  
  
 Protože <xref:System.Windows.Media.Geometry> k typu <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> objekty poskytují několik speciální funkce: mohou být deklarovány jako [prostředky](../advanced/xaml-resources.md), sdíleny mezi více objektů, jen pro čtení ke zlepšení výkonu, klonování, a provedené bezpečné pro vlákna. Další informace o různých funkcí poskytovaných službou <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometrie vs. Obrazce  
 <xref:System.Windows.Media.Geometry> a <xref:System.Windows.Shapes.Shape> třídy vypadá to, že podobně jako v tom, že oba popisují 2D obrazce (porovnání <xref:System.Windows.Media.EllipseGeometry> a <xref:System.Windows.Shapes.Ellipse> například), ale existují důležité rozdíly.  
  
 Za prvé <xref:System.Windows.Media.Geometry> třída dědí z <xref:System.Windows.Freezable> třídy při <xref:System.Windows.Shapes.Shape> třída dědí z <xref:System.Windows.FrameworkElement>. Protože jsou prvky, <xref:System.Windows.Shapes.Shape> objekty lze vykreslit sami a součástí systému rozložení při <xref:System.Windows.Media.Geometry> nelze objekty.  
  
 I když <xref:System.Windows.Shapes.Shape> objekty jsou použitelné snadněji než <xref:System.Windows.Media.Geometry> objekty, <xref:System.Windows.Media.Geometry> objekty jsou větší variabilitu. Zatímco <xref:System.Windows.Shapes.Shape> objektu se použije k vykreslení 2D grafika <xref:System.Windows.Media.Geometry> objektu můžete použít k definování geometrické oblast pro 2D grafika, definujte oblast pro ořezové nebo určit oblast pro dosažení testování, například.  
  
### <a name="the-path-shape"></a>Tvar cesty  
 Jeden <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> třídy, ve skutečnosti používá <xref:System.Windows.Media.Geometry> popsat její obsah. Tím, že nastavíte <xref:System.Windows.Shapes.Path.Data%2A> vlastnost <xref:System.Windows.Shapes.Path> s <xref:System.Windows.Media.Geometry> a nastavení jeho <xref:System.Windows.Shapes.Shape.Fill%2A> a <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnosti, které může mít za následek <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Společné vlastnosti, které trvat geometrii  
 V předchozích částech uvedeno, že geometrické objekty lze použít s jinými objekty pro různé účely, jako je například kreslení tvarů, animace a oříznutí. Následující tabulka uvádí několik tříd, které mají vlastnosti, které trvat <xref:System.Windows.Media.Geometry> objektu.  
  
|Type|Vlastnost|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Typy jednoduchých geometrie  
 Základní třída pro všechny geometrie je abstraktní třída <xref:System.Windows.Media.Geometry>.  Třídy, které jsou odvozeny z <xref:System.Windows.Media.Geometry> třídy mohou být seskupeny zhruba do tří kategorií: jednoduché geometrie, cesta geometrie a složené geometrie.  
  
 Jednoduché geometrické třídy zahrnují <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, a <xref:System.Windows.Media.EllipseGeometry> a slouží k vytvoření základní geometrické tvary, třeba řádky, obdélníky a kruzích.  
  
-   A <xref:System.Windows.Media.LineGeometry> je definován tak, že zadáte počáteční bod řádku a koncový bod.  
  
-   A <xref:System.Windows.Media.RectangleGeometry> je definována s <xref:System.Windows.Rect> struktura, která určuje relativní pozici a jeho výška a šířka. Zaoblený obdélník můžete vytvořit tak, že nastavíte <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> vlastnosti.  
  
-   <xref:System.Windows.Media.EllipseGeometry> Je definována středový bod, x-radius a poloměr y.  Následující příklady ukazují, jak vytvořit jednoduchý geometrie pro vykreslování a pro oříznutí.  
  
 Tyto stejné obrazce, jakož i složitější tvary, je možné vytvořit <xref:System.Windows.Media.PathGeometry> nebo kombinací geometrické objekty najednou, ale tyto třídy poskytují jednodušší prostředky pro vytváření těchto základních geometrické tvary.  
  
 Následující příklad ukazuje, jak vytvořit a vykreslování <xref:System.Windows.Media.LineGeometry>.  Jak bylo uvedeno dříve, <xref:System.Windows.Media.Geometry> objektu se nepodařilo vykreslit, tak v příkladu se používá <xref:System.Windows.Shapes.Path> tvar k vykreslení řádku.  Protože řádku nemá žádné oblasti, nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost <xref:System.Windows.Shapes.Path> by neměl žádný vliv; místo toho pouze <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> nejsou zadány vlastnosti. Výstup z příkladu ukazuje následující obrázek.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
LineGeometry vykreslovány z (10,20) (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.EllipseGeometry>.  Příklady sady <xref:System.Windows.Media.EllipseGeometry.Center%2A> z <xref:System.Windows.Media.EllipseGeometry> je nastavena na bod `50,50` a poloměr x a y-radius jsou obě nastaveny na `50`, vytváří kruh průměru 100.  Vnitřní elipsy kresleno přiřazení hodnoty k vlastnosti výplň Path element, v tomto případě <xref:System.Windows.Media.Brushes.Gold%2A>. Výstup z příkladu ukazuje následující obrázek.  
  
 ![EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
EllipseGeometry vykreslovat (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Následující příklad ukazuje, jak vytvořit a vykreslování <xref:System.Windows.Media.RectangleGeometry>.  Určené pozici a rozměry obdélníku <xref:System.Windows.Rect> struktury. Pozice je `50,50` a výška a šířka jsou obě `25`, která vytvoří čtverec. Výstup z příkladu ukazuje následující obrázek.  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry vykreslovat 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Následující příklad ukazuje, jak pomocí <xref:System.Windows.Media.EllipseGeometry> jako oblast ústřižku pro bitovou kopii.  <xref:System.Windows.Controls.Image> Objektu je definována s <xref:System.Windows.FrameworkElement.Width%2A> 200 a <xref:System.Windows.FrameworkElement.Height%2A> 150.  <xref:System.Windows.Media.EllipseGeometry> s <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> hodnotu 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> hodnota 75 a <xref:System.Windows.Media.EllipseGeometry.Center%2A> hodnota 100,75 nastavená na <xref:System.Windows.UIElement.Clip%2A> vlastnosti bitové kopie.  Zobrazí se pouze část obrázku, který je v rámci oblasti se třemi tečkami. Výstup z příkladu ukazuje následující obrázek.  
  
 ![Obrázek a nemusíte výstřižek](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
EllipseGeometry umožňuje oříznout ovládacího prvku pro obrázek  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Cesta geometrie  
 <xref:System.Windows.Media.PathGeometry> Třídy a jeho zjednodušené uživatelé s ekvivalentními oprávněními <xref:System.Windows.Media.StreamGeometry> třídu, poskytují způsob, jak popisují několik komplexní hodnoty tvořené oblouky, křivky a řádky.  
  
 V srdci <xref:System.Windows.Media.PathGeometry> je kolekce <xref:System.Windows.Media.PathFigure> objektů, takže s názvem, protože každý obrázek popisuje diskrétní tvar v <xref:System.Windows.Media.PathGeometry>. Každý <xref:System.Windows.Media.PathFigure> je samotný sestávající z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý popisuje segment na obrázku.  
  
 Existuje mnoho typů segmentů.  
  
|Typ segmentu|Popis|Příklad|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Vytvoří oblouku elipsy mezi dvěma body.|[Vytvoření oblouku elipsy](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Vytvoří kubické Bézierovy křivky mezi dvěma body.|[Vytvoření Kubické Bézierovy křivky](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Vytvoří čáry mezi dvěma body.|[Vytvoření LineSegment v PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Vytvoří řadu kubické Bézierovy křivky.|Zobrazit <xref:System.Windows.Media.PolyBezierSegment> typ stránky.|  
|<xref:System.Windows.Media.PolyLineSegment>|Vytvoří řadu řádky.|Zobrazit <xref:System.Windows.Media.PolyLineSegment> typ stránky.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Vytvoří řadu kvadratické Bézierovy křivky.|Zobrazit <xref:System.Windows.Media.PolyQuadraticBezierSegment> stránky.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Vytvoří kvadratické Bézierovy křivky.|[Vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmenty v rámci <xref:System.Windows.Media.PathFigure> se sloučí do jediného geometrické obrazce s koncový bod každý segment se počáteční bod dalšího segmentu. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Vlastnost <xref:System.Windows.Media.PathFigure> Určuje bod, ze které je vykresleno první segment. Každý další segment začíná na koncový bod předchozího segmentu. Například zobrazuje svislá čára z `10,50` k `10,150` lze definovat tak, že nastavíte <xref:System.Windows.Media.PathFigure.StartPoint%2A> vlastnost `10,50` a vytváření <xref:System.Windows.Media.LineSegment> s <xref:System.Windows.Media.LineSegment.Point%2A> nastavení vlastnosti `10,150`.  
  
 Následující příklad vytvoří jednoduchý <xref:System.Windows.Media.PathGeometry> sestává z jediného <xref:System.Windows.Media.PathFigure> s <xref:System.Windows.Media.LineSegment> a zobrazí ji pomocí <xref:System.Windows.Shapes.Path> elementu. <xref:System.Windows.Media.PathFigure> Objektu <xref:System.Windows.Media.PathFigure.StartPoint%2A> je nastavena na `10,20` a <xref:System.Windows.Media.LineSegment> je definována s koncový bod `100,130`. Je vidět na následujícím obrázku <xref:System.Windows.Media.PathGeometry> vytvořené v tomto příkladu.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
PathGeometry –, který obsahuje jeden LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Je vhodné kontrastní v tomto příkladu s předchozím <xref:System.Windows.Media.LineGeometry> příklad.  Syntaxe pro <xref:System.Windows.Media.PathGeometry> je mnohem podrobnější než, který používá pro jednoduchou <xref:System.Windows.Media.LineGeometry>, a to může být vhodnější použít <xref:System.Windows.Media.LineGeometry> třídy v takovém případě ale podrobné syntaxe <xref:System.Windows.Media.PathGeometry> umožňuje velmi složité a komplexní geometrické oblastech.  
  
 Složitější geometrie lze vytvořit pomocí kombinace <xref:System.Windows.Media.PathSegment> objekty.  
  
 Následující příklad používá <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>a <xref:System.Windows.Media.ArcSegment> k vytvoření tvaru. Příklad nejprve vytvoří kubické Bézierovy křivky je definovat čtyři body: počáteční bod, což je koncový bod předchozího segmentu, koncový bod (<xref:System.Windows.Media.BezierSegment.Point3%2A>), a dvě kontrolní body (<xref:System.Windows.Media.BezierSegment.Point1%2A> a <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Ovládací prvek dva body kubické Bézierovy křivky chovají jako magnets přilákání části co by jinak byly rovné čáry směrem k samotné, vytváření křivky. Bod ovládacím prvku první <xref:System.Windows.Media.BezierSegment.Point1%2A>, má vliv na začátku části křivky; druhý řídicí bod <xref:System.Windows.Media.BezierSegment.Point2%2A>, ovlivňuje koncová část křivky.  
  
 Příklad přidá <xref:System.Windows.Media.LineSegment>, který je vykreslen mezi předchozím koncový bod <xref:System.Windows.Media.BezierSegment> , který před bodu určeného jeho <xref:System.Windows.Media.LineSegment> vlastnost.  
  
 Tento příklad přidá <xref:System.Windows.Media.ArcSegment>, který pochází z koncového bodu předchozí <xref:System.Windows.Media.LineSegment> bodu určeného jeho <xref:System.Windows.Media.ArcSegment.Point%2A> vlastnost. Příklad také určuje oblouku x - a -poloměr y (<xref:System.Windows.Media.ArcSegment.Size%2A>), úhel otočení (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), příznak, který udává, jak velké by měl být úhel oblouku výsledný (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) a hodnotu, která udává, v jakém směru vykreslením oblouku (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Následující obrázek znázorňuje tvar vytvořené v tomto příkladu.  
  
 ![A PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Možné vytvářet i složitější geometrie pomocí několika <xref:System.Windows.Media.PathFigure> objekty v rámci <xref:System.Windows.Media.PathGeometry>.  
  
 Následující příklad vytvoří <xref:System.Windows.Media.PathGeometry> se dvěma <xref:System.Windows.Media.PathFigure> objektů, z nichž každý obsahuje více <xref:System.Windows.Media.PathSegment> objekty.  <xref:System.Windows.Media.PathFigure> z výše uvedeného příkladu a <xref:System.Windows.Media.PathFigure> s <xref:System.Windows.Media.PolyLineSegment> a <xref:System.Windows.Media.QuadraticBezierSegment> se používají.  A <xref:System.Windows.Media.PolyLineSegment> je definována s polem bodů a <xref:System.Windows.Media.QuadraticBezierSegment> je definována s řídicí bod a koncový bod. Následující obrázek znázorňuje tvar vytvořené v tomto příkladu.  
  
 ![A PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry s několika obrázků  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Podobně jako <xref:System.Windows.Media.PathGeometry> třídy, <xref:System.Windows.Media.StreamGeometry> definuje komplexní geometrické obrazce, který může obsahovat křivky oblouky a řádky. Na rozdíl od <xref:System.Windows.Media.PathGeometry>, obsah <xref:System.Windows.Media.StreamGeometry> nepodporují datové vazby, animace nebo úpravy. Použití <xref:System.Windows.Media.StreamGeometry> když potřebujete k popisu komplexní geometry, ale nechcete, aby režii podporuje datové vazby, animace nebo úpravy. Z důvodu jeho efektivitu a <xref:System.Windows.Media.StreamGeometry> třídy je dobrou volbou pro popis doplňků pro úpravy.  
  
 Příklad najdete v tématu [vytvoření tvaru použitím StreamGeometry](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Syntaxe značek cesty  
 <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> podporuje [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] atribut syntaxe pomocí speciální řadu přesunutí a vykreslení příkazů. Další informace najdete v tématu [syntaxe značek cesty](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Složený geometrie  
 Složený geometrické objekty lze vytvořit pomocí <xref:System.Windows.Media.GeometryGroup>, <xref:System.Windows.Media.CombinedGeometry>, nebo voláním statické <xref:System.Windows.Media.Geometry> metoda <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
-   <xref:System.Windows.Media.CombinedGeometry> Objektu a <xref:System.Windows.Media.Geometry.Combine%2A> metoda provádí logické operace zkombinovat oblasti určené dvě geometrie. <xref:System.Windows.Media.Geometry> objekty, které mají žádné oblasti se zahodí. Jenom dva <xref:System.Windows.Media.Geometry> objekty mohou být kombinovány (i když tyto dvě geometrie může také být složené geometrie).  
  
-   <xref:System.Windows.Media.GeometryGroup> Třída vytvoří sloučení <xref:System.Windows.Media.Geometry> objekty obsahuje bez kombinování jejich oblasti. Libovolný počet <xref:System.Windows.Media.Geometry> objekty mohou být přidány do <xref:System.Windows.Media.GeometryGroup>. Příklad najdete v tématu [vytvoření složeného tvaru](how-to-create-a-composite-shape.md).  
  
 Protože neprovádějte operaci combine, pomocí <xref:System.Windows.Media.GeometryGroup> objekty nabízí v porovnání s použitím výkony těží <xref:System.Windows.Media.CombinedGeometry> objekty nebo <xref:System.Windows.Media.Geometry.Combine%2A> metody.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Kombinované geometrie  
 V předchozí části, které jsou uvedené <xref:System.Windows.Media.CombinedGeometry> objektu a <xref:System.Windows.Media.Geometry.Combine%2A> metoda kombinovat oblasti určené geometrie, které obsahují. <xref:System.Windows.Media.GeometryCombineMode> Výčet Určuje, jak jsou zkombinované geometrie. Možné hodnoty parametru <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> vlastnosti jsou: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, a <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je definována s režimem kombinování sjednocení.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Výsledky sjednocení kombinování režimu](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je definována s kombinování režimu <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejného protokolu radius, ale s posunem centra 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Výsledky Xor kombinování režimu](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Další příklady najdete v tématu [vytvoření složeného tvaru](how-to-create-a-composite-shape.md) a [vytvoření kombinované geometrie](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Freezable – funkce  
 Protože dědí sám od <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Geometry> třídy poskytují několik speciálních funkcí: <xref:System.Windows.Media.Geometry> objekty mohou být deklarovány jako [prostředky XAML](../advanced/xaml-resources.md), sdíleny mezi více objektů, jen pro čtení ke zlepšení výkon, klonování a provedli bezpečné pro vlákna. Další informace o různých funkcí poskytovaných službou <xref:System.Windows.Freezable> objekty, najdete [přehled Zablokovatelných objektů](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Další funkce geometrie  
 <xref:System.Windows.Media.Geometry> Třída rovněž poskytuje užitečné pomocné metody, jako je následující:  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> -Získá oblasti <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> -Určuje, zda geometrii obsahuje další <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> -Určuje, zda tah <xref:System.Windows.Media.Geometry> obsahuje zadaný bod.  
  
 Zobrazit <xref:System.Windows.Media.Geometry> třídu pro úplný seznam všech její metody.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Syntaxe značek cesty](path-markup-syntax.md)
- [– postupy](geometries-how-to-topics.md)
- [Přehled animace](animation-overview.md)
- [Tvary a základní kresby v přehledu WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled vykreslovaných objektů](drawing-objects-overview.md)
