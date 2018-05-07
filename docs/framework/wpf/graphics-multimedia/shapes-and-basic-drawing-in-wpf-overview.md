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
ms.openlocfilehash: adbf982da25ff445d277b7c1b5911217d9825c02
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Tvary a základní kresby v přehledu WPF
Toto téma poskytuje přehled o tom, jak kreslení pomocí <xref:System.Windows.Shapes.Shape> objekty. A <xref:System.Windows.Shapes.Shape> je typ <xref:System.Windows.UIElement> , umožňuje kreslení obrazce na obrazovku. Protože jsou prvky uživatelského rozhraní, <xref:System.Windows.Shapes.Shape> objekty mohou být použity uvnitř <xref:System.Windows.Controls.Panel> elementy a většina ovládacích prvků.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nabízí několik vrstev přístupu k grafika a vykreslování služby. V horní vrstvě <xref:System.Windows.Shapes.Shape> objekty jsou snadno použitelné a poskytují řady užitečných funkcí, jako je například rozložení a účast v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] událostí systému.  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a>Objekty tvarů  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje řadu připravené k použití <xref:System.Windows.Shapes.Shape> objekty.  Všechny objekty tvar dědí <xref:System.Windows.Shapes.Shape> třídy. K dispozici tvar objekty zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape> objekty sdílejí následující běžné vlastnosti.  
  
-   <xref:System.Windows.Shapes.Shape.Stroke%2A>: Popisuje, jak je vykresluje obrysu obrazce.  
  
-   <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Popisuje Tloušťka obrysu tvaru.  
  
-   <xref:System.Windows.Shapes.Shape.Fill%2A>: Popisuje, jak se vykresluje uvnitř tvaru.  
  
