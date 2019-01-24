---
title: Tvary a základní kresby v přehledu WPF
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
ms.openlocfilehash: e3a18d1cf788dfa8f2a9b05077b30af7eeabe584
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665900"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Tvary a základní kresby v přehledu WPF
Toto téma poskytuje přehled o tom, jak kreslení pomocí <xref:System.Windows.Shapes.Shape> objekty. A <xref:System.Windows.Shapes.Shape> je typ <xref:System.Windows.UIElement> , která umožňuje nakreslit obrazec na obrazovku. Protože jsou prvky uživatelského rozhraní, <xref:System.Windows.Shapes.Shape> objekty mohou být použity uvnitř <xref:System.Windows.Controls.Panel> elementy a většina ovládacích prvků.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nabízí několik úrovní přístupu k grafické a vykreslovací služby. V horní vrstvě <xref:System.Windows.Shapes.Shape> objekty jsou snadné použití a poskytují mnoho užitečných funkcí, jako je rozložení a zúčastnit se [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systém událostí.  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Shape – objekty  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje řadu připravených k použití <xref:System.Windows.Shapes.Shape> objekty.  Dědí všechny objekty obrazce <xref:System.Windows.Shapes.Shape> třídy. K dispozici shape – objekty zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape> objekty sdílejí společné následující vlastnosti.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: Popisuje, jak Vymalování obrysu obrazce.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Popisuje tloušťku obrysu obrazce.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: Popisuje, jak je překreslit vnitřní část obrazce.  
  
-   Vlastnosti dat k zadání souřadnic a vrcholy, měřeno v pixelech nezávislých na zařízení.  
  
 Protože jsou odvozeny z <xref:System.Windows.UIElement>, shape – objekty může být použit uvnitř panelů a většina ovládacích prvků. <xref:System.Windows.Controls.Canvas> Panel je obzvláště vhodný pro vytváření komplexních výkresů, protože podporuje absolutní pozici jeho podřízených objektů.  
  
 <xref:System.Windows.Shapes.Line> Třída umožňuje nakreslit čáru mezi dvěma body. Následující příklad ukazuje několik způsobů, jak zadat řádek souřadnice a vlastností tahu.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Následující obrázek ukazuje vygenerované <xref:System.Windows.Shapes.Line>.  
  
 ![Řádek obrázek](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 I když <xref:System.Windows.Shapes.Line> poskytuje třídy <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost nastavení nemá žádný vliv, protože <xref:System.Windows.Shapes.Line> nemá žádné oblasti.  
  
 Je jiné běžné obrazce <xref:System.Windows.Shapes.Ellipse>.  Vytvoření <xref:System.Windows.Shapes.Ellipse> definováním obrazce <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti. Chcete-li nakreslit kruh, zadejte <xref:System.Windows.Shapes.Ellipse> jehož <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou hodnoty stejné.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Následující obrázek ukazuje příklad vykreslovaných <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Obrázek Elipsa](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Pomocí cesty a geometrie  
 <xref:System.Windows.Shapes.Path> Třída umožňuje kreslení křivek a obrazců složité. Tyto křivky a obrazce se popisují pomocí <xref:System.Windows.Media.Geometry> objekty. Použití <xref:System.Windows.Shapes.Path>, vytvoříte <xref:System.Windows.Media.Geometry> a použít ho nastavit <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Path.Data%2A> vlastnost.  
  
 Existuje široká škála <xref:System.Windows.Media.Geometry> objekty lze vybírat. <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, A <xref:System.Windows.Media.EllipseGeometry> třídy popisují relativně jednoduché obrazce. Pokud chcete vytvářet složitější tvary nebo vytvořit křivky, použijte <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry – a PathSegments  
 <xref:System.Windows.Media.PathGeometry> objekty jsou složená z jednoho nebo více <xref:System.Windows.Media.PathFigure> objektů; každý <xref:System.Windows.Media.PathFigure> představuje různé "obrázek" nebo tvar. Každý <xref:System.Windows.Media.PathFigure> je samotný sestávající z jednoho nebo více <xref:System.Windows.Media.PathSegment> objekty, každý představující připojených část obrázku nebo tvar. Segment typy zahrnují následující: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, a <xref:System.Windows.Media.ArcSegment>.  
  
 V následujícím příkladu <xref:System.Windows.Shapes.Path> se používá k nakreslení kvadratické Bézierovy křivky.  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Následující obrázek ukazuje vykreslené tvaru.  
  
 ![Cesta k obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Další informace o <xref:System.Windows.Media.PathGeometry> a druhý <xref:System.Windows.Media.Geometry> třídy, najdete v článku [přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>XAML se používá zkratka syntaxe  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete také použít speciální syntaxe zkrácený k popisu <xref:System.Windows.Shapes.Path>. V následujícím příkladu se používá zkrácený syntaxe nakreslit obrazec složité.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Následující obrázek ukazuje vykreslovaných <xref:System.Windows.Shapes.Path>.  
  
 ![Cesta k obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> Atribut řetězec začíná příkazu "moveto" indikován M, který vytváří bod spuštění pro cestu ve službě souřadnicový systém <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path> data parametrů rozlišují malá a velká písmena. Velké M označuje absolutní umístění pro nové aktuálního místa. Malá písmena m by označoval relativních souřadnicích. První segment je kubické Bézierovy křivky počínaje (100,200) a končící (400,175), vykresleného pomocí nich řídit body (100,25) a (400,350). Tento segment je indikován příkaz jazyka C v <xref:System.Windows.Shapes.Path.Data%2A> atribut řetězců. Znovu velké C určuje absolutní cestu. malá písmena c by označoval relativní cestu.  
  
 Druhý segment začíná příkaz vodorovné absolutní "lineto" H, který určuje linií z předchozích podřízená cesta koncového bodu (400,175) do nového koncového bodu (280,175). Protože je příkaz vodorovné "lineto", je hodnota zadaná *x*-koordinaci.  
  
 Úplná cesta syntaxi naleznete v tématu <xref:System.Windows.Shapes.Path.Data%2A> odkaz a [vytvoření tvaru použitím PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Malování obrazců  
 <xref:System.Windows.Media.Brush> objekty se používají k vyplnění obrazce <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.Fill%2A>. V následujícím příkladu, stroke a výplň <xref:System.Windows.Shapes.Ellipse> jsou uvedeny. Všimněte si, že platného vstupu pro vlastnosti štětce může být buď klíčové slovo nebo šestnáctková hodnota barvy. Další informace o klíčových slovech dostupnou barvu najdete v tématu vlastnosti <xref:System.Windows.Media.Colors> třídy v <xref:System.Windows.Media> oboru názvů.  
  
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
  
 Následující obrázek ukazuje vygenerované <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elipsa](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternativně můžete syntax prvku vlastnosti explicitně vytvořit <xref:System.Windows.Media.SolidColorBrush> objektu k vyplnění obrazce plnou barvou.  
  
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
  
 Následující obrázek znázorňuje vykreslené tvaru.  
  
 ![Obrázek SolidColorBrush](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Můžete také malovat stroke nebo výplň s přechody, obrázky, modely a více obrazce. Další informace najdete v tématu [Malování plnými barvami a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Obrazce umožňující roztažení  
 <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, A <xref:System.Windows.Shapes.Rectangle> mít všechny třídy <xref:System.Windows.Shapes.Shape.Stretch%2A> vlastnost. Tato vlastnost určuje, jak <xref:System.Windows.Shapes.Shape> je tak, aby vyplnil roztažený obsah na objekt (shape chcete kreslit) <xref:System.Windows.Shapes.Shape> místo rozložení objektu. A <xref:System.Windows.Shapes.Shape> objektu rozložení místo představuje velikost místa <xref:System.Windows.Shapes.Shape> je přidělena systém rozložení, protože buď explicitní <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení. Další informace o rozložení ve Windows Presentation Foundation, najdete v části [rozložení](../../../../docs/framework/wpf/advanced/layout.md) Přehled.  
  
 Vlastnost Stretch má jednu z následujících hodnot:  
  
-   <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Nejsou roztažený obsah objektu.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Jsou roztažený obsah objektu tak, aby vyplnil místo jeho rozložení.  Poměr stran nezachová.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Jsou roztažený obsah objektu tak, aby vyplnil místo jeho rozložení zachováním jeho původního poměru stran co nejvíc.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Pro úplně naplnění jeho rozložení místo zachováním jeho původní poměr stran obrázku jsou roztažený obsah objektu.  
  
 Všimněte si, že když <xref:System.Windows.Shapes.Shape> jsou roztažený obsah objektu, <xref:System.Windows.Shapes.Shape> obrysu objektu vymalováním po roztažení.  
  
 V následujícím příkladu <xref:System.Windows.Shapes.Polygon> se používá k nakreslení velmi malý trojúhelník z (0,0) (0,1) na (1,1). <xref:System.Windows.Shapes.Polygon> Objektu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou nastaveny na hodnotu 100, a jeho roztáhnout vlastnost je nastavena na hodnotu Fill. V důsledku toho <xref:System.Windows.Shapes.Polygon> obsah objektu (trojúhelník) jsou roztažen tak, aby vyplnil místo větší.  
  
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
 <xref:System.Windows.Media.Transform> Třída poskytuje způsob, jak transformace obrazců do dvourozměrné roviny.  Různé druhy transformace zahrnují otočení (<xref:System.Windows.Media.RotateTransform>), škálování (<xref:System.Windows.Media.ScaleTransform>), posun (<xref:System.Windows.Media.SkewTransform>) a překladu (<xref:System.Windows.Media.TranslateTransform>).  
  
 Běžné transformace má použít pro obrazec je otočení.  Otočíte tvar, vytvořit <xref:System.Windows.Media.RotateTransform> a určit jeho <xref:System.Windows.Media.RotateTransform.Angle%2A>. <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 otočí element 45 stupňů doprava, kterým je úhel 90 otočí element 90 stupňů po směru hodinových ručiček, a tak dále. Nastavte <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti, pokud chcete řídicí bod o tom, které se otočí element. Hodnoty těchto vlastností jsou vyjádřeny v souřadnicového prostoru element, který se má transformovat. <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula. Nakonec se vztahují <xref:System.Windows.Media.RotateTransform> na prvek. Pokud nechcete, aby transformací, která má být ovlivněn rozložení, nastavte obrazce <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.  
  
 V následujícím příkladu <xref:System.Windows.Media.RotateTransform> slouží k otáčet 45 stupňů obrazec o tvaru levého horního rohu (0; 0).  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 V následujícím příkladu jiný tvar je otočený 45 stupňů, ale tentokrát je otočený o bodu (25,50).  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Na následujícím obrázku je výsledkem použití dvou transformací.  
  
 ![45 stupňů rotace s různými středy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 V předchozích příkladech byla použita jeden transformace každého objektu shape. Použití několika transformací na tvar (nebo jiný prvek uživatelského rozhraní), použijte <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Viz také:
- [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)
- [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)
- [Návod: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
