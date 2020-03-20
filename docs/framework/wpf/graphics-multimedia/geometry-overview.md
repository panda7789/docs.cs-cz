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
ms.openlocfilehash: 1329f26e588b90fcd25052fb805058915b8825e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186477"
---
# <a name="geometry-overview"></a>Přehled geometrie
Tento přehled popisuje, jak [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Media.Geometry> používat třídy k popisu obrazců. Toto téma také kontrastuje <xref:System.Windows.Media.Geometry> rozdíly <xref:System.Windows.Shapes.Shape> mezi objekty a prvky.  

<a name="wcpsdk_graphics_geometry_introduction"></a>
## <a name="what-is-a-geometry"></a>Co je geometrie?  
 Třída <xref:System.Windows.Media.Geometry> a třídy, které z <xref:System.Windows.Media.EllipseGeometry>ní <xref:System.Windows.Media.PathGeometry>jsou <xref:System.Windows.Media.CombinedGeometry>odvozeny, například , , a , umožňují popsat geometrii obrazce 2D. Tyto geometrické popisy mají mnoho použití, jako je definování tvaru malovat na obrazovku nebo definování hit-test a klip oblastí. K definování cesty animace můžete dokonce použít geometrii.  
  
 <xref:System.Windows.Media.Geometry>objekty mohou být jednoduché, například obdélníky a kružnice nebo složené, vytvořené ze dvou nebo více objektů geometrie.  Složitější geometrie lze vytvořit <xref:System.Windows.Media.PathGeometry> pomocí <xref:System.Windows.Media.StreamGeometry> tříd a, které umožňují popsat oblouky a křivky.  
  
 Vzhledem <xref:System.Windows.Media.Geometry> k <xref:System.Windows.Freezable>tomu, <xref:System.Windows.Media.Geometry> že a je typ , objekty poskytují několik speciálních funkcí: mohou být deklarovány jako [prostředky](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdílené mezi více objektů, jen pro čtení ke zlepšení výkonu, klonované a z více vláken bezpečné. Další informace o různých funkcích <xref:System.Windows.Freezable> poskytovaných objekty naleznete v tématu [Přehled mrazivých objektů](../advanced/freezable-objects-overview.md).  
  
<a name="wcpsdk_graphics_geometry_geometryandshapes"></a>
## <a name="geometries-vs-shapes"></a>Geometrie vs. tvary  
 A <xref:System.Windows.Media.Geometry> <xref:System.Windows.Shapes.Shape> třídy se zdají podobné v tom, <xref:System.Windows.Media.EllipseGeometry> že <xref:System.Windows.Shapes.Ellipse> oba popisují 2D tvary (porovnat a například), ale existují důležité rozdíly.  
  
 Pro jednoho <xref:System.Windows.Media.Geometry> třídy dědí <xref:System.Windows.Freezable> z <xref:System.Windows.Shapes.Shape> třídy, <xref:System.Windows.FrameworkElement>zatímco třída dědí z . Vzhledem k <xref:System.Windows.Shapes.Shape> tomu, že se jedná o prvky, mohou objekty vykreslit samy sebe a účastnit se systému rozložení, zatímco <xref:System.Windows.Media.Geometry> objekty nemohou.  
  
 Přestože <xref:System.Windows.Shapes.Shape> jsou objekty snadněji <xref:System.Windows.Media.Geometry> použitelné <xref:System.Windows.Media.Geometry> než objekty, objekty jsou univerzálnější. Zatímco <xref:System.Windows.Shapes.Shape> objekt se používá k vykreslení <xref:System.Windows.Media.Geometry> 2D grafiky, objekt lze použít k definování geometrické oblasti pro 2D grafiku, definování oblasti pro oříznutí nebo definování oblasti pro testování přístupů, například.  
  
### <a name="the-path-shape"></a>Obrazec Cesta  
 Jeden <xref:System.Windows.Shapes.Shape>, <xref:System.Windows.Shapes.Path> třída, ve <xref:System.Windows.Media.Geometry> skutečnosti používá k popisu jeho obsah. Nastavením <xref:System.Windows.Shapes.Path.Data%2A> vlastnosti <xref:System.Windows.Shapes.Path> s <xref:System.Windows.Media.Geometry> a a <xref:System.Windows.Shapes.Shape.Fill%2A> <xref:System.Windows.Shapes.Shape.Stroke%2A> nastavením a vlastností můžete vykreslit <xref:System.Windows.Media.Geometry>.  
  
<a name="commonproperties"></a>
## <a name="common-properties-that-take-a-geometry"></a>Společné vlastnosti, které berou geometrii  
 Předchozí části uvedené, že geometrie objekty lze použít s jinými objekty pro různé účely, jako je například kreslení tvarů, animace a oříznutí. V následující tabulce je uvedeno několik <xref:System.Windows.Media.Geometry> tříd, které mají vlastnosti, které přebírají objekt.  
  
|Typ|Vlastnost|  
|----------|--------------|  
|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath.PathGeometry%2A>|  
|<xref:System.Windows.Media.DrawingGroup>|<xref:System.Windows.Media.DrawingGroup.ClipGeometry%2A>|  
|<xref:System.Windows.Media.GeometryDrawing>|<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>|  
|<xref:System.Windows.Shapes.Path>|<xref:System.Windows.Shapes.Path.Data%2A>|  
|<xref:System.Windows.UIElement>|<xref:System.Windows.UIElement.Clip%2A>|  
  
<a name="wcpsdk_graphics_geometry_geometrytypes"></a>
## <a name="simple-geometry-types"></a>Jednoduché typy geometrie  
 Základní třída pro všechny geometrie <xref:System.Windows.Media.Geometry>je abstraktní třída .  Třídy, které <xref:System.Windows.Media.Geometry> jsou odvozeny z třídy, lze zhruba rozdělit do tří kategorií: jednoduché geometrie, geometrie cesty a složené geometrie.  
  
 Jednoduché třídy <xref:System.Windows.Media.LineGeometry>geometrie zahrnují , <xref:System.Windows.Media.RectangleGeometry>, a <xref:System.Windows.Media.EllipseGeometry> a používají se k vytvoření základních geometrických tvarů, jako jsou čáry, obdélníky a kružnice.  
  
- A <xref:System.Windows.Media.LineGeometry> je definována zadáním počátečního bodu čáry a koncového bodu.  
  
- A <xref:System.Windows.Media.RectangleGeometry> je definována se strukturou, <xref:System.Windows.Rect> která určuje její relativní polohu a výšku a šířku. Zaoblený obdélník můžete <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> vytvořit <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> nastavením vlastností a.  
  
- A <xref:System.Windows.Media.EllipseGeometry> je definován středovým bodem, poloměrem x a poloměrem y.  Následující příklady ukazují, jak vytvořit jednoduché geometrie pro vykreslování a ořezy.  
  
 Tyto stejné tvary, stejně jako složitější tvary, mohou být vytvořeny pomocí <xref:System.Windows.Media.PathGeometry> nebo kombinací objektů geometrie dohromady, ale tyto třídy poskytují jednodušší prostředky pro výrobu těchto základních geometrických tvarů.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.LineGeometry>a vykreslit .  Jak již bylo <xref:System.Windows.Media.Geometry> uvedeno dříve, objekt není schopen <xref:System.Windows.Shapes.Path> kreslit sám, takže příklad používá obrazec k vykreslení čáry.  Vzhledem k tomu, že <xref:System.Windows.Shapes.Shape.Fill%2A> řádek <xref:System.Windows.Shapes.Path> nemá žádnou oblast, nastavení vlastnosti by nemělo žádný vliv; místo toho <xref:System.Windows.Shapes.Shape.Stroke%2A> jsou <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> zadány pouze vlastnosti a. Následující obrázek znázorňuje výstup z příkladu.  
  
 ![A LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
A LineGeometry byly od (10,20) do (100 130)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.EllipseGeometry>a vykreslit .  Příklady nastaví <xref:System.Windows.Media.EllipseGeometry.Center%2A> <xref:System.Windows.Media.EllipseGeometry> je nastavena na `50,50` bod a x-poloměr a y-poloměr `50`jsou nastaveny na , který vytvoří kružnice o průměru 100.  Vnitřek elipsy je vybarvený přiřazením hodnoty vlastnosti Fill elementu Path, v tomto případě <xref:System.Windows.Media.Brushes.Gold%2A>. Následující obrázek znázorňuje výstup z příkladu.  
  
 ![Geometrie ellipse](./media/graphicsmm-ellipse.gif "graphicsmm_ellipse")  
Geometrie EllipseGeometry nakreslená na (50,50)  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmellipsegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmellipsegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMEllipseGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmellipsegeometryexample)]  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.RectangleGeometry>a vykreslit .  Pozice a rozměry obdélníku jsou definovány strukturou. <xref:System.Windows.Rect> Poloha je `50,50` a výška a `25`šířka jsou obě , což vytváří čtverec. Následující obrázek znázorňuje výstup z příkladu.  
  
 ![Geometrie Rectangle](./media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
Geometrie Rectanglegeometry nakreslena na 50,50  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.EllipseGeometry> použít oblast klipu jako oblast klipu pro obrázek.  Objekt <xref:System.Windows.Controls.Image> je definován <xref:System.Windows.FrameworkElement.Width%2A> s a 200 a a <xref:System.Windows.FrameworkElement.Height%2A> 150.  S <xref:System.Windows.Media.EllipseGeometry> hodnotou <xref:System.Windows.Media.EllipseGeometry.RadiusX%2A> 100, <xref:System.Windows.Media.EllipseGeometry.RadiusY%2A> hodnota 75 a <xref:System.Windows.Media.EllipseGeometry.Center%2A> hodnota 100,75 je nastavena na <xref:System.Windows.UIElement.Clip%2A> vlastnost obrázku.  Zobrazí se pouze část obrazu, která se nachází v oblasti elipsy. Následující obrázek znázorňuje výstup z příkladu.  
  
 ![Obrázek s oříznutím a bez něj](./media/graphicsmm-clipexample.png "graphicsmm_clipexample")  
EllipseGeometry slouží k oříznutí image ovládacího prvku  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmimageclipgeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmimageclipgeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMImageClipGeometryExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmimageclipgeometryexample)]  
  
