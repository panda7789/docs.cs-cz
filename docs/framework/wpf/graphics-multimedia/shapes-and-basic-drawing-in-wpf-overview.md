---
title: Přehled tvarů a základní kresby
description: Rozšiřte své uživatelské rozhraní pomocí obrazců připraveného k použití a několika vrstev vydaných vykreslovacích služeb v Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 41d8f2b87232740c8945bd6a6099aa86dbe77bc6
ms.sourcegitcommit: b6a1869f97a37f11a68c90afde1a520a6887dcbc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2020
ms.locfileid: "85853696"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a>Tvary a základní kresby v přehledu WPF
Toto téma poskytuje přehled o tom, jak kreslit s <xref:System.Windows.Shapes.Shape> objekty. <xref:System.Windows.Shapes.Shape>Je typ <xref:System.Windows.UIElement> , který umožňuje nakreslit obrazec na obrazovku. Vzhledem k tomu, že jsou prvky uživatelského rozhraní, <xref:System.Windows.Shapes.Shape> lze objekty použít uvnitř <xref:System.Windows.Controls.Panel> prvků a většiny ovládacích prvků.  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]nabízí několik vrstev přístupu ke grafikám a vykreslovacím službám. V horní vrstvě se <xref:System.Windows.Shapes.Shape> objekty snadno používají a poskytují mnoho užitečných funkcí, jako je například rozložení a účast v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systému událostí.  

<a name="shapes"></a>
## <a name="shape-objects"></a>Objekty obrazce  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje několik objektů připravených k použití <xref:System.Windows.Shapes.Shape> .  Všechny objekty obrazce dědí z <xref:System.Windows.Shapes.Shape> třídy. Dostupné objekty obrazce zahrnují <xref:System.Windows.Shapes.Ellipse> , <xref:System.Windows.Shapes.Line> , <xref:System.Windows.Shapes.Path> , <xref:System.Windows.Shapes.Polygon> , <xref:System.Windows.Shapes.Polyline> a <xref:System.Windows.Shapes.Rectangle> . <xref:System.Windows.Shapes.Shape>objekty sdílejí následující společné vlastnosti.  
  
- <xref:System.Windows.Shapes.Shape.Stroke%2A>: Popisuje, jak je vykreslen obrys tvaru.  
  
- <xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Popisuje tloušťku obrysu tvaru.  
  
- <xref:System.Windows.Shapes.Shape.Fill%2A>: Popisuje, jak je vykreslen vnitřní prvek obrazce.  
  
