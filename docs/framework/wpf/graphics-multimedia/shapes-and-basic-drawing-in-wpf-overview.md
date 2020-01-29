---
title: Přehled tvarů a základní kresby
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
ms.openlocfilehash: dfdbf67d35cbb13e80d0c5184f165b0cc660e2ef
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731619"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Tvary a základní kresby v přehledu WPF
Toto téma poskytuje přehled o tom, jak kreslit pomocí <xref:System.Windows.Shapes.Shape> objektů. <xref:System.Windows.Shapes.Shape> je typ <xref:System.Windows.UIElement>, který umožňuje nakreslit obrazec na obrazovku. Vzhledem k tomu, že jsou prvky uživatelského rozhraní, <xref:System.Windows.Shapes.Shape> objekty lze použít uvnitř <xref:System.Windows.Controls.Panel> prvků a většiny ovládacích prvků.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] nabízí několik vrstev přístupu ke grafikám a vykreslovacím službám. V horní vrstvě <xref:System.Windows.Shapes.Shape> objekty snadno použít a poskytují mnoho užitečných funkcí, jako je například rozložení a účast v systému událostí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  

<a name="shapes"></a>   
## <a name="shape-objects"></a>Objekty obrazce  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] poskytuje řadu <xref:System.Windows.Shapes.Shape> objektů připravených k použití.  Všechny objekty obrazce dědí z třídy <xref:System.Windows.Shapes.Shape>. Dostupné objekty obrazce zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>a <xref:System.Windows.Shapes.Rectangle>. <xref:System.Windows.Shapes.Shape> objektů sdílí následující společné vlastnosti.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: popisuje, jak je vykreslen Obrys obrazce.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: popisuje tloušťku obrysu tvaru.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: popisuje, jak se vykreslit vnitřní část obrazce.  
  