<a name="wcpsdk_graphics_geometry_pathgeometry"></a>
## <a name="path-geometries"></a>Geometrie cesty  
 Třída <xref:System.Windows.Media.PathGeometry> a její lehký <xref:System.Windows.Media.StreamGeometry> ekvivalent, třída, poskytují prostředky k popisu více složitých obrázků složených z oblouků, křivek a čar.  
  
 V srdci <xref:System.Windows.Media.PathGeometry> je kolekce <xref:System.Windows.Media.PathFigure> objektů, tak pojmenovaný, protože každá postava popisuje samostatný <xref:System.Windows.Media.PathGeometry>tvar v . Každý <xref:System.Windows.Media.PathFigure> z nich se skládá <xref:System.Windows.Media.PathSegment> z jednoho nebo více objektů, z nichž každý popisuje segment obrázku.  
  
 Existuje mnoho typů segmentů.  
  
|Typ segmentu|Popis|Příklad|  
|------------------|-----------------|-------------|  
|<xref:System.Windows.Media.ArcSegment>|Vytvoří eliptický oblouk mezi dvěma body.|[Vytvořte eliptický oblouk](how-to-create-an-elliptical-arc.md).|  
|<xref:System.Windows.Media.BezierSegment>|Vytvoří kubickou Bezierovu křivku mezi dvěma body.|[Vytvořte kubickou bezierovou křivku](how-to-create-a-cubic-bezier-curve.md).|  
|<xref:System.Windows.Media.LineSegment>|Vytvoří čáru mezi dvěma body.|[Vytvoření LineSegment v PathGeometry](how-to-create-a-linesegment-in-a-pathgeometry.md)|  
|<xref:System.Windows.Media.PolyBezierSegment>|Vytvoří řadu kubických Bezierových křivek.|Podívejte <xref:System.Windows.Media.PolyBezierSegment> se na stránku typu.|  
|<xref:System.Windows.Media.PolyLineSegment>|Vytvoří řadu řádků.|Podívejte <xref:System.Windows.Media.PolyLineSegment> se na stránku typu.|  
|<xref:System.Windows.Media.PolyQuadraticBezierSegment>|Vytvoří řadu kvadratické Bezierovy křivky.|Podívejte <xref:System.Windows.Media.PolyQuadraticBezierSegment> se na stránku.|  
|<xref:System.Windows.Media.QuadraticBezierSegment>|Vytvoří kvadratickou Bezierovu křivku.|[Vytvořte kvadratickou Bezierovu křivku](how-to-create-a-quadratic-bezier-curve.md).|  
  
 Segmenty v <xref:System.Windows.Media.PathFigure> rámci a jsou sloučeny do jednoho geometrického tvaru, přičemž koncový bod každého segmentu je počátečním bodem dalšího segmentu. Vlastnost <xref:System.Windows.Media.PathFigure.StartPoint%2A> <xref:System.Windows.Media.PathFigure> určuje bod, ze kterého je vykreslen první segment. Každý následující segment začíná v koncovém bodě předchozího segmentu. Například svislou `10,50` `10,150` čáru od do <xref:System.Windows.Media.PathFigure.StartPoint%2A> lze `10,50` definovat nastavením <xref:System.Windows.Media.LineSegment.Point%2A> vlastnosti `10,150`a vytvořením <xref:System.Windows.Media.LineSegment> s nastavením vlastnosti .  
  
 Následující příklad vytvoří <xref:System.Windows.Media.PathGeometry> jednoduchý skládá z <xref:System.Windows.Media.PathFigure> jednoho <xref:System.Windows.Media.LineSegment> s a <xref:System.Windows.Shapes.Path> zobrazí jej pomocí prvku. Objekt <xref:System.Windows.Media.PathFigure> <xref:System.Windows.Media.PathFigure.StartPoint%2A> je nastaven na `10,20` a <xref:System.Windows.Media.LineSegment> je definován s `100,130`koncovým bodem . Následující obrázek <xref:System.Windows.Media.PathGeometry> znázorňuje vytvořený tímto příkladem.  
  
 ![A LineGeometry](./media/graphicsmm-line.gif "graphicsmm_line")  
