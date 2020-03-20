---
title: Tvary a základní přehled výkresů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- shapes [WPF], about shapes
- basic drawing [WPF]
- vector drawing [WPF], overview
- vectors [WPF], drawing
- Shape objects [WPF]
ms.assetid: 66d7a6d6-e3b6-47bc-8dfe-8a1b26f7d901
ms.openlocfilehash: 44104bec478f1fbb10acc0e591af43ea95fecdc5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141325"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Tvary a základní kresby v přehledu WPF
Toto téma poskytuje přehled o <xref:System.Windows.Shapes.Shape> tom, jak kreslit s objekty. A <xref:System.Windows.Shapes.Shape> je <xref:System.Windows.UIElement> typ, který umožňuje nakreslit obrazec na obrazovku. Vzhledem k tomu, <xref:System.Windows.Shapes.Shape> že se <xref:System.Windows.Controls.Panel> jedná o prvky uživatelského rozhraní, objekty lze použít uvnitř prvky a většinu ovládacích prvků.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]nabízí několik vrstev přístupu ke grafickým a vykreslovací službám. V horní vrstvě <xref:System.Windows.Shapes.Shape> jsou objekty snadno použitelné a poskytují mnoho užitečných funkcí, jako je rozložení a účast v systému [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] událostí.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Objekty obrazce  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje řadu objektů připravených <xref:System.Windows.Shapes.Shape> k použití.  Všechny objekty obrazce dědí z <xref:System.Windows.Shapes.Shape> třídy. Mezi dostupné <xref:System.Windows.Shapes.Ellipse>objekty tvarů patří <xref:System.Windows.Shapes.Line>, , <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape>objekty sdílejí následující společné vlastnosti.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Popisuje, jak je obrys obrazce malovaný.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Popisuje tloušťku obrysu obrazce.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Popisuje, jak je vnitřek tvaru malovaný.  
  