-   Vlastnosti dat k určení souřadnice a vrcholy, měřená v pixelech nezávislé na zařízení.  
  
 Protože jsou odvozeny od <xref:System.Windows.UIElement>, tvar objekty mohou být použity uvnitř panelů a většina ovládacích prvků. <xref:System.Windows.Controls.Canvas> Panel je obzvláště vhodný pro vytváření komplexní kresby, protože podporuje absolutní umístění jeho podřízených objektů.  
  
 <xref:System.Windows.Shapes.Line> Vám umožňuje kreslení čáry mezi dva body. Následující příklad znázorňuje několik způsobů, jak určit souřadnice řádku a vlastnosti tahu.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Následující obrázek ukazuje vygenerované <xref:System.Windows.Shapes.Line>.  
  
 ![Řádek obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 I když <xref:System.Windows.Shapes.Line> poskytuje třídy <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost, jeho nastavení nemá žádný vliv, protože <xref:System.Windows.Shapes.Line> nemá žádné oblasti.  
  
 Další běžné obrazec je <xref:System.Windows.Shapes.Ellipse>.  Vytvoření <xref:System.Windows.Shapes.Ellipse> definováním tvaru <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti. Kreslení kruh, zadejte <xref:System.Windows.Shapes.Ellipse> jejichž <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou hodnoty stejné.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Následující obrázek ukazuje příklad vykreslené <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Obrázek elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Pomocí cesty a geometrie  
 <xref:System.Windows.Shapes.Path> Vám umožňuje kreslení křivek a obrazců komplexní. Tyto křivek a obrazců jsou popsány pomocí <xref:System.Windows.Media.Geometry> objekty. Použít <xref:System.Windows.Shapes.Path>, vytvoříte <xref:System.Windows.Media.Geometry> a použít ho nastavit <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Path.Data%2A> vlastnost.  
  
 Existují různé <xref:System.Windows.Media.Geometry> objekty lze vybírat. <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, A <xref:System.Windows.Media.EllipseGeometry> třídy popisují poměrně jednoduché tvarů. Chcete-li vytvořit složitější tvary nebo křivek, použijte <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry a PathSegments  
 <xref:System.Windows.Media.PathGeometry> objekty, které se skládají z jedné nebo více <xref:System.Windows.Media.PathFigure> objekty; každá <xref:System.Windows.Media.PathFigure> představuje různé "obrázek" nebo tvaru. Každý <xref:System.Windows.Media.PathFigure> se sám skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objekty, každý představuje připojené část obrázku nebo tvaru. Segment typy patří: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, a <xref:System.Windows.Media.ArcSegment>.  
  
 V následujícím příkladu <xref:System.Windows.Shapes.Path> slouží k vykreslení kvadratické Bézierovy křivky.  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Následující obrázek znázorňuje vykreslené tvaru.  
  
 ![Cesta k obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Další informace o <xref:System.Windows.Media.PathGeometry> a dalších <xref:System.Windows.Media.Geometry> třídách naleznete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>Syntaxe se používá zkratka XAML  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete také použít speciální zkrácené syntaxe k popisu <xref:System.Windows.Shapes.Path>. V následujícím příkladu zkrácené syntaxe slouží k vykreslení komplexní obrazce.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Následující obrázek ukazuje vykreslovaných <xref:System.Windows.Shapes.Path>.  
  
 ![Cesta k obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A> Řetězec atributu začíná příkaz "MoveTo (přesunout)" indikován M, který vytváří bod spuštění pro cestu v souřadnicový systém <xref:System.Windows.Controls.Canvas>. <xref:System.Windows.Shapes.Path> parametry dat rozlišují velká a malá písmena. Velké M Určuje absolutní umístění pro nový aktuální bod. Malá písmena m by znamenat relativních souřadnicích. První segment je krychlový začátku křivku Bézierových na (100,200) a končí na (400,175), vykresleného použití dvou řídit body (100,25) a (400,350). Tento segment uvedené v příkazu jazyka C v <xref:System.Windows.Shapes.Path.Data%2A> atribut řetězec. Znovu velké C označuje zadat absolutní cestu. malá písmena c by označit relativní cestu.  
  
 Druhý segment začíná příkaz vodorovné absolutní "lineto" H, který určuje linií z předchozí cestou koncového bodu (400,175) pro nový koncový bod (280,175). Vzhledem k tomu, že je příkaz vodorovné "lineto", je hodnota zadaná *x*-koordinaci.  
  
 Kompletní cesta syntaxe, najdete v článku <xref:System.Windows.Shapes.Path.Data%2A> odkaz a [vytvořit obrazce pomocí Objekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Malování tvarů  
 <xref:System.Windows.Media.Brush> objekty se používají k vyplnění obrazce <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.Fill%2A>. V následujícím příkladu, tah a výplň <xref:System.Windows.Shapes.Ellipse> nejsou zadány. Všimněte si, že platného vstupu pro stopy vlastnosti mohou být buď – klíčové slovo nebo hexadecimální hodnoty barvy. Další informace o klíčových dostupnou barvu, najdete v části vlastnosti <xref:System.Windows.Media.Colors> třídy v <xref:System.Windows.Media> oboru názvů.  
  
```  
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
  
 ![Elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternativně můžete pomocí syntaxe element vlastnost nemusel vytvářet <xref:System.Windows.Media.SolidColorBrush> objektu k vyplnění obrazce plnou barvou.  
  
```  
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
  
 ![SolidColorBrush – ilustrace](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Můžete také malovat tahu nebo výplně s přechody, obrázky, vzory a další obrazce. Další informace najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Rozpínatelnou tvarů  
 <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, A <xref:System.Windows.Shapes.Rectangle> všechny třídy <xref:System.Windows.Shapes.Shape.Stretch%2A> vlastnost. Tato vlastnost určuje, jak <xref:System.Windows.Shapes.Shape> obsah objektu (tvar, který má být vykreslen) je roztažen tak, aby vyplnil celou <xref:System.Windows.Shapes.Shape> místo rozložení objektu. A <xref:System.Windows.Shapes.Shape> místo rozložení objektu je množství místa <xref:System.Windows.Shapes.Shape> je přidělena rozložení systému, protože buď explicitního <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení. Další informace o rozložení v systému Windows Presentation Foundation, najdete v části [rozložení](../../../../docs/framework/wpf/advanced/layout.md) Přehled.  
  
 Vlastnost Stretch má jednu z následujících hodnot:  
  
-   <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Nejsou roztažen tak obsah objektu.  
  
-   <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Obsah objektu jsou roztažen tak, aby vyplňování jeho rozložení místa.  Není zachován poměr stran.  
  
-   <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Obsah objektu roztažen tak co nejvíce při vyplňování jeho rozložení místa při zachování jeho původního poměru stran obrázku.  
  
-   <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Obsah objektu jsou roztažen tak, aby úplně vyplňování jeho rozložení místa při zachování jeho původního poměru stran obrázku.  
  
 Všimněte si, že při <xref:System.Windows.Shapes.Shape> jsou roztažen tak obsah objektu, <xref:System.Windows.Shapes.Shape> obrysu objektu vykreslením po roztažení.  
  
 V následujícím příkladu <xref:System.Windows.Shapes.Polygon> slouží k vykreslení velmi malý trojúhelník z (0,0) (0,1) k (1,1). <xref:System.Windows.Shapes.Polygon> Objektu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou nastavené na 100 a jeho stretch vlastnost je nastavena na výplně. V důsledku toho <xref:System.Windows.Shapes.Polygon> obsah objektu (trojúhelník) jsou roztažen tak, aby vyplnil větší prostor.  
  
```  
...  
<Polygon  
  Points="0,0 0,1 1,1"  
  Fill="Blue"  
  Width="100"  
  Height="100"  
  Stretch="Fill"  
  Stroke="Black"  
  StrokeThickness="2" />  
...  
```  
  
```  
...  
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
...  
```  
  
<a name="transforms"></a>   
## <a name="transforming-shapes"></a>Transformace tvarů  
 <xref:System.Windows.Media.Transform> Třída poskytuje způsob, jak transformace obrazců do dvourozměrné roviny.  Různé typy transformace zahrnují otočení (<xref:System.Windows.Media.RotateTransform>), škálování (<xref:System.Windows.Media.ScaleTransform>), zkosení (<xref:System.Windows.Media.SkewTransform>) a překlad (<xref:System.Windows.Media.TranslateTransform>).  
  
 Běžné transformaci, kterou chcete použít pro obrazce je rotaci kolem.  Otočení obrazce, vytvoření <xref:System.Windows.Media.RotateTransform> a zadejte jeho <xref:System.Windows.Media.RotateTransform.Angle%2A>. <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 otočí element 45 stupňů doprava; úhel 90 otočí element 90 stupňů po směru hodinových ručiček; a tak dále. Nastavte <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti, pokud chcete řídit bodem o tom, které element otočen. Hodnoty těchto vlastností jsou vyjádřeny v prostoru souřadnic prováděna transformace elementu. <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula. Nakonec se vztahují <xref:System.Windows.Media.RotateTransform> do elementu. Pokud nechcete, aby transformace ovlivnit rozložení, nastavte tvaru <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.  
  
 V následujícím příkladu <xref:System.Windows.Media.RotateTransform> se používá k Otočit tvar 45 stupňů o tvaru levého horního rohu (0,0).  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 V následujícím příkladu jiné tvar je otočený 45 stupňů, ale tentokrát je otáčet o bodu (25,50).  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Následující obrázek znázorňuje výsledky použití dvou transformace.  
  
 ![Otočení o 45 stupňů s různými středy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 V předchozích příkladech jeden transformace byla použita pro každý objekt tvaru. Použít více transformací obrazce (nebo jakýkoli další prvek uživatelského rozhraní), použijte <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Viz také  
 [2D grafika a obrázky](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [Přehled malování plnými barvami a přechody](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [Přehled geometrie](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [Návod: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
