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
ms.openlocfilehash: f45c13e1af9bc2d1f75da11b13a2c03936b136c1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73455019"
---
# <a name="geometry-overview"></a>Přehled geometrie
Tento přehled popisuje, jak použít třídy [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> k popisu tvarů. Toto téma také rozlišuje rozdíly mezi objekty <xref:System.Windows.Media.Geometry> a <xref:System.Windows.Shapes.Shape> prvky.  

<a name="wcpsdk_graphics_geometry_introduction"></a>   
## <a name="what-is-a-geometry"></a>Co je geometrie?  
 Třída <xref:System.Windows.Media.Geometry> a třídy, které jsou z něj odvozeny, například <xref:System.Windows.Media.EllipseGeometry>, <xref:System.Windows.Media.PathGeometry>a <xref:System.Windows.Media.CombinedGeometry>, umožňují popsat geometrii dvojrozměrného obrazce. Tyto geometrické popisy mají mnoho použití, například definování tvaru pro malování na obrazovku nebo definování oblastí pro test volání a oříznutí. Můžete dokonce použít geometrii k definování cesty animace.  
  
 objekty <xref:System.Windows.Media.Geometry> mohou být jednoduché, například obdélníky a kružnice nebo složené, vytvořené ze dvou nebo více objektů geometrie.  Složitější geometrií lze vytvořit pomocí tříd <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry>, které umožňují popsat elipsy a křivky.  
  
 Vzhledem k tomu, že <xref:System.Windows.Media.Geometry> je typ <xref:System.Windows.Freezable>, <xref:System.Windows.Media.Geometry> objektů poskytují několik speciálních funkcí: mohou být deklarovány jako [prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdíleny mezi více objekty, které jsou určeny jen pro čtení, aby bylo možné zvýšit výkon, klonovat a vytvořit zabezpečený přístup z více vláken. Další informace o různých funkcích poskytovaných <xref:System.Windows.Freezable> objekty najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>   
## <a name="geometries-vs-shapes"></a>Geometrií vs. Shapes  
 Třídy <xref:System.Windows.Media.Geometry> a <xref:System.Windows.Shapes.Shape> vypadají podobně jako v tom, že oba popisují 2D obrazce (například porovnávají <xref:System.Windows.Media.EllipseGeometry> a <xref:System.Windows.Shapes.Ellipse>), ale existují důležité rozdíly.  
  
 Pro jednu třídu <xref:System.Windows.Media.Geometry> dědí z <xref:System.Windows.Freezable> třídy, zatímco třída <xref:System.Windows.Shapes.Shape> dědí od <xref:System.Windows.FrameworkElement>. Vzhledem k tomu, že se jedná o prvky, <xref:System.Windows.Shapes.Shape> objekty mohou sám sebe vykreslit a zúčastnit se v systému rozložení, zatímco objekty <xref:System.Windows.Media.Geometry> nemohou.  
  
 I když <xref:System.Windows.Shapes.Shape> objekty jsou snadněji použitelné než objekty <xref:System.Windows.Media.Geometry>, <xref:System.Windows.Media.Geometry> objekty jsou všestrannější. I když se k vykreslování 2D grafiky používá objekt <xref:System.Windows.Shapes.Shape>, je možné použít <xref:System.Windows.Media.Geometry> objekt k definování geometrické oblasti 2D grafiky, definování oblasti pro oříznutí nebo definování oblasti pro testování přístupů, například.  
  
### <a name="the-path-shape"></a>Obrazec cesty  
 Jedna <xref:System.Windows.Shapes.Shape>, třída <xref:System.Windows.Shapes.Path>, ve skutečnosti používá <xref:System.Windows.Media.Geometry> k popisu jejího obsahu. Nastavením vlastnosti <xref:System.Windows.Shapes.Path.Data%2A> <xref:System.Windows.Shapes.Path> pomocí <xref:System.Windows.Media.Geometry> a nastavením vlastností <xref:System.Windows.Shapes.Shape.Fill%2A> a <xref:System.Windows.Shapes.Shape.Stroke%2A> můžete vykreslit <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>   
## <a name="common-properties-that-take-a-geometry"></a>Společné vlastnosti, které berou geometrii  
 Výše uvedené části uvádí, že objekty geometrie lze použít s jinými objekty pro celou řadu účelů, například kreslení tvarů, animování a oříznutí. V následující tabulce jsou uvedeny různé třídy, které mají vlastnosti, které přijímají objekt <xref:System.Windows.Media.Geometry>.  
  
|Typ|Vlastnost|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>   
## <a name="simple-geometry-types"></a>Jednoduché typy geometrie  
 Základní třída pro všechny geometrií je abstraktní třída <xref:System.Windows.Media.Geometry>.  Třídy, které jsou odvozeny od <xref:System.Windows.Media.Geometry> třídy, mohou být zhruba seskupeny do tří kategorií: jednoduché geometrií, cesta geometrií a složený geometrií.  
  
 Jednoduché třídy geometrie zahrnují <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>a <xref:System.Windows.Media.EllipseGeometry> a slouží k vytváření základních geometrických tvarů, jako jsou čáry, obdélníky a kružnice.  
  
- <xref:System.Windows.Media.LineGeometry> je definována zadáním počátečního bodu řádku a koncového bodu.  
  
- <xref:System.Windows.Media.RectangleGeometry> je definována se strukturou <xref:System.Windows.Rect>, která určuje jeho relativní pozici a výšku a šířku. Zaoblený obdélník můžete vytvořit nastavením vlastností <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> a <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A>.  
  
- <xref:System.Windows.Media.EllipseGeometry> definuje středový bod, x-RADIUS a y-RADIUS.  Následující příklady ukazují, jak vytvořit jednoduchý geometrií pro vykreslování a pro oříznutí.  
  
 Tyto stejné tvary i složitější tvary lze vytvořit pomocí <xref:System.Windows.Media.PathGeometry> nebo kombinací objektů geometrie dohromady, ale tyto třídy poskytují jednodušší způsob, jak tyto základní geometrické tvary vyrobit.  
  
 Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.LineGeometry>.  Jak bylo uvedeno dříve, objekt <xref:System.Windows.Media.Geometry> není schopen nakreslit sám sebe, takže příklad vykreslí čáru pomocí <xref:System.Windows.Shapes.Path>ho tvaru.  Vzhledem k tomu, že řádek nemá žádnou oblast, nastavení vlastnosti <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Path> by nebylo nijak ovlivněno. místo toho jsou zadány pouze vlastnosti <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>. Následující obrázek ukazuje výstup z příkladu.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
LineGeometry vykreslený z (10, 20) do (100 130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 Další příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.EllipseGeometry>.  V příkladech se nastaví <xref:System.Windows.Media.EllipseGeometry.Center%2A> <xref:System.Windows.Media.EllipseGeometry> je nastavena na `50,50` bodu a x-RADIUS a y-RADIUS jsou nastaveny na `50`, což vytvoří kruh s průměrem 100.  Vnitřní část elipsy je vykreslena přiřazením hodnoty k vlastnosti Fill elementu PATH v tomto případě <xref:System.Windows.Media.Brushes.Gold%2A>. Následující obrázek ukazuje výstup z příkladu.  
  
 ![EllipseGeometry](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
EllipseGeometry vykreslený na (50, 50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Následující příklad ukazuje, jak vytvořit a vykreslit <xref:System.Windows.Media.RectangleGeometry>.  Pozice a rozměry obdélníku jsou definovány strukturou <xref:System.Windows.Rect>. Pozice je `50,50` a výška a šířka jsou `25`, což vytvoří čtverec. Následující obrázek ukazuje výstup z příkladu.  
  
 ![RectangleGeometry](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry vykreslený na 50, 50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Následující příklad ukazuje, jak použít <xref:System.Windows.Media.EllipseGeometry> jako oblast klipu pro obrázek.  Objekt <xref:System.Windows.Controls.Image> je definován s <xref:System.Windows.FrameworkElement.Width%2A> 200 a <xref:System.Windows.FrameworkElement.Height%2A> 150.  <xref:System.Windows.Media.EllipseGeometry> s <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> hodnotou 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> hodnotou 75 a <xref:System.Windows.Media.EllipseGeometry.Center%2A> hodnotou 100, 75 je nastavená vlastnost <xref:System.Windows.UIElement.Clip%2A> obrázku.  Zobrazí se pouze část obrázku, která je v oblasti elipsy. Následující obrázek ukazuje výstup z příkladu.  
  
 ![Obrázek s oříznutím a bez něj](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
EllipseGeometry použitý k Vystřižení ovládacího prvku obrázek  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>   
## <a name="path-geometries"></a>Geometrií cesty  
 Třída <xref:System.Windows.Media.PathGeometry> a její odlehčený ekvivalent, <xref:System.Windows.Media.StreamGeometry> třída, poskytují způsob, jak popsat více složitých číslic složených z oblouků, křivek a čar.  
  
 Na srdci <xref:System.Windows.Media.PathGeometry> je kolekce objektů <xref:System.Windows.Media.PathFigure>, takže se pojmenuje, protože každý obrázek popisuje diskrétní tvar v <xref:System.Windows.Media.PathGeometry>. Každý <xref:System.Windows.Media.PathFigure> se skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý popisuje segment obrázku.  
  
 Existuje mnoho typů segmentů.  
  
|Typ segmentu|Popis|Příklad|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Vytvoří eliptický oblouk mezi dvěma body.|[Vytvořte eliptický oblouk](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Vytvoří Bézierovu křivku krychle mezi dvěma body.|[Vytvoří bézierovu křivku krychle](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Vytvoří čáru mezi dvěma body.|[Vytvoření LineSegment v PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Vytvoří řadu krychlových Bézierových křivek.|Podívejte se na stránku typ <xref:System.Windows.Media.PolyBezierSegment>.|  
|<xref:System.Windows.Media.PolyLineSegment>|Vytvoří řadu řádků.|Podívejte se na stránku typ <xref:System.Windows.Media.PolyLineSegment>.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Vytvoří řadu kvadratických Bézierových křivek.|Podívejte se na stránku <xref:System.Windows.Media.PolyQuadraticBezierSegment>.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Vytvoří kvadratickou Bézierovu křivku.|[Vytvoření kvadratické Bézierovy křivky](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmenty v rámci <xref:System.Windows.Media.PathFigure> jsou zkombinovány do jednoho geometrického tvaru s koncovým bodem každého segmentu, který je počátečním bodem dalšího segmentu. Vlastnost <xref:System.Windows.Media.PathFigure.StartPoint%2A> <xref:System.Windows.Media.PathFigure> určuje bod, ze kterého je vykreslen první segment. Každý další segment začíná na koncovém bodu předchozího segmentu. Například svislou čáru z `10,50` do `10,150` lze definovat nastavením vlastnosti <xref:System.Windows.Media.PathFigure.StartPoint%2A> na `10,50` a vytvořením <xref:System.Windows.Media.LineSegment> s nastavením vlastnosti <xref:System.Windows.Media.LineSegment.Point%2A> `10,150`.  
  
 Následující příklad vytvoří jednoduchý <xref:System.Windows.Media.PathGeometry> skládající se z jednoho <xref:System.Windows.Media.PathFigure> pomocí <xref:System.Windows.Media.LineSegment> a zobrazí jej pomocí elementu <xref:System.Windows.Shapes.Path>. <xref:System.Windows.Media.PathFigure.StartPoint%2A> <xref:System.Windows.Media.PathFigure> objektu je nastavena na hodnotu `10,20` a <xref:System.Windows.Media.LineSegment> je definován s koncovým bodem `100,130`. Následující ilustrace znázorňuje <xref:System.Windows.Media.PathGeometry> vytvořeným tímto příkladem.  
  
 ![LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
PathGeometry, který obsahuje jeden LineSegment  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 V tomto příkladu se jako předchozí <xref:System.Windows.Media.LineGeometry> příklad poliší.  Syntaxe použitá pro <xref:System.Windows.Media.PathGeometry> je mnohem přesnější, než se používá pro jednoduché <xref:System.Windows.Media.LineGeometry>a v tomto případě může být vhodnější použít třídu <xref:System.Windows.Media.LineGeometry> v tomto případě, ale podrobná syntaxe <xref:System.Windows.Media.PathGeometry> umožňuje extrémně komplikované a složité geometrické oblasti.  
  
 Složitější geometrií lze vytvořit pomocí kombinace objektů <xref:System.Windows.Media.PathSegment>.  
  
 Následující příklad používá <xref:System.Windows.Media.BezierSegment>, <xref:System.Windows.Media.LineSegment>a <xref:System.Windows.Media.ArcSegment> k vytvoření tvaru. Příklad nejprve vytvoří Bézierovu křivku krychle, která definuje čtyři body: počáteční bod, což je koncový bod předchozího segmentu, koncový bod (<xref:System.Windows.Media.BezierSegment.Point3%2A>) a dva řídicí body (<xref:System.Windows.Media.BezierSegment.Point1%2A> a <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Dva řídicí body krychlové Bézierovy křivky se chovají jako magnetická a využívají podíly, které by jinak představovaly rovnou přímku směrem k samotnému a vytvářejí křivku. První řídicí bod, <xref:System.Windows.Media.BezierSegment.Point1%2A>, má vliv na počáteční část křivky; Druhý řídicí bod, <xref:System.Windows.Media.BezierSegment.Point2%2A>, ovlivňuje koncovou část křivky.  
  
 Příklad následně přidá <xref:System.Windows.Media.LineSegment>, který je vykreslen mezi koncovým bodem předchozí <xref:System.Windows.Media.BezierSegment>, který předchází bodu určenému vlastností <xref:System.Windows.Media.LineSegment>.  
  
 Příklad následně přidá <xref:System.Windows.Media.ArcSegment>, která je vykreslena z koncového bodu předchozí <xref:System.Windows.Media.LineSegment> do bodu určeného vlastností <xref:System.Windows.Media.ArcSegment.Point%2A>. Příklad také určuje, že oblouk je x-a y-RADIUS (<xref:System.Windows.Media.ArcSegment.Size%2A>), úhel otočení (<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>), příznak označující, jak velký úhel výsledného oblouku má být (<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>), a hodnotu, která označuje směr vykreslování oblouku (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Následující ilustrace znázorňuje tvar vytvořený tímto příkladem.  
  
 ![PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Ještě složitější geometrií lze vytvořit pomocí více objektů <xref:System.Windows.Media.PathFigure> v rámci <xref:System.Windows.Media.PathGeometry>.  
  
 Následující příklad vytvoří <xref:System.Windows.Media.PathGeometry> se dvěma objekty <xref:System.Windows.Media.PathFigure>, z nichž každý obsahuje více objektů <xref:System.Windows.Media.PathSegment>.  Použijí se <xref:System.Windows.Media.PathFigure> z výše uvedeného příkladu a <xref:System.Windows.Media.PathFigure> s <xref:System.Windows.Media.PolyLineSegment> a <xref:System.Windows.Media.QuadraticBezierSegment>.  <xref:System.Windows.Media.PolyLineSegment> je definována pole bodů a <xref:System.Windows.Media.QuadraticBezierSegment> je definováno řídicím bodem a koncovým bodem. Následující ilustrace znázorňuje tvar vytvořený tímto příkladem.  
  
 ![PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry s více číslicemi  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Podobně jako třída <xref:System.Windows.Media.PathGeometry>, <xref:System.Windows.Media.StreamGeometry> definuje složitý geometrický tvar, který může obsahovat křivky, elipsy a čáry. Na rozdíl od <xref:System.Windows.Media.PathGeometry>obsah <xref:System.Windows.Media.StreamGeometry> nepodporuje datové vazby, animace ani úpravy. Použijte <xref:System.Windows.Media.StreamGeometry>, pokud potřebujete popsat složitou geometrii, ale nechcete, aby režie podporovala datové vazby, animace nebo úpravy. Z důvodu jeho efektivity je třída <xref:System.Windows.Media.StreamGeometry> vhodnou volbou pro popisování doplňků.  
  
 Příklad najdete v tématu [Vytvoření obrazce pomocí StreamGeometry](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Syntaxe značek cesty  
 Typy <xref:System.Windows.Media.PathGeometry> a <xref:System.Windows.Media.StreamGeometry> podporují syntaxi atributu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] pomocí speciální řady příkazů Move a Draw. Další informace najdete v tématu [syntaxe označení cest](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>   
## <a name="composite-geometries"></a>Složené geometrií  
 Složené objekty geometrie lze vytvořit pomocí <xref:System.Windows.Media.GeometryGroup>, <xref:System.Windows.Media.CombinedGeometry>nebo voláním metody static <xref:System.Windows.Media.Geometry> <xref:System.Windows.Media.Geometry.Combine%2A>.  
  
- Objekt <xref:System.Windows.Media.CombinedGeometry> a metoda <xref:System.Windows.Media.Geometry.Combine%2A> provádí logickou operaci pro kombinování oblasti definované dvěma geometrií. <xref:System.Windows.Media.Geometry> objekty, které nemají žádnou oblast, jsou zahozeny. Kombinovat lze pouze dva <xref:System.Windows.Media.Geometry> objekty (i když tyto dva geometrií mohou být také složené geometrií).  
  
- Třída <xref:System.Windows.Media.GeometryGroup> vytvoří Amalgamation objektů <xref:System.Windows.Media.Geometry>, které obsahuje, bez kombinace jejich oblasti. Do <xref:System.Windows.Media.GeometryGroup>lze přidat libovolný počet objektů <xref:System.Windows.Media.Geometry>. Příklad najdete v tématu [Vytvoření složeného tvaru](how-to-create-a-composite-shape.md).  
  
 Vzhledem k tomu, že neprovede operaci kombinování, použití <xref:System.Windows.Media.GeometryGroup> objektů poskytuje výhody výkonu při použití objektů <xref:System.Windows.Media.CombinedGeometry> nebo <xref:System.Windows.Media.Geometry.Combine%2A> metody.  
  
<a name="combindgeometriessection"></a>   
## <a name="combined-geometries"></a>Kombinované geometrií  
 Předchozí část zmíněná <xref:System.Windows.Media.CombinedGeometry> objekt a metoda <xref:System.Windows.Media.Geometry.Combine%2A> kombinuje oblast definovanou geometrií, kterou obsahují. Výčet <xref:System.Windows.Media.GeometryCombineMode> určuje, jak jsou geometrií kombinovány. Možné hodnoty pro vlastnost <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> jsou: <xref:System.Windows.Media.GeometryCombineMode.Union>, <xref:System.Windows.Media.GeometryCombineMode.Intersect>, <xref:System.Windows.Media.GeometryCombineMode.Exclude>a <xref:System.Windows.Media.GeometryCombineMode.Xor>.  
  
 V následujícím příkladu je <xref:System.Windows.Media.CombinedGeometry> definováno pomocí kombinovaného režimu sjednocení.  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kružnice stejného poloměru, ale posunou Center o 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Výsledky režimu kombinování sjednocení](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 V následujícím příkladu je <xref:System.Windows.Media.CombinedGeometry> definován s režimem kombinované <xref:System.Windows.Media.GeometryCombineMode.Xor>.  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> i <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kružnice stejného poloměru, ale posunou Center o 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Výsledky kombinovaného režimu XOR](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Další příklady najdete v tématu [Vytvoření složeného tvaru](how-to-create-a-composite-shape.md) a [Vytvoření kombinované geometrie](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>   
## <a name="freezable-features"></a>Funkce Freezable  
 Vzhledem k tomu, že dědí z třídy <xref:System.Windows.Freezable>, poskytuje <xref:System.Windows.Media.Geometry> třídy několik speciálních funkcí: objekty <xref:System.Windows.Media.Geometry> mohou být deklarovány jako [prostředky XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdílené mezi více objekty, které jsou určeny jen pro čtení pro zlepšení výkonu, klonování a provedení. bezpečné pro přístup z více vláken. Další informace o různých funkcích poskytovaných <xref:System.Windows.Freezable> objekty najdete v tématu [Přehled objektů Freezable](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>   
## <a name="other-geometry-features"></a>Další funkce geometrie  
 Třída <xref:System.Windows.Media.Geometry> také poskytuje užitečné pomocné metody, například následující:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A> – získá oblast <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A> – určuje, zda geometrie obsahuje jiný <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A> – určuje, zda tah <xref:System.Windows.Media.Geometry> obsahuje zadaný bod.  
  
 Úplný seznam jeho metod naleznete v tématu <xref:System.Windows.Media.Geometry> třídy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Syntaxe značek cesty](path-markup-syntax.md)
- [Témata s postupy](geometries-how-to-topics.md)
- [Přehled animace](animation-overview.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled nakreslených objektů](drawing-objects-overview.md)