- Vlastnosti dat pro určení souřadnic a vrcholů, měřeno v pixelech nezávislých na zařízení.  
  
 Protože jsou <xref:System.Windows.UIElement>odvozeny z , objekty tvarů lze použít uvnitř panelů a většinu ovládacích prvků. Panel <xref:System.Windows.Controls.Canvas> je obzvláště dobrou volbou pro vytváření složitých výkresů, protože podporuje absolutní umístění podřízených objektů.  
  
 Třída <xref:System.Windows.Shapes.Line> umožňuje nakreslit čáru mezi dvěma body. Následující příklad ukazuje několik způsobů, jak určit souřadnice čáry a vlastnosti tahu.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Následující obrázek znázorňuje vykreslenou <xref:System.Windows.Shapes.Line>.  
  
 ![Obrázek čáry](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 Přestože <xref:System.Windows.Shapes.Line> třída poskytuje <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost, nastavení nemá žádný <xref:System.Windows.Shapes.Line> vliv, protože nemá žádnou oblast.  
  
 Dalším běžným <xref:System.Windows.Shapes.Ellipse>tvarem je .  <xref:System.Windows.Shapes.Ellipse> Vytvořte definováním vlastností <xref:System.Windows.FrameworkElement.Width%2A> obrazce a <xref:System.Windows.FrameworkElement.Height%2A> jeho vlastností. Chcete-li nakreslit <xref:System.Windows.Shapes.Ellipse> kružnici, určete, jejichž <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> hodnoty jsou stejné.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Následující obrázek znázorňuje příklad <xref:System.Windows.Shapes.Ellipse>vykresleného obrázku .  
  
 ![Ilustrace elipsy](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Použití cest a geometrií  
 Třída <xref:System.Windows.Shapes.Path> umožňuje kreslit křivky a složité tvary. Tyto křivky a tvary <xref:System.Windows.Media.Geometry> jsou popsány pomocí objektů. Chcete-li <xref:System.Windows.Shapes.Path>použít , <xref:System.Windows.Media.Geometry> vytvořte a <xref:System.Windows.Shapes.Path> použijte jej <xref:System.Windows.Shapes.Path.Data%2A> k nastavení vlastnosti objektu.  
  
 Existuje celá řada <xref:System.Windows.Media.Geometry> objektů z čeho vybírat. <xref:System.Windows.Media.LineGeometry>Třídy <xref:System.Windows.Media.RectangleGeometry>, <xref:System.Windows.Media.EllipseGeometry> a popisují relativně jednoduché tvary. Chcete-li vytvořit složitější tvary nebo <xref:System.Windows.Media.PathGeometry>vytvořit křivky, použijte .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry a Segmenty cesty  
 <xref:System.Windows.Media.PathGeometry>objekty se skládají <xref:System.Windows.Media.PathFigure> z jednoho nebo více objektů; každý <xref:System.Windows.Media.PathFigure> představuje jiný "obrázek" nebo tvar. Každý <xref:System.Windows.Media.PathFigure> z nich se skládá <xref:System.Windows.Media.PathSegment> z jednoho nebo více objektů, z nichž každý představuje připojenou část obrázku nebo tvaru. Typy segmentů zahrnují <xref:System.Windows.Media.LineSegment> <xref:System.Windows.Media.BezierSegment>následující: <xref:System.Windows.Media.ArcSegment>, a .  
  
 V následujícím příkladu <xref:System.Windows.Shapes.Path> se a používá k nakreslení kvadratické Bezierovy křivky.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Následující obrázek znázorňuje vykreslený obrazec.  
  
 ![Ilustrace cesta](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Další informace <xref:System.Windows.Media.PathGeometry> o ostatních <xref:System.Windows.Media.Geometry> třídách naleznete v tématu [Přehled geometrie](geometry-overview.md).  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>Zkrácená syntaxe XAML  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]souboru můžete také použít speciální zkrácenou syntaxi k popisu <xref:System.Windows.Shapes.Path>. V následujícím příkladu se zkrácená syntaxe používá k nakreslení složitého tvaru.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Následující obrázek znázorňuje vykreslenou <xref:System.Windows.Shapes.Path>.  
  
 ![Ilustrace cesta](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 Řetězec <xref:System.Windows.Shapes.Path.Data%2A> atributu začíná příkazem "moveto", označeným M, který vytváří počáteční bod pro cestu <xref:System.Windows.Controls.Canvas>v souřadnicovém systému . <xref:System.Windows.Shapes.Path>parametry dat rozlišují malá a velká písmena. Velké město M označuje absolutní umístění nového aktuálního bodu. Malé písmeno m by znamenalo relativní souřadnice. První segment je kubická Bezierova křivka začínající na (100 200) a končící na (400 175), nakreslená pomocí dvou kontrolních bodů (100 25) a (400 350). Tento segment je označen příkazem <xref:System.Windows.Shapes.Path.Data%2A> C v řetězci atributu. Opět platí, že kapitál C označuje absolutní cestu; malá písmena c by naznačovala relativní cestu.  
  
 Druhý segment začíná absolutním vodorovným příkazem "lineto" H, který určuje čáru nakreslenou z koncového bodu předchozí podcesty (400 175) na nový koncový bod (280 175). Vzhledem k tomu, že se jedná o horizontální příkaz "lineto", zadaná hodnota je souřadnice *x.*  
  
 Úplnou syntaxi cesty <xref:System.Windows.Shapes.Path.Data%2A> naleznete v odkazu a [vytvoření obrazce pomocí pathgeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Obrazobrazové malby  
 <xref:System.Windows.Media.Brush>objekty se používají k <xref:System.Windows.Shapes.Shape.Stroke%2A> malování <xref:System.Windows.Shapes.Shape.Fill%2A>tvaru a . V následujícím příkladu <xref:System.Windows.Shapes.Ellipse> jsou určeny tah a výplň. Všimněte si, že platný vstup pro vlastnosti stopy může být hodnota klíčového slova nebo šestnáctkové barvy. Další informace o dostupných klíčových slovech barev naleznete v <xref:System.Windows.Media.Colors> vlastnostech třídy v oboru <xref:System.Windows.Media> názvů.  
  
```xaml
<Canvas Background="LightGray">
   <Ellipse  
      Canvas.Top="50"  
      Canvas.Left="50"  
      Fill="#FFFFFF00"  
      Height="75"  
      Width="75"  
      StrokeThickness="5"  
      Stroke="#FF0000FF"/>  
</Canvas>  
```  
  
 Následující obrázek znázorňuje vykreslenou <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elipsu](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Případně můžete použít syntaxi prvku vlastnosti <xref:System.Windows.Media.SolidColorBrush> k explicitnímu vytvoření objektu, který obrazec namaluje plnou barvou.  
  
```xaml
<!-- This polygon shape uses pre-defined color values for its Stroke and  
     Fill properties.   
     The SolidColorBrush's Opacity property affects the fill color in   
     this case by making it slightly transparent (opacity of 0.4) so   
     that it blends with any underlying color. -->  
  
<Polygon  
    Points="300,200 400,125 400,275 300,200"  
    Stroke="Purple"
    StrokeThickness="2">  
    <Polygon.Fill>  
       <SolidColorBrush Color="Blue" Opacity="0.4"/>  
    </Polygon.Fill>  
</Polygon>  
```  
  
 Následující obrázek znázorňuje vykreslený obrazec.  
  
 ![SolidColorBrush ilustrace](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Můžete také malovat tah nebo výplň pomocí přechodů, obrazů, vzorků a dalších. Další informace naleznete v tématu [Malování plnými barvami a přechody Přehled](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a>Roztažitelné tvary  
 <xref:System.Windows.Shapes.Line>Vlastnosti <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>mají <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> , , <xref:System.Windows.Shapes.Shape.Stretch%2A> , a třídy. Tato vlastnost určuje, <xref:System.Windows.Shapes.Shape> jak je obsah objektu (tvar, který má <xref:System.Windows.Shapes.Shape> být nakreslen) roztažen tak, aby vyplnil prostor rozvržení objektu. Prostor <xref:System.Windows.Shapes.Shape> rozložení objektu je velikost <xref:System.Windows.Shapes.Shape> místa, které je přiděleno systémem rozložení, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> z důvodu explicitního a nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení. Další informace o rozložení v nadaci Windows Presentation Foundation najdete v [tématu Přehled rozložení.](../advanced/layout.md)  
  
 Stretch Vlastnost má jednu z následujících hodnot:  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Obsah objektu není roztažený.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen tak, aby vyplnil prostor rozložení.  Poměr stran není zachován.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Obsah objektu je co nejvíce roztažen tak, aby vyplnil prostor rozvržení při zachování původního poměru stran.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen tak, aby zcela vyplnil prostor rozvržení při zachování původního poměru stran.  
  
 Všimněte si, <xref:System.Windows.Shapes.Shape> že když je obsah <xref:System.Windows.Shapes.Shape> objektu roztažený, obrys objektu je po roztažení vymalován.  
  
 V následujícím příkladu <xref:System.Windows.Shapes.Polygon> se a používá k nakreslení velmi malého trojúhelníku od (0,0) do (0,1) do (1,1). Objekt <xref:System.Windows.Shapes.Polygon> je <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou nastaveny na 100 a jeho stretch vlastnost je nastavena na Fill. V důsledku toho <xref:System.Windows.Shapes.Polygon> je obsah objektu (trojúhelník) roztažen tak, aby vyplnil větší prostor.  
  
```xaml
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
```

```csharp
PointCollection myPointCollection = new PointCollection();  
myPointCollection.Add(new Point(0,0));  
myPointCollection.Add(new Point(0,1));  
myPointCollection.Add(new Point(1,1));  
  
Polygon myPolygon = new Polygon();  
myPolygon.Points = myPointCollection;  
myPolygon.Fill = Brushes.Blue;  
myPolygon.Width = 100;  
myPolygon.Height = 100;  
myPolygon.Stretch = Stretch.Fill;  
myPolygon.Stroke = Brushes.Black;  
myPolygon.StrokeThickness = 2;  
```

<a name="transforms"></a>
## <a name="transforming-shapes"></a>Transformace obrazců  
 Třída <xref:System.Windows.Media.Transform> poskytuje prostředky k transformaci tvarů ve dvourozměrné rovině.  Mezi různé typy transformace<xref:System.Windows.Media.RotateTransform>patří otočení<xref:System.Windows.Media.ScaleTransform>(<xref:System.Windows.Media.SkewTransform>), měřítko<xref:System.Windows.Media.TranslateTransform>( ), zkosení ( ) a překlad ( ).  
  
 Běžnou transformací, která se má použít na obrazec, je otočení.  Chcete-li obrazec <xref:System.Windows.Media.RotateTransform> otočit, <xref:System.Windows.Media.RotateTransform.Angle%2A>vytvořte a určete jeho . 45 <xref:System.Windows.Media.RotateTransform.Angle%2A> otočí prvek o 45 stupňů ve směru hodinových ručiček; úhel 90 otočí prvek o 90 stupňů ve směru hodinových ručiček; a tak dále. Nastavte <xref:System.Windows.Media.RotateTransform.CenterX%2A> vlastnosti a, <xref:System.Windows.Media.RotateTransform.CenterY%2A> pokud chcete řídit bod, o který je prvek otočen. Tyto hodnoty vlastností jsou vyjádřeny v souřadnicovém prostoru prvku, který je transformován. <xref:System.Windows.Media.RotateTransform.CenterX%2A>a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula. Nakonec použít <xref:System.Windows.Media.RotateTransform> prvek. Pokud nechcete, aby transformace ovlivnila rozložení, nastavte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost obrazce.  
  
 V následujícím příkladu <xref:System.Windows.Media.RotateTransform> se a používá k otočení obrazce o 45 stupňů kolem levého horního rohu obrazce (0,0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 V dalším příkladu je jiný obrazec otočen o 45 stupňů, ale tentokrát se otočí kolem bodu (25,50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Následující obrázek znázorňuje výsledky použití dvou transformací.  
  
 ![Otočení o 45 stupňů s různými středovými body](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 V předchozích příkladech byla na každý objekt tvaru použita jedna transformace. Chcete-li použít více transformací na obrazec (nebo jakýkoli jiný prvek rozhraní), použijte <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Viz také

- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Přehled geometrie](geometry-overview.md)
- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Přehled animace](animation-overview.md)