- Vlastnosti dat pro určení souřadnic a vrcholů měřených v pixelech nezávislých na zařízení.  
  
 Vzhledem k tomu, že jsou odvozeny od <xref:System.Windows.UIElement>, lze objekty obrazce použít uvnitř panelů a většiny ovládacích prvků. <xref:System.Windows.Controls.Canvas> panel je zvlášť dobrým výběrem pro vytváření složitých kreseb, protože podporuje absolutní umístění svých podřízených objektů.  
  
 Třída <xref:System.Windows.Shapes.Line> umožňuje nakreslit čáru mezi dvěma body. Následující příklad ukazuje několik způsobů určení souřadnic řádků a vlastností tahu.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Následující obrázek znázorňuje vykreslený <xref:System.Windows.Shapes.Line>.  
  
 ![Čára – ilustrace](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 I když třída <xref:System.Windows.Shapes.Line> poskytuje vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A>, nastavení nemá žádný vliv, protože <xref:System.Windows.Shapes.Line> nemá žádnou oblast.  
  
 Dalším běžným obrazcem je <xref:System.Windows.Shapes.Ellipse>.  Vytvořte <xref:System.Windows.Shapes.Ellipse> definováním vlastností <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> obrazce. Chcete-li nakreslit kruh, určete <xref:System.Windows.Shapes.Ellipse>, jehož hodnoty <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou stejné.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Následující obrázek ukazuje příklad vykreslené <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elipsa – ilustrace](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a>Používání cest a geometrií  
 Třída <xref:System.Windows.Shapes.Path> umožňuje kreslení křivek a složitých tvarů. Tyto křivky a tvary jsou popsány pomocí <xref:System.Windows.Media.Geometry> objektů. Chcete-li použít <xref:System.Windows.Shapes.Path>, vytvořte <xref:System.Windows.Media.Geometry> a použijte jej k nastavení vlastnosti <xref:System.Windows.Shapes.Path.Data%2A> objektu <xref:System.Windows.Shapes.Path>.  
  
 Existuje řada objektů <xref:System.Windows.Media.Geometry>, ze kterých si můžete vybrat. Třídy <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>a <xref:System.Windows.Media.EllipseGeometry> popisují relativně jednoduché tvary. K vytvoření složitějších tvarů nebo vytváření křivek použijte <xref:System.Windows.Media.PathGeometry>.  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry a PathSegments  
 objekty <xref:System.Windows.Media.PathGeometry> se skládají z jednoho nebo více objektů <xref:System.Windows.Media.PathFigure>; Každý <xref:System.Windows.Media.PathFigure> představuje jiný obrázek nebo tvar. Každý <xref:System.Windows.Media.PathFigure> se skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý představuje připojenou část obrázku nebo tvaru. Typy segmentů zahrnují následující: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>a <xref:System.Windows.Media.ArcSegment>.  
  
 V následujícím příkladu je použita <xref:System.Windows.Shapes.Path> k nakreslení kvadratické Bézierovy křivky.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Vykreslený obrazec znázorňuje následující obrázek.  
  
 ![Ilustrace cesty](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Další informace o <xref:System.Windows.Media.PathGeometry> a dalších třídách <xref:System.Windows.Media.Geometry> naleznete v [přehledu geometrie](geometry-overview.md).  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a>Syntaxe XAML s zkratkou  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete k popisu <xref:System.Windows.Shapes.Path>použít také speciální zkrácenou syntaxi. V následujícím příkladu je použita zkrácená syntaxe pro vykreslení složitého tvaru.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Následující obrázek znázorňuje vykreslený <xref:System.Windows.Shapes.Path>.  
  
 ![Ilustrace cesty](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 Řetězec atributu <xref:System.Windows.Shapes.Path.Data%2A> začíná příkazem "MoveTo", který je označen M, který vytváří počáteční bod pro cestu v souřadnicovém systému <xref:System.Windows.Controls.Canvas>. parametry <xref:System.Windows.Shapes.Path> dat rozlišují velká a malá písmena. Velké písmeno M označuje absolutní umístění pro nový aktuální bod. Malé písmeno m značí relativní souřadnice. První segment je krychle Bézierovy křivky, která začíná na (100 200) a končí (400 175), vykreslená pomocí dvou řídicích bodů (100, 25) a (400 350). Tento segment je označen příkazem jazyka C v řetězci atributu <xref:System.Windows.Shapes.Path.Data%2A>. Opět velké písmeno C označuje absolutní cestu; Malé písmeno c indikuje relativní cestu.  
  
 Druhý segment začíná absolutní horizontální příkazem "LineTo" H, který určuje řádek nakreslený z předchozí koncového bodu dílčí cesty (400 175) do nového koncového bodu (280 175). Vzhledem k tomu, že se jedná o horizontální příkaz "LineTo", zadaná hodnota je souřadnice *x*.  
  
 Úplnou syntaxi cesty najdete v odkazu na <xref:System.Windows.Shapes.Path.Data%2A> a [vytvoření tvaru pomocí PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a>Vybarvení tvarů  
 <xref:System.Windows.Media.Brush> objektů se používají k vykreslování <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.Fill%2A>obrazce. V následujícím příkladu jsou zadány tahy a Fill <xref:System.Windows.Shapes.Ellipse>. Všimněte si, že platný vstup pro vlastnosti štětce může být buď klíčové slovo, nebo hexadecimální hodnota barvy. Další informace o dostupných barevných klíčových klíčích naleznete v tématu vlastnosti <xref:System.Windows.Media.Colors> třídy v oboru názvů <xref:System.Windows.Media>.  
  
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
  
 Následující obrázek znázorňuje vykreslený <xref:System.Windows.Shapes.Ellipse>.  
  
 ![Elipsa](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternativně můžete použít syntaxi elementu Property k explicitnímu vytvoření objektu <xref:System.Windows.Media.SolidColorBrush> k vykreslování tvaru plnou barvou.  
  
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
  
 Následující ilustrace znázorňuje vykreslený obrazec.  
  
 ![Obrázek SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")  
  
 Můžete také malovat tahy nebo výplň obrazce pomocí přechodů, obrázků, vzorů a dalších. Další informace najdete v tématu [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a>Roztažené obrazce  
 Třídy <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>a <xref:System.Windows.Shapes.Rectangle> mají vlastnost <xref:System.Windows.Shapes.Shape.Stretch%2A>. Tato vlastnost určuje, jak má být obsah objektu <xref:System.Windows.Shapes.Shape> (tvar, který má být vykreslen) roztažen tak, aby vyplnil prostor rozložení objektu <xref:System.Windows.Shapes.Shape>. Prostor rozložení <xref:System.Windows.Shapes.Shape>ho objektu je množství místa, které <xref:System.Windows.Shapes.Shape> přiděluje systém rozložení, z důvodu explicitního <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>ho nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení. Další informace o rozložení v Windows Presentation Foundation najdete v tématu Přehled [rozložení](../advanced/layout.md) .  
  
 Vlastnost Stretch přijímá jednu z následujících hodnot:  
  
- <xref:System.Windows.Media.Stretch.None>: obsah objektu <xref:System.Windows.Shapes.Shape> se roztáhne.  
  
- <xref:System.Windows.Media.Stretch.Fill>: obsah objektu <xref:System.Windows.Shapes.Shape> je roztažen tak, aby vyplnil jeho prostor rozložení.  Poměr stran není zachován.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: obsah <xref:System.Windows.Shapes.Shape> objektu se roztáhne co nejvíce, aby se vyplnil jeho prostor rozložení a přitom se zachovává jeho původní poměr stran.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: obsah objektu <xref:System.Windows.Shapes.Shape> se roztáhne, aby se úplně vyplnil jeho prostor rozložení a přitom se zachovává jeho původní poměr stran.  
  
 Všimněte si, že při roztažení obsahu <xref:System.Windows.Shapes.Shape>ho objektu je obrys objektu <xref:System.Windows.Shapes.Shape> vykreslen po roztažení.  
  
 V následujícím příkladu se <xref:System.Windows.Shapes.Polygon> používá k nakreslení velmi malého trojúhelníku od (0, 0) do (0, 1) do (1, 1). <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> objektu <xref:System.Windows.Shapes.Polygon> jsou nastaveny na 100 a vlastnost Stretch je nastavená na Fill. V důsledku toho je obsah objektu <xref:System.Windows.Shapes.Polygon> (trojúhelník) roztažen tak, aby vyplnil větší prostor.  
  
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
 Třída <xref:System.Windows.Media.Transform> poskytuje prostředky pro transformaci tvarů v dvojrozměrné rovině.  Mezi různé typy transformace patří rotace (<xref:System.Windows.Media.RotateTransform>), Scale (<xref:System.Windows.Media.ScaleTransform>), zkosit (<xref:System.Windows.Media.SkewTransform>) a Translation (<xref:System.Windows.Media.TranslateTransform>).  
  
 Společná transformace, která se má použít na obrazec, je rotace.  Chcete-li otočit tvar, vytvořte <xref:System.Windows.Media.RotateTransform> a zadejte jeho <xref:System.Windows.Media.RotateTransform.Angle%2A>. <xref:System.Windows.Media.RotateTransform.Angle%2A> 45 otočí element 45 stupňů po směru hodinových ručiček. úhel 90 otočí element 90 stupňů po směru hodinových ručiček. a tak dále. Nastavte vlastnosti <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A>, pokud chcete určit, kde se má prvek otočit. Tyto hodnoty vlastností se vyjadřují v souřadnicovém prostoru elementu, který se transformuje. <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula. Nakonec použijte <xref:System.Windows.Media.RotateTransform> pro element. Pokud nechcete, aby transformace ovlivnila rozložení, nastavte vlastnost <xref:System.Windows.UIElement.RenderTransform%2A> obrazce.  
  
 V následujícím příkladu se <xref:System.Windows.Media.RotateTransform> používá k otočení tvaru 45 stupňů kolem levého horního rohu obrazce (0, 0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 V dalším příkladu je další tvar otočený 45 stupňů, ale tentokrát se otáčí kolem bodu (25, 50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Následující ilustrace znázorňuje výsledky použití dvou transformací.  
  
 ![45 stupňů otočení s různými centry](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 V předchozích příkladech se u každého objektu Shape použila jedna transformace. Chcete-li použít více transformací na tvar (nebo jakýkoli jiný prvek uživatelského rozhraní), použijte <xref:System.Windows.Media.TransformGroup>.  
  
## <a name="see-also"></a>Viz také:

- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Přehled geometrie](geometry-overview.md)
- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Přehled animace](animation-overview.md)
