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
ms.openlocfilehash: 01c460ae18c489a21c860c6d2b10f551e6e68242
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558067"
---
# <a name="geometry-overview"></a>Přehled geometrie
Tento přehled popisuje postup použití [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> třídy k popisu tvarů. V tomto tématu jsou také uvedeny rozdíly mezi <xref:System.Windows.Media.Geometry> objekty a <xref:System.Windows.Shapes.Shape> elementy.  
  
  
<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Co je objekt Geometry?  
 <xref:System.Windows.Media.Geometry> Třídy a třídy, které jsou odvozeny od, jako například <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>, a <xref:System.Windows.Media.CombinedGeometry>, vám umožní popisují geometrie 2D obrazce. Tyto popisy geometrickou mít mnoho používá, takové definování obrazce k vyplnění na obrazovku nebo definování vstupů do testovacích a klip oblasti. Objekt geometry můžete použít i k definování cestu animace.  
  
 <xref:System.Windows.Media.Geometry> třeba obdélníků a kroužky nebo složené, vytvořené ze dvou nebo více objektů geometry, mohou být jednoduchý, objekty.  Složitější geometrie lze vytvořit pomocí <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> třídy, které vám umožní popisují oblouky a křivek.  
  
 Protože <xref:System.Windows.Media.Geometry> je typ <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> objekty poskytují několik speciální funkce: můžete být deklarována jako [prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md), sdílené mezi více objektů, jen pro čtení ke zlepšení výkonu, klonovat, a provedené bezpečné pro přístup z více vláken. Další informace o různých funkcí poskytovaných <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometrie vs. Obrazce  
 <xref:System.Windows.Media.Geometry> a <xref:System.Windows.Shapes.Shape> třídy vypadat podobně jako v tom, že oba popisují 2D obrazce (porovnat <xref:System.Windows.Media.EllipseGeometry> a <xref:System.Windows.Shapes.Ellipse> třeba), ale jsou důležité rozdíly.  
  
 Pro jeden <xref:System.Windows.Media.Geometry> třída dědí z <xref:System.Windows.Freezable> třída při <xref:System.Windows.Shapes.Shape> třída dědí z <xref:System.Windows.FrameworkElement>. Protože jsou elementy, <xref:System.Windows.Shapes.Shape> objekty může vykreslit sami a účast v systému rozložení při <xref:System.Windows.Media.Geometry> nelze objekty.  
  
 I když <xref:System.Windows.Shapes.Shape> objekty jsou více snadno použitelné než <xref:System.Windows.Media.Geometry> objekty, <xref:System.Windows.Media.Geometry> objekty jsou rozmanitější. Při <xref:System.Windows.Shapes.Shape> objektu slouží k vykreslení 2D grafiky <xref:System.Windows.Media.Geometry> objekt lze použít k definování geometrickou oblast pro 2D grafiky, definovat oblast pro výstřižek nebo určit oblasti pro testování přístupů, například.  
  
### <a name="the-path-shape"></a>Tvar cesty  
 Jeden <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> třídy, ve skutečnosti používá <xref:System.Windows.Media.Geometry> k popisu její obsah. Nastavením <xref:System.Windows.Shapes.Path.Data%2A> vlastnost <xref:System.Windows.Shapes.Path> s <xref:System.Windows.Media.Geometry> a nastavení jeho <xref:System.Windows.Shapes.Shape.Fill%2A> a <xref:System.Windows.Shapes.Shape.Stroke%2A> vlastnosti, může vykreslit <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Společné vlastnosti, které trvat Geometry  
 V předchozích částech uvedeno, že objekty geometrie lze použít s jinými objekty pro jiné účely, například kreslení tvarů, animace a výstřižek. Následující tabulka uvádí několik tříd, které mají vlastnosti, které trvat <xref:System.Windows.Media.Geometry> objektu.  
  
|Typ|Vlastnost|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Jednoduché geometrie typy  
 Základní třída pro všechny geometrie je abstraktní třída <xref:System.Windows.Media.Geometry>.  Odvozené třídy <xref:System.Windows.Media.Geometry> třídy můžete zhruba rozdělit do tří kategorií: jednoduchý geometrie, cesta geometrie a složené geometrie.  
  
 Třídy jednoduchého geometrie zahrnují <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, a <xref:System.Windows.Media.EllipseGeometry> a slouží k vytváření základní geometrické obrazce, např. řádky, obdélníků a kroužky.  
  
-   A <xref:System.Windows.Media.LineGeometry> je definována bodem počáteční a koncový bod.  
  
-   A <xref:System.Windows.Media.RectangleGeometry> je definovaná pomocí <xref:System.Windows.Rect> struktura, která určuje relativní pozici a jeho výškou a šířkou. Můžete vytvořit zaoblený obdélník nastavením <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> vlastnosti.  
  
-   <xref:System.Windows.Media.EllipseGeometry> Je definován středový bod, protokolu radius x a y-radius.  Následující příklady ukazují, jak vytvořit jednoduché geometrie pro vykreslování a výstřižek.  
  
 Tyto stejné tvarů, jakož i složitější tvarů, můžete vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo kombinací geometrie objekty společně, ale tyto třídy poskytují jednodušší prostředky pro vytvoření tyto základní geometrické obrazce.  
  
 Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.LineGeometry>.  Jak už jsme zmínili dřív, <xref:System.Windows.Media.Geometry> objekt se nepodařilo kreslení sebe, tak v příkladu se používá <xref:System.Windows.Shapes.Path> tvar, který má vykreslit řádek.  Protože řádek má žádné oblasti, nastavení <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost <xref:System.Windows.Shapes.Path> by mít žádný vliv; místo toho pouze <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> jsou zadané vlastnosti. Následující obrázek znázorňuje výstup z příkladu.  
  
 ![Objekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
Objekt LineGeometry čerpají z (10,20) na (100,130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 Další příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.EllipseGeometry>.  Příklady nastaví <xref:System.Windows.Media.EllipseGeometry.Center%2A> z <xref:System.Windows.Media.EllipseGeometry> je nastavena na bod `50,50` a protokolu radius x a y-radius jsou obě nastaveny na `50`, vytváří kruh o průměru 100.  Vnitřní se třemi tečkami vykreslením přiřazením hodnoty pro vlastnost výplně element cesty, v takovém případě <xref:System.Windows.Media.Brushes.Gold%2A>. Následující obrázek znázorňuje výstup z příkladu.  
  
 ![Objekt EllipseGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Objekt EllipseGeometry vykreslovat (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.RectangleGeometry>.  Pozice a dimenze obdélníku jsou definovány <xref:System.Windows.Rect> struktura. Pozice je `50,50` a výška a šířka jsou obě `25`, která vytvoří čtverce. Následující obrázek znázorňuje výstup z příkladu.  
  
 ![Objekt RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Objekt RectangleGeometry vykreslovat 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Následující příklad ukazuje, jak používat <xref:System.Windows.Media.EllipseGeometry> jako klip oblast pro bitovou kopii.  <xref:System.Windows.Controls.Image> Objektu je definována pomocí <xref:System.Windows.FrameworkElement.Width%2A> 200 a <xref:System.Windows.FrameworkElement.Height%2A> 150.  <xref:System.Windows.Media.EllipseGeometry> s <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> hodnotu 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> hodnota 75 a <xref:System.Windows.Media.EllipseGeometry.Center%2A> hodnota 100,75 nastavena na <xref:System.Windows.UIElement.Clip%2A> vlastnost bitové kopie.  Zobrazí se pouze část obrázku, který je v oblasti se třemi tečkami. Následující obrázek znázorňuje výstup z příkladu.  
  
 ![Obrázek s i bez výstřižek](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
Objekt EllipseGeometry používá k oříznutí ovládacího prvku obrázek  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Cesta geometrie  
 <xref:System.Windows.Media.PathGeometry> Třídy a ekvivalentní šedé – <xref:System.Windows.Media.StreamGeometry> třídu, poskytují způsob, jak popisují více komplexní útvarů tvořený oblouky, křivek a řádky.  
  
 Jádrem <xref:System.Windows.Media.PathGeometry> je kolekce <xref:System.Windows.Media.PathFigure> objekty, takže s názvem, protože každý obrázek popisuje diskrétní obrazce v <xref:System.Windows.Media.PathGeometry>. Každý <xref:System.Windows.Media.PathFigure> se sám skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý popisuje segment na obrázku.  
  
 Existuje mnoho typů segmentů.  
  
|Typ segmentu|Popis|Příklad|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Vytvoří oblouk eliptické mezi dva body.|[Vytvoření eliptické oblouk](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Vytvoří krychlový Bézierovu křivku mezi dva body.|[Vytvoření krychlový Bézierovu křivku](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Vytvoří řádek mezi dva body.|[Vytvoření LineSegment v PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Vytvoří řadu krychlový Bézierových křivek.|Najdete v článku <xref:System.Windows.Media.PolyBezierSegment> typ stránky.|  
|<xref:System.Windows.Media.PolyLineSegment>|Vytvoří řadu řádky.|Najdete v článku <xref:System.Windows.Media.PolyLineSegment> typ stránky.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Vytvoří řadu kvadratické Bézierovy křivky.|Najdete v článku <xref:System.Windows.Media.PolyQuadraticBezierSegment> stránky.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Vytvoří kvadratické Bézierovy křivky.|[Vytvoření kvadratické Bézierovy křivky](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmenty v rámci <xref:System.Windows.Media.PathFigure> jsou sloučeny do jednoho geometrické obrazce s koncovým bodem každý segment se počáteční bod další segmentu. <xref:System.Windows.Media.PathFigure.StartPoint%2A> Vlastnost <xref:System.Windows.Media.PathFigure> Určuje bod, ze kterého se nevykreslí první segment. Každý další segment začíná na koncový bod předchozího segmentu. Například svislá čára z `10,50` k `10,150` můžete definovat nastavením <xref:System.Windows.Media.PathFigure.StartPoint%2A> vlastnost `10,50` a vytváření <xref:System.Windows.Media.LineSegment> s <xref:System.Windows.Media.LineSegment.Point%2A> vlastnost na hodnotu `10,150`.  
  
 Následující příklad vytvoří jednoduchou <xref:System.Windows.Media.PathGeometry> skládá z jedné <xref:System.Windows.Media.PathFigure> s <xref:System.Windows.Media.LineSegment> a zobrazí pomocí <xref:System.Windows.Shapes.Path> elementu. <xref:System.Windows.Media.PathFigure> Objektu <xref:System.Windows.Media.PathFigure.StartPoint%2A> je nastaven na `10,20` a <xref:System.Windows.Media.LineSegment> je definován s koncovým bodem `100,130`. Následující obrázek ukazuje <xref:System.Windows.Media.PathGeometry> vytvořené v tomto příkladu.  
  
 ![Objekt LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.gif "graphicsmm_line")  
PathGeometry, který obsahuje jeden LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Je vhodné kontrastní tento příklad s předchozím <xref:System.Windows.Media.LineGeometry> příklad.  Syntaxe pro <xref:System.Windows.Media.PathGeometry> je mnohem podrobnější než pro jednoduchý <xref:System.Windows.Media.LineGeometry>, a má smysl další používat <xref:System.Windows.Media.LineGeometry> třídy v tomto případě ale podrobné syntaxe <xref:System.Windows.Media.PathGeometry> umožňuje velmi složité a komplexní geometrickou oblasti.  
  
 Složitější geometrie lze vytvořit pomocí kombinace <xref:System.Windows.Media.PathSegment> objekty.  
  
 Další příklad používá <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>a <xref:System.Windows.Media.ArcSegment> vytvořte tvaru. V příkladu se vytváří nejprve krychlový Bézierovy křivky je tak, že definujete čtyři body: počáteční bod, který je koncový bod předchozího segmentu, koncový bod (<xref:System.Windows.Media.BezierSegment.Point3%2A>), a dva řídit body (<xref:System.Windows.Media.BezierSegment.Point1%2A> a <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Ovládací prvek dva body krychlový Bézierovy křivky chovat jako magnets, získání části co by se jinak mohly přímku směrem sami, který vytvořil křivka. První prvek bod, <xref:System.Windows.Media.BezierSegment.Point1%2A>, má vliv na začátku část křivky; druhý řídicí bod <xref:System.Windows.Media.BezierSegment.Point2%2A>, ovlivňuje koncová část křivku.  
  
 V příkladu se pak přidá <xref:System.Windows.Media.LineSegment>, který vykreslením mezi koncovým bodem předchozím <xref:System.Windows.Media.BezierSegment> , před bodu určeného jeho <xref:System.Windows.Media.LineSegment> vlastnost.  
  
 V příkladu se pak přidá <xref:System.Windows.Media.ArcSegment>, což je čerpají z koncového bodu předchozích <xref:System.Windows.Media.LineSegment> bodu určeného jeho <xref:System.Windows.Media.ArcSegment.Point%2A> vlastnost. Tento příklad také určuje oblouku x - a y-radius (<xref:System.Windows.Media.ArcSegment.Size%2A>), úhel otočení (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), příznak, který udává, jak velké by měla být úhel oblouku výsledné (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>) a hodnotu, která určuje, kterým směrem oblouk vykreslením (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Následující obrázek znázorňuje tvaru vytvořené v tomto příkladu.  
  
 ![Objekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path2.gif "graphicsmm_path2")  
Objekt PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 I složitější geometrie lze vytvořit pomocí několika <xref:System.Windows.Media.PathFigure> objekty v rámci <xref:System.Windows.Media.PathGeometry>.  
  
 Následující příklad vytvoří <xref:System.Windows.Media.PathGeometry> se dvěma <xref:System.Windows.Media.PathFigure> objekty, z nichž každý obsahuje více <xref:System.Windows.Media.PathSegment> objekty.  <xref:System.Windows.Media.PathFigure> z výše uvedeném příkladu a <xref:System.Windows.Media.PathFigure> s <xref:System.Windows.Media.PolyLineSegment> a <xref:System.Windows.Media.QuadraticBezierSegment> se používají.  A <xref:System.Windows.Media.PolyLineSegment> je definovaná pomocí pole bodů a <xref:System.Windows.Media.QuadraticBezierSegment> je definovaná pomocí řídicího bodu a koncový bod. Následující obrázek znázorňuje tvaru vytvořené v tomto příkladu.  
  
 ![Objekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry s více obrázků  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Podobně jako <xref:System.Windows.Media.PathGeometry> třída, <xref:System.Windows.Media.StreamGeometry> definuje komplexní geometrickou tvar, který může obsahovat čar, křivek a oblouky. Na rozdíl od <xref:System.Windows.Media.PathGeometry>, obsah <xref:System.Windows.Media.StreamGeometry> nepodporují vazby dat, animace nebo úpravy. Použití <xref:System.Windows.Media.StreamGeometry> když potřebujete popisují komplexní geometry, ale nechcete, aby nároky na podporu vazby dat, animace nebo úpravy. Z důvodu jeho efektivitu <xref:System.Windows.Media.StreamGeometry> třída je vhodná pro popisující ozdobného prvku.  
  
 Příklad, naleznete v části [vytvoření obrazce pomocí StreamGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Syntaxe značek cesty  
 <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> typy podpory [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] atribut syntaxe pomocí speciální řadu přesunutí a kreslení příkazy. Další informace najdete v tématu [syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Složené geometrie  
 Složené geometrie objekty mohou být vytvořeny pomocí <xref:System.Windows.Media.GeometryGroup>, <xref:System.Windows.Media.CombinedGeometry>, nebo voláním statické <xref:System.Windows.Media.Geometry> metoda <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
-   <xref:System.Windows.Media.CombinedGeometry> Objektu a <xref:System.Windows.Media.Geometry.Combine%2A> metoda provádí logická operace kombinovat oblasti určené dvě geometrie. <xref:System.Windows.Media.Geometry> objekty, které mají žádné oblasti se zahodí. Pouze dva <xref:System.Windows.Media.Geometry> objekty mohou být kombinovány (i když tyto dvě geometrie může být také složené geometrie).  
  
-   <xref:System.Windows.Media.GeometryGroup> Třída vytvoří sloučení <xref:System.Windows.Media.Geometry> objekty obsahuje bez kombinování jejich oblasti. Libovolný počet <xref:System.Windows.Media.Geometry> můžete přidat objekty <xref:System.Windows.Media.GeometryGroup>. Příklad, naleznete v části [vytváření kompozitních tvaru](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md).  
  
 Protože neprovádět operaci combine, pomocí <xref:System.Windows.Media.GeometryGroup> objekty poskytuje výkonnostních výhod oproti použití <xref:System.Windows.Media.CombinedGeometry> objekty nebo <xref:System.Windows.Media.Geometry.Combine%2A> metoda.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Kombinovaná geometrie  
 V předchozí části uvedených <xref:System.Windows.Media.CombinedGeometry> objektu a <xref:System.Windows.Media.Geometry.Combine%2A> metoda kombinovat oblasti určené geometrie obsahují. <xref:System.Windows.Media.GeometryCombineMode> Výčet Určuje, jak se geometrie zkombinují. Možné hodnoty <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> jsou: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>, a <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je definován s režimem zkombinujte unie.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejné radius, ale s posunem centrech 50.  
  
 [!code-xaml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Výsledky sjednocení kombinování režimu](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je definován s kombinační režim <xref:System.Windows.Media.GeometryCombineMode.Xor>.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kroužky stejné radius, ale s posunem centrech 50.  
  
 [!code-xaml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Výsledky Xor kombinování režimu](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Další příklady najdete v tématu [vytváření kompozitních tvaru](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md) a [vytvořit objekt kombinaci Geometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Zmrazitelné funkce  
 Protože dědí z <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Geometry> třídy poskytují několik speciální funkce: <xref:System.Windows.Media.Geometry> objekty lze deklarovat jako [XAML prostředky](../../../../docs/framework/wpf/advanced/xaml-resources.md), sdílené mezi více objektů, jen pro čtení ke zlepšení výkon, klonovat a provedené bezpečné pro přístup z více vláken. Další informace o různých funkcí poskytovaných <xref:System.Windows.Freezable> objekty, najdete [zmrazitelné objekty – přehled](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Další funkce geometrie  
 <xref:System.Windows.Media.Geometry> Třída rovněž poskytuje užitečné pomocné metody, jako jsou následující:  
  
-   <xref:System.Windows.Media.Geometry.GetArea%2A> -Získá oblasti <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.FillContains%2A> -Určuje, zda geometrie obsahuje jiné <xref:System.Windows.Media.Geometry>.  
  
-   <xref:System.Windows.Media.Geometry.StrokeContains%2A> -Určuje, zda tah <xref:System.Windows.Media.Geometry> obsahuje zadaný bod.  
  
 Najdete v článku <xref:System.Windows.Media.Geometry> třídu pro úplný seznam všech její metody.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Geometry>  
 <xref:System.Windows.Media.PathGeometry>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Syntaxe značek cesty](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/geometries-how-to-topics.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)