PathGeometry, který obsahuje jeden Segment čáry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrylineexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrylineexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryLineExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrylineexample)]  
  
 Stojí za to pokoně <xref:System.Windows.Media.LineGeometry> porovnal tento příklad s předchozím příkladem.  Syntaxe použitá <xref:System.Windows.Media.PathGeometry> pro a je mnohem podrobnější než <xref:System.Windows.Media.LineGeometry>syntaxe použitá pro jednoduché <xref:System.Windows.Media.LineGeometry> a může mít větší smysl použít <xref:System.Windows.Media.PathGeometry> třídu v tomto případě, ale podrobná syntaxe umožňuje extrémně složité a složité geometrické oblasti.  
  
 Složitější geometrie lze vytvořit pomocí <xref:System.Windows.Media.PathSegment> kombinace objektů.  
  
 Další příklad používá <xref:System.Windows.Media.BezierSegment>obrazec , a <xref:System.Windows.Media.LineSegment>a a. <xref:System.Windows.Media.ArcSegment> Příklad nejprve vytvoří kubickou Bezierovu křivku definováním čtyř bodů: počátečního bodu, což je<xref:System.Windows.Media.BezierSegment.Point3%2A>koncový bod předchozího segmentu, koncový bod ( ) a dva řídicí body (<xref:System.Windows.Media.BezierSegment.Point1%2A> a <xref:System.Windows.Media.BezierSegment.Point2%2A>).  Dva řídicí body kubické Bezierovy křivky se chovají jako magnety a přitahují části toho, co by jinak bylo přímkou směrem k sobě, což vytváří křivku. První řídicí bod <xref:System.Windows.Media.BezierSegment.Point1%2A>, ovlivňuje počáteční část křivky; druhý řídicí bod <xref:System.Windows.Media.BezierSegment.Point2%2A>, ovlivňuje koncovou část křivky.  
  
 Příklad pak přidá <xref:System.Windows.Media.LineSegment>, který je nakreslena mezi <xref:System.Windows.Media.BezierSegment> koncový bod předcházející, <xref:System.Windows.Media.LineSegment> které mu předcházely do bodu určeného jeho vlastnost.  
  
 Příklad pak přidá <xref:System.Windows.Media.ArcSegment>, který je nakreslena z <xref:System.Windows.Media.LineSegment> koncového bodu <xref:System.Windows.Media.ArcSegment.Point%2A> předcházející do bodu určeného jeho vlastnost. Příklad také určuje poloměr x a y oblouku<xref:System.Windows.Media.ArcSegment.Size%2A>( ),<xref:System.Windows.Media.ArcSegment.RotationAngle%2A>úhel natočení ( ), příznak označující, jak<xref:System.Windows.Media.ArcSegment.IsLargeArc%2A>velký by měl být úhel výsledného oblouku ( ) a hodnotu označující, ve kterém směru je oblouk nakreslen (<xref:System.Windows.Media.ArcSegment.SweepDirection%2A>). Následující obrázek znázorňuje obrazec vytvořený v tomto příkladu.  
  
 ![A PathGeometry](./media/graphicsmm-path2.gif "graphicsmm_path2")  