- Vlastnosti dat pro určení souřadnic a vrcholů měřených v pixelech nezávislých na zařízení.  
  
 Vzhledem k tomu, že jsou odvozeny z <xref:System.Windows.UIElement> , lze použít objekty obrazce uvnitř panelů a většiny ovládacích prvků. <xref:System.Windows.Controls.Canvas>Panel je zvlášť dobrý volbou pro vytváření složitých kreseb, protože podporuje absolutní umístění svých podřízených objektů.  
  
 <xref:System.Windows.Shapes.Line>Třída umožňuje nakreslit čáru mezi dvěma body. Následující příklad ukazuje několik způsobů určení souřadnic řádků a vlastností tahu.  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 Vykreslení znázorňuje následující obrázek <xref:System.Windows.Shapes.Line> .  
  
 ![Čára – ilustrace](./media/shape-ovw-line2.gif "shape_ovw_line2")  
  
 I když <xref:System.Windows.Shapes.Line> Třída poskytuje <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost, nastavení nemá žádný vliv, protože <xref:System.Windows.Shapes.Line> nemá žádnou oblast.  
  
 Dalším běžným obrazcem je <xref:System.Windows.Shapes.Ellipse> .  Vytvořte <xref:System.Windows.Shapes.Ellipse> pomocí definováním <xref:System.Windows.FrameworkElement.Width%2A> vlastností a vlastností obrazce <xref:System.Windows.FrameworkElement.Height%2A> . Chcete-li nakreslit kruh, zadejte, <xref:System.Windows.Shapes.Ellipse> jejichž <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> hodnoty a jsou stejné.  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 Následující obrázek ukazuje příklad vykreslené <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Elipsa – ilustrace](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a>Používání cest a geometrií  
 <xref:System.Windows.Shapes.Path>Třída umožňuje nakreslit křivky a složité tvary. Tyto křivky a tvary jsou popsány pomocí <xref:System.Windows.Media.Geometry> objektů. Chcete-li použít <xref:System.Windows.Shapes.Path> , vytvoříte <xref:System.Windows.Media.Geometry> a použijete jej k nastavení <xref:System.Windows.Shapes.Path> vlastnosti objektu <xref:System.Windows.Shapes.Path.Data%2A> .  
  
 Existuje řada <xref:System.Windows.Media.Geometry> objektů, ze kterých si můžete vybrat. <xref:System.Windows.Media.LineGeometry>Třídy, <xref:System.Windows.Media.RectangleGeometry> a <xref:System.Windows.Media.EllipseGeometry> popisují relativně jednoduché tvary. Chcete-li vytvořit složitější tvary nebo vytvořit křivky, použijte <xref:System.Windows.Media.PathGeometry> .  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a>PathGeometry a PathSegments  
 <xref:System.Windows.Media.PathGeometry>objekty se skládají z jednoho nebo více <xref:System.Windows.Media.PathFigure> objektů; každá <xref:System.Windows.Media.PathFigure> představuje jiný "obrázek" nebo tvar. Každá <xref:System.Windows.Media.PathFigure> z nich se skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý představuje připojenou část obrázku nebo tvaru. Typy segmentů zahrnují následující: <xref:System.Windows.Media.LineSegment> , <xref:System.Windows.Media.BezierSegment> , a <xref:System.Windows.Media.ArcSegment> .  
  
 V následujícím příkladu <xref:System.Windows.Shapes.Path> je použit k nakreslení kvadratické Bézierovy křivky.  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 Vykreslený obrazec znázorňuje následující obrázek.  
  
 ![Ilustrace cesty](./media/shape-ovw-path2.gif "shape_ovw_path2")  
  
 Další informace o <xref:System.Windows.Media.PathGeometry> a dalších <xref:System.Windows.Media.Geometry> třídách naleznete v [přehledu geometrie](geometry-overview.md).  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a>Syntaxe XAML s zkratkou  
 V aplikaci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] můžete použít také speciální zkrácenou syntaxi k popisu <xref:System.Windows.Shapes.Path> . V následujícím příkladu je použita zkrácená syntaxe pro vykreslení složitého tvaru.  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 Následující obrázek znázorňuje vykreslený <xref:System.Windows.Shapes.Path> .  
  
 ![Ilustrace cesty](./media/shape-ovw-path.PNG "shape_ovw_path")  
  
 <xref:System.Windows.Shapes.Path.Data%2A>Řetězec atributu začíná příkazem "MoveTo", který je označen M, který vytváří počáteční bod pro cestu v souřadnicovém systému <xref:System.Windows.Controls.Canvas> . <xref:System.Windows.Shapes.Path>v parametrech dat se rozlišují velká a malá písmena. Velké písmeno M označuje absolutní umístění pro nový aktuální bod. Malé písmeno m značí relativní souřadnice. První segment je krychle Bézierovy křivky, která začíná na (100 200) a končí (400 175), vykreslená pomocí dvou řídicích bodů (100, 25) a (400 350). Tento segment je označen příkazem jazyka C v <xref:System.Windows.Shapes.Path.Data%2A> řetězci atributu. Opět velké písmeno C označuje absolutní cestu; Malé písmeno c indikuje relativní cestu.  
  
 Druhý segment začíná absolutní horizontální příkazem "LineTo" H, který určuje řádek nakreslený z předchozí koncového bodu dílčí cesty (400 175) do nového koncového bodu (280 175). Vzhledem k tomu, že se jedná o horizontální příkaz "LineTo", zadaná hodnota je souřadnice *x*.  
  
 Úplnou syntaxi cesty naleznete v <xref:System.Windows.Shapes.Path.Data%2A> odkazu a [vytvoření tvaru pomocí PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a>Vybarvení tvarů  
 <xref:System.Windows.Media.Brush>objekty slouží k malování <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.Fill%2A> . V následujícím příkladu je zadán tah a výplň <xref:System.Windows.Shapes.Ellipse> . Všimněte si, že platný vstup pro vlastnosti štětce může být buď klíčové slovo, nebo hexadecimální hodnota barvy. Další informace o dostupných barevných klíčových klíčích naleznete v tématu vlastnosti <xref:System.Windows.Media.Colors> třídy v <xref:System.Windows.Media> oboru názvů.  
  
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
  
 Vykreslení znázorňuje následující obrázek <xref:System.Windows.Shapes.Ellipse> .  
  
 ![Elipsa](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")  
  
 Alternativně můžete použít syntaxi elementu vlastnosti k explicitnímu vytvoření <xref:System.Windows.Media.SolidColorBrush> objektu pro malování tvaru plnou barvou.  
  
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
 <xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path> Všechny třídy,,, <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> a <xref:System.Windows.Shapes.Rectangle> mají <xref:System.Windows.Shapes.Shape.Stretch%2A> vlastnost. Tato vlastnost určuje, jak <xref:System.Windows.Shapes.Shape> je obsah objektu (tvar, který má být vykreslen) roztažen tak, aby vyplnil <xref:System.Windows.Shapes.Shape> prostor rozložení objektu. <xref:System.Windows.Shapes.Shape>Prostor rozložení objektu je množství místa, které <xref:System.Windows.Shapes.Shape> je přiděleno systémem rozložení, z důvodu explicitního <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení a. Další informace o rozložení v Windows Presentation Foundation najdete v tématu Přehled [rozložení](../advanced/layout.md) .  
  
 Vlastnost Stretch přijímá jednu z následujících hodnot:  
  
- <xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Obsah objektu není roztažen.  
  
- <xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen tak, aby vyplnil jeho prostor rozložení.  Poměr stran není zachován.  
  
- <xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen co nejvíce, aby bylo možné vyplnit jeho prostor rozložení a přitom zachovat jeho původní poměr stran.  
  
- <xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen tak, aby zcela vyplnil své místo rozložení při zachování původního poměru stran.  
  
 Všimněte si, že při <xref:System.Windows.Shapes.Shape> roztažení obsahu objektu <xref:System.Windows.Shapes.Shape> je obrys objektu vykreslen po roztažení.  
  
 V následujícím příkladu <xref:System.Windows.Shapes.Polygon> se používá k nakreslení velmi malého trojúhelníku od (0, 0) do (0, 1) do (1, 1). <xref:System.Windows.Shapes.Polygon>Objekt <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> je nastaven na 100 a jeho vlastnost Stretch je nastavena na hodnotu Fill. V důsledku toho je <xref:System.Windows.Shapes.Polygon> obsah objektu (trojúhelník) roztažen tak, aby vyplnil větší prostor.  
  
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
 <xref:System.Windows.Media.Transform>Třída poskytuje prostředky pro transformaci tvarů v dvourozměrné rovině.  Mezi různé typy transformace patří rotace ( <xref:System.Windows.Media.RotateTransform> ), Scale ( <xref:System.Windows.Media.ScaleTransform> ), zkosit ( <xref:System.Windows.Media.SkewTransform> ) a Translation ( <xref:System.Windows.Media.TranslateTransform> ).  
  
 Společná transformace, která se má použít na obrazec, je rotace.  Chcete-li otočit tvar, vytvořte <xref:System.Windows.Media.RotateTransform> a zadejte jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> . <xref:System.Windows.Media.RotateTransform.Angle%2A>Z 45 otočit element 45 stupňů po směru hodinových ručiček; úhel 90 otočí element o 90 stupňů po směru hodinových ručiček a tak dále. Nastavte <xref:System.Windows.Media.RotateTransform.CenterX%2A> vlastnosti a, <xref:System.Windows.Media.RotateTransform.CenterY%2A> Pokud chcete určit, kde má být prvek otočen. Tyto hodnoty vlastností se vyjadřují v souřadnicovém prostoru elementu, který se transformuje. <xref:System.Windows.Media.RotateTransform.CenterX%2A>a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula. Nakonec použijte <xref:System.Windows.Media.RotateTransform> pro element. Pokud nechcete, aby transformace ovlivnila rozložení, nastavte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost tvaru.  
  
 V následujícím příkladu <xref:System.Windows.Media.RotateTransform> se používá k otočení tvaru 45 stupňů kolem levého horního rohu obrazce (0, 0).  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 V dalším příkladu je další tvar otočený 45 stupňů, ale tentokrát se otáčí kolem bodu (25, 50).  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 Následující ilustrace znázorňuje výsledky použití dvou transformací.  
  
 ![45 stupňů otočení s různými centry](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")  
  
 V předchozích příkladech se u každého objektu Shape použila jedna transformace. Chcete-li použít více transformací na tvar (nebo jakýkoli jiný prvek uživatelského rozhraní), použijte <xref:System.Windows.Media.TransformGroup> .  
  
## <a name="see-also"></a>Viz také

- [2D grafika a obrázky](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md)
- [Přehled geometrie](geometry-overview.md)
- [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [Přehled animace](animation-overview.md)