A PathGeometry  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexexample)]  
  
 Ještě složitější geometrie lze vytvořit <xref:System.Windows.Media.PathFigure> pomocí <xref:System.Windows.Media.PathGeometry>více objektů v rámci .  
  
 Následující příklad vytvoří <xref:System.Windows.Media.PathGeometry> se <xref:System.Windows.Media.PathFigure> dvěma objekty, <xref:System.Windows.Media.PathSegment> z nichž každý obsahuje více objektů.  Z <xref:System.Windows.Media.PathFigure> výše uvedeného <xref:System.Windows.Media.PathFigure> příkladu <xref:System.Windows.Media.PolyLineSegment> a <xref:System.Windows.Media.QuadraticBezierSegment> s a a a se používají.  A <xref:System.Windows.Media.PolyLineSegment> je definována s pole <xref:System.Windows.Media.QuadraticBezierSegment> body a je definována s řídicím bodem a koncovým bodem. Následující obrázek znázorňuje obrazec vytvořený v tomto příkladu.  
  
 ![A PathGeometry](./media/graphicsmm-path.gif "graphicsmm_path")  
PathGeometry s více čísly  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmpathgeometrycomplexmultiexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmpathgeometrycomplexmultiexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMPathGeometryComplexMultiExample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmpathgeometrycomplexmultiexample)]  
  
### <a name="streamgeometry"></a>StreamGeometry  
 Podobně <xref:System.Windows.Media.PathGeometry> jako třída <xref:System.Windows.Media.StreamGeometry> definuje komplexní geometrický tvar, který může obsahovat křivky, oblouky a čáry. Na <xref:System.Windows.Media.PathGeometry>rozdíl od , <xref:System.Windows.Media.StreamGeometry> obsah nepodporují datové vazby, animace nebo změny. Použijte, <xref:System.Windows.Media.StreamGeometry> když potřebujete popsat složitou geometrii, ale nechcete režii podpůrné datové vazby, animace nebo úpravy. Vzhledem k jeho <xref:System.Windows.Media.StreamGeometry> účinnosti, třída je dobrou volbou pro popis adorners.  
  
 Příklad naleznete v [tématu Vytvoření obrazce pomocí StreamGeometry](how-to-create-a-shape-using-a-streamgeometry.md).  
  
### <a name="path-markup-syntax"></a>Syntaxe značek cesty  
 Typy <xref:System.Windows.Media.PathGeometry> <xref:System.Windows.Media.StreamGeometry> a podporují [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] syntaxi atributu pomocí speciální řady příkazů pro přesun a kreslení. Další informace naleznete v [tématu Syntaxe značek cesty](path-markup-syntax.md).  
  
<a name="wcpsdk_graphics_geometry_introduction2"></a>
## <a name="composite-geometries"></a>Složené geometrie  
 Objekty složené geometrie <xref:System.Windows.Media.GeometryGroup>lze <xref:System.Windows.Media.CombinedGeometry>vytvořit pomocí , <xref:System.Windows.Media.Geometry> a <xref:System.Windows.Media.Geometry.Combine%2A>nebo voláním statické metody .  
  
- Objekt <xref:System.Windows.Media.CombinedGeometry> a <xref:System.Windows.Media.Geometry.Combine%2A> metoda provádí logickou operaci kombinovat oblast definovanou dvěma geometriemi. <xref:System.Windows.Media.Geometry>objekty, které nemají žádnou oblast, jsou zahozeny. Zkombinovat <xref:System.Windows.Media.Geometry> lze pouze dva objekty (i když tyto dvě geometrie mohou být také složené geometrie).  
  
- Třída <xref:System.Windows.Media.GeometryGroup> vytvoří sloučení objektů, <xref:System.Windows.Media.Geometry> které obsahuje bez kombinování jejich oblasti. Do souboru <xref:System.Windows.Media.Geometry> <xref:System.Windows.Media.GeometryGroup>lze přidat libovolný počet objektů. Příklad najdete v [tématu Vytvoření složeného tvaru](how-to-create-a-composite-shape.md).  
  
 Vzhledem k tomu, že <xref:System.Windows.Media.GeometryGroup> neprovádějí operaci kombinovat, pomocí objektů poskytuje výhody výkonu nad pomocí <xref:System.Windows.Media.CombinedGeometry> objektů nebo <xref:System.Windows.Media.Geometry.Combine%2A> metody.  
  
<a name="combindgeometriessection"></a>
## <a name="combined-geometries"></a>Kombinované geometrie  
 Předchozí část uvedený <xref:System.Windows.Media.CombinedGeometry> objekt a <xref:System.Windows.Media.Geometry.Combine%2A> metoda kombinovat oblast definovanou geometrie, které obsahují. Výčet <xref:System.Windows.Media.GeometryCombineMode> určuje, jak jsou kombinovány geometrie. Možné hodnoty <xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> vlastnosti jsou: <xref:System.Windows.Media.GeometryCombineMode.Intersect> <xref:System.Windows.Media.GeometryCombineMode.Exclude> <xref:System.Windows.Media.GeometryCombineMode.Xor> <xref:System.Windows.Media.GeometryCombineMode.Union>, , a .  
  
 V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je a definována s kombinovaným způsobem Unie.  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kružnice se stejným poloměrem, ale se středy odsazenými 50.  
  
 [!code-xaml[GeometrySample#23](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![Výsledky kombinovaného režimu Unie](./media/mil-task-combined-geometry-union.PNG "mil_task_combined_geometry_union")  
  
 V následujícím příkladu <xref:System.Windows.Media.CombinedGeometry> je a definována <xref:System.Windows.Media.GeometryCombineMode.Xor>s kombinovaným režimem .  Obě <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> a <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> jsou definovány jako kružnice se stejným poloměrem, ale se středy odsazenými 50.  
  
 [!code-xaml[GeometrySample#24](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Výsledky kombinovaného režimu Xor](./media/mil-task-combined-geometry-xor.PNG "mil_task_combined_geometry_xor")  
  
 Další příklady naleznete [v tématu Vytvoření složeného tvaru](how-to-create-a-composite-shape.md) a Vytvoření kombinované [geometrie](how-to-create-a-combined-geometry.md).  
  
<a name="freezable_features"></a>
## <a name="freezable-features"></a>Zmrazitelné funkce  
 Vzhledem k tomu, že dědí z <xref:System.Windows.Freezable> třídy, <xref:System.Windows.Media.Geometry> třída poskytuje několik speciálních funkcí: <xref:System.Windows.Media.Geometry> objekty mohou být deklarovány jako Prostředky [XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md), sdílené mezi více objektů, jen pro čtení ke zlepšení výkonu, klonované a z přístupu k vláknu. Další informace o různých funkcích <xref:System.Windows.Freezable> poskytovaných objekty naleznete v tématu [Přehled mrazivých objektů](../advanced/freezable-objects-overview.md).  
  
<a name="othergeometryfeatures"></a>
## <a name="other-geometry-features"></a>Další prvky geometrie  
 Třída <xref:System.Windows.Media.Geometry> také poskytuje užitečné metody nástroje, například následující:  
  
- <xref:System.Windows.Media.Geometry.GetArea%2A>- Získá oblast <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.FillContains%2A>- Určuje, zda geometrie obsahuje jinou <xref:System.Windows.Media.Geometry>.  
  
- <xref:System.Windows.Media.Geometry.StrokeContains%2A>- Určuje, zda tah <xref:System.Windows.Media.Geometry> obsahuje zadaný bod.  
  
 Kompletní <xref:System.Windows.Media.Geometry> seznam jeho metod naleznete ve třídě.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Geometry>
- <xref:System.Windows.Media.PathGeometry>
- <xref:System.Windows.Shapes.Path>
- <xref:System.Windows.Media.GeometryDrawing>
- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Syntaxe značek cesty](path-markup-syntax.md)
- [Témata s postupy](geometries-how-to-topics.md)
- [Přehled animace](animation-overview.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
- [Přehled vykreslovaných objektů](drawing-objects-overview.md)
