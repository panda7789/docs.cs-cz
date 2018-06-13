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
ms.locfileid: "33566308"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="2a636-102">Tvary a základní kresby v přehledu WPF</span><span class="sxs-lookup"><span data-stu-id="2a636-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="2a636-103">Toto téma poskytuje přehled o tom, jak kreslení pomocí <xref:System.Windows.Shapes.Shape> objekty.</span><span class="sxs-lookup"><span data-stu-id="2a636-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="2a636-104">A <xref:System.Windows.Shapes.Shape> je typ <xref:System.Windows.UIElement> , umožňuje kreslení obrazce na obrazovku.</span><span class="sxs-lookup"><span data-stu-id="2a636-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="2a636-105">Protože jsou prvky uživatelského rozhraní, <xref:System.Windows.Shapes.Shape> objekty mohou být použity uvnitř <xref:System.Windows.Controls.Panel> elementy a většina ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="2a636-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="2a636-106"> nabízí několik vrstev přístupu k grafika a vykreslování služby.</span><span class="sxs-lookup"><span data-stu-id="2a636-106"> offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="2a636-107">V horní vrstvě <xref:System.Windows.Shapes.Shape> objekty jsou snadno použitelné a poskytují řady užitečných funkcí, jako je například rozložení a účast v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] událostí systému.</span><span class="sxs-lookup"><span data-stu-id="2a636-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="2a636-108">Objekty tvarů</span><span class="sxs-lookup"><span data-stu-id="2a636-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="2a636-109"> poskytuje řadu připravené k použití <xref:System.Windows.Shapes.Shape> objekty.</span><span class="sxs-lookup"><span data-stu-id="2a636-109"> provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="2a636-110">Všechny objekty tvar dědí <xref:System.Windows.Shapes.Shape> třídy.</span><span class="sxs-lookup"><span data-stu-id="2a636-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="2a636-111">K dispozici tvar objekty zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="2a636-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="2a636-112"><xref:System.Windows.Shapes.Shape> objekty sdílejí následující běžné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2a636-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
-   <span data-ttu-id="2a636-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Popisuje, jak je vykresluje obrysu obrazce.</span><span class="sxs-lookup"><span data-stu-id="2a636-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
-   <span data-ttu-id="2a636-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Popisuje Tloušťka obrysu tvaru.</span><span class="sxs-lookup"><span data-stu-id="2a636-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
-   <span data-ttu-id="2a636-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Popisuje, jak se vykresluje uvnitř tvaru.</span><span class="sxs-lookup"><span data-stu-id="2a636-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
-   <span data-ttu-id="2a636-116">Vlastnosti dat k určení souřadnice a vrcholy, měřená v pixelech nezávislé na zařízení.</span><span class="sxs-lookup"><span data-stu-id="2a636-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="2a636-117">Protože jsou odvozeny od <xref:System.Windows.UIElement>, tvar objekty mohou být použity uvnitř panelů a většina ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="2a636-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="2a636-118"><xref:System.Windows.Controls.Canvas> Panel je obzvláště vhodný pro vytváření komplexní kresby, protože podporuje absolutní umístění jeho podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="2a636-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="2a636-119"><xref:System.Windows.Shapes.Line> Vám umožňuje kreslení čáry mezi dva body.</span><span class="sxs-lookup"><span data-stu-id="2a636-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="2a636-120">Následující příklad znázorňuje několik způsobů, jak určit souřadnice řádku a vlastnosti tahu.</span><span class="sxs-lookup"><span data-stu-id="2a636-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="2a636-121">Následující obrázek ukazuje vygenerované <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="2a636-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="2a636-122">![Řádek obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="2a636-122">![Line illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="2a636-123">I když <xref:System.Windows.Shapes.Line> poskytuje třídy <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost, jeho nastavení nemá žádný vliv, protože <xref:System.Windows.Shapes.Line> nemá žádné oblasti.</span><span class="sxs-lookup"><span data-stu-id="2a636-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="2a636-124">Další běžné obrazec je <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="2a636-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="2a636-125">Vytvoření <xref:System.Windows.Shapes.Ellipse> definováním tvaru <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2a636-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="2a636-126">Kreslení kruh, zadejte <xref:System.Windows.Shapes.Ellipse> jejichž <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou hodnoty stejné.</span><span class="sxs-lookup"><span data-stu-id="2a636-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="2a636-127">Následující obrázek ukazuje příklad vykreslené <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="2a636-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="2a636-128">![Obrázek elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="2a636-128">![Ellipse illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="2a636-129">Pomocí cesty a geometrie</span><span class="sxs-lookup"><span data-stu-id="2a636-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="2a636-130"><xref:System.Windows.Shapes.Path> Vám umožňuje kreslení křivek a obrazců komplexní.</span><span class="sxs-lookup"><span data-stu-id="2a636-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="2a636-131">Tyto křivek a obrazců jsou popsány pomocí <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="2a636-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="2a636-132">Použít <xref:System.Windows.Shapes.Path>, vytvoříte <xref:System.Windows.Media.Geometry> a použít ho nastavit <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Path.Data%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2a636-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="2a636-133">Existují různé <xref:System.Windows.Media.Geometry> objekty lze vybírat.</span><span class="sxs-lookup"><span data-stu-id="2a636-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="2a636-134"><xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, A <xref:System.Windows.Media.EllipseGeometry> třídy popisují poměrně jednoduché tvarů.</span><span class="sxs-lookup"><span data-stu-id="2a636-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="2a636-135">Chcete-li vytvořit složitější tvary nebo křivek, použijte <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="2a636-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="2a636-136">PathGeometry a PathSegments</span><span class="sxs-lookup"><span data-stu-id="2a636-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="2a636-137"><xref:System.Windows.Media.PathGeometry> objekty, které se skládají z jedné nebo více <xref:System.Windows.Media.PathFigure> objekty; každá <xref:System.Windows.Media.PathFigure> představuje různé "obrázek" nebo tvaru.</span><span class="sxs-lookup"><span data-stu-id="2a636-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="2a636-138">Každý <xref:System.Windows.Media.PathFigure> se sám skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objekty, každý představuje připojené část obrázku nebo tvaru.</span><span class="sxs-lookup"><span data-stu-id="2a636-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="2a636-139">Segment typy patří: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, a <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="2a636-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="2a636-140">V následujícím příkladu <xref:System.Windows.Shapes.Path> slouží k vykreslení kvadratické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="2a636-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="2a636-141">Následující obrázek znázorňuje vykreslené tvaru.</span><span class="sxs-lookup"><span data-stu-id="2a636-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="2a636-142">![Cesta k obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="2a636-142">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="2a636-143">Další informace o <xref:System.Windows.Media.PathGeometry> a dalších <xref:System.Windows.Media.Geometry> třídách naleznete v tématu [geometrie přehled](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2a636-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="2a636-144">Syntaxe se používá zkratka XAML</span><span class="sxs-lookup"><span data-stu-id="2a636-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="2a636-145">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete také použít speciální zkrácené syntaxe k popisu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="2a636-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="2a636-146">V následujícím příkladu zkrácené syntaxe slouží k vykreslení komplexní obrazce.</span><span class="sxs-lookup"><span data-stu-id="2a636-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="2a636-147">Následující obrázek ukazuje vykreslovaných <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="2a636-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="2a636-148">![Cesta k obrázku](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="2a636-148">![Path illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="2a636-149"><xref:System.Windows.Shapes.Path.Data%2A> Řetězec atributu začíná příkaz "MoveTo (přesunout)" indikován M, který vytváří bod spuštění pro cestu v souřadnicový systém <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="2a636-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="2a636-150"><xref:System.Windows.Shapes.Path> parametry dat rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="2a636-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="2a636-151">Velké M Určuje absolutní umístění pro nový aktuální bod.</span><span class="sxs-lookup"><span data-stu-id="2a636-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="2a636-152">Malá písmena m by znamenat relativních souřadnicích.</span><span class="sxs-lookup"><span data-stu-id="2a636-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="2a636-153">První segment je krychlový začátku křivku Bézierových na (100,200) a končí na (400,175), vykresleného použití dvou řídit body (100,25) a (400,350).</span><span class="sxs-lookup"><span data-stu-id="2a636-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="2a636-154">Tento segment uvedené v příkazu jazyka C v <xref:System.Windows.Shapes.Path.Data%2A> atribut řetězec.</span><span class="sxs-lookup"><span data-stu-id="2a636-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="2a636-155">Znovu velké C označuje zadat absolutní cestu. malá písmena c by označit relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="2a636-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="2a636-156">Druhý segment začíná příkaz vodorovné absolutní "lineto" H, který určuje linií z předchozí cestou koncového bodu (400,175) pro nový koncový bod (280,175).</span><span class="sxs-lookup"><span data-stu-id="2a636-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="2a636-157">Vzhledem k tomu, že je příkaz vodorovné "lineto", je hodnota zadaná *x*-koordinaci.</span><span class="sxs-lookup"><span data-stu-id="2a636-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="2a636-158">Kompletní cesta syntaxe, najdete v článku <xref:System.Windows.Shapes.Path.Data%2A> odkaz a [vytvořit obrazce pomocí Objekt PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="2a636-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="2a636-159">Malování tvarů</span><span class="sxs-lookup"><span data-stu-id="2a636-159">Painting Shapes</span></span>  
 <span data-ttu-id="2a636-160"><xref:System.Windows.Media.Brush> objekty se používají k vyplnění obrazce <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a636-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="2a636-161">V následujícím příkladu, tah a výplň <xref:System.Windows.Shapes.Ellipse> nejsou zadány.</span><span class="sxs-lookup"><span data-stu-id="2a636-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="2a636-162">Všimněte si, že platného vstupu pro stopy vlastnosti mohou být buď – klíčové slovo nebo hexadecimální hodnoty barvy.</span><span class="sxs-lookup"><span data-stu-id="2a636-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="2a636-163">Další informace o klíčových dostupnou barvu, najdete v části vlastnosti <xref:System.Windows.Media.Colors> třídy v <xref:System.Windows.Media> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="2a636-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="2a636-164">Následující obrázek ukazuje vygenerované <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="2a636-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="2a636-165">![Elipsy](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="2a636-165">![An ellipse](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="2a636-166">Alternativně můžete pomocí syntaxe element vlastnost nemusel vytvářet <xref:System.Windows.Media.SolidColorBrush> objektu k vyplnění obrazce plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="2a636-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="2a636-167">Následující obrázek znázorňuje vykreslené tvaru.</span><span class="sxs-lookup"><span data-stu-id="2a636-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="2a636-168">![SolidColorBrush – ilustrace](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="2a636-168">![SolidColorBrush illustration](../../../../docs/framework/wpf/graphics-multimedia/media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="2a636-169">Můžete také malovat tahu nebo výplně s přechody, obrázky, vzory a další obrazce.</span><span class="sxs-lookup"><span data-stu-id="2a636-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="2a636-170">Další informace najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2a636-170">For more information, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="2a636-171">Rozpínatelnou tvarů</span><span class="sxs-lookup"><span data-stu-id="2a636-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="2a636-172"><xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, A <xref:System.Windows.Shapes.Rectangle> všechny třídy <xref:System.Windows.Shapes.Shape.Stretch%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2a636-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="2a636-173">Tato vlastnost určuje, jak <xref:System.Windows.Shapes.Shape> obsah objektu (tvar, který má být vykreslen) je roztažen tak, aby vyplnil celou <xref:System.Windows.Shapes.Shape> místo rozložení objektu.</span><span class="sxs-lookup"><span data-stu-id="2a636-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="2a636-174">A <xref:System.Windows.Shapes.Shape> místo rozložení objektu je množství místa <xref:System.Windows.Shapes.Shape> je přidělena rozložení systému, protože buď explicitního <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="2a636-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="2a636-175">Další informace o rozložení v systému Windows Presentation Foundation, najdete v části [rozložení](../../../../docs/framework/wpf/advanced/layout.md) Přehled.</span><span class="sxs-lookup"><span data-stu-id="2a636-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../../../../docs/framework/wpf/advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="2a636-176">Vlastnost Stretch má jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="2a636-176">The Stretch property takes one of the following values:</span></span>  
  
-   <span data-ttu-id="2a636-177"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Nejsou roztažen tak obsah objektu.</span><span class="sxs-lookup"><span data-stu-id="2a636-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
-   <span data-ttu-id="2a636-178"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Obsah objektu jsou roztažen tak, aby vyplňování jeho rozložení místa.</span><span class="sxs-lookup"><span data-stu-id="2a636-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="2a636-179">Není zachován poměr stran.</span><span class="sxs-lookup"><span data-stu-id="2a636-179">Aspect ratio is not preserved.</span></span>  
  
-   <span data-ttu-id="2a636-180"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Obsah objektu roztažen tak co nejvíce při vyplňování jeho rozložení místa při zachování jeho původního poměru stran obrázku.</span><span class="sxs-lookup"><span data-stu-id="2a636-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
-   <span data-ttu-id="2a636-181"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Obsah objektu jsou roztažen tak, aby úplně vyplňování jeho rozložení místa při zachování jeho původního poměru stran obrázku.</span><span class="sxs-lookup"><span data-stu-id="2a636-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="2a636-182">Všimněte si, že při <xref:System.Windows.Shapes.Shape> jsou roztažen tak obsah objektu, <xref:System.Windows.Shapes.Shape> obrysu objektu vykreslením po roztažení.</span><span class="sxs-lookup"><span data-stu-id="2a636-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="2a636-183">V následujícím příkladu <xref:System.Windows.Shapes.Polygon> slouží k vykreslení velmi malý trojúhelník z (0,0) (0,1) k (1,1).</span><span class="sxs-lookup"><span data-stu-id="2a636-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="2a636-184"><xref:System.Windows.Shapes.Polygon> Objektu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou nastavené na 100 a jeho stretch vlastnost je nastavena na výplně.</span><span class="sxs-lookup"><span data-stu-id="2a636-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="2a636-185">V důsledku toho <xref:System.Windows.Shapes.Polygon> obsah objektu (trojúhelník) jsou roztažen tak, aby vyplnil větší prostor.</span><span class="sxs-lookup"><span data-stu-id="2a636-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="2a636-186">Transformace tvarů</span><span class="sxs-lookup"><span data-stu-id="2a636-186">Transforming Shapes</span></span>  
 <span data-ttu-id="2a636-187"><xref:System.Windows.Media.Transform> Třída poskytuje způsob, jak transformace obrazců do dvourozměrné roviny.</span><span class="sxs-lookup"><span data-stu-id="2a636-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="2a636-188">Různé typy transformace zahrnují otočení (<xref:System.Windows.Media.RotateTransform>), škálování (<xref:System.Windows.Media.ScaleTransform>), zkosení (<xref:System.Windows.Media.SkewTransform>) a překlad (<xref:System.Windows.Media.TranslateTransform>).</span><span class="sxs-lookup"><span data-stu-id="2a636-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="2a636-189">Běžné transformaci, kterou chcete použít pro obrazce je rotaci kolem.</span><span class="sxs-lookup"><span data-stu-id="2a636-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="2a636-190">Otočení obrazce, vytvoření <xref:System.Windows.Media.RotateTransform> a zadejte jeho <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="2a636-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="2a636-191"><xref:System.Windows.Media.RotateTransform.Angle%2A> 45 otočí element 45 stupňů doprava; úhel 90 otočí element 90 stupňů po směru hodinových ručiček; a tak dále.</span><span class="sxs-lookup"><span data-stu-id="2a636-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="2a636-192">Nastavte <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti, pokud chcete řídit bodem o tom, které element otočen.</span><span class="sxs-lookup"><span data-stu-id="2a636-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="2a636-193">Hodnoty těchto vlastností jsou vyjádřeny v prostoru souřadnic prováděna transformace elementu.</span><span class="sxs-lookup"><span data-stu-id="2a636-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="2a636-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula.</span><span class="sxs-lookup"><span data-stu-id="2a636-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="2a636-195">Nakonec se vztahují <xref:System.Windows.Media.RotateTransform> do elementu.</span><span class="sxs-lookup"><span data-stu-id="2a636-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="2a636-196">Pokud nechcete, aby transformace ovlivnit rozložení, nastavte tvaru <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2a636-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="2a636-197">V následujícím příkladu <xref:System.Windows.Media.RotateTransform> se používá k Otočit tvar 45 stupňů o tvaru levého horního rohu (0,0).</span><span class="sxs-lookup"><span data-stu-id="2a636-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="2a636-198">V následujícím příkladu jiné tvar je otočený 45 stupňů, ale tentokrát je otáčet o bodu (25,50).</span><span class="sxs-lookup"><span data-stu-id="2a636-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="2a636-199">Následující obrázek znázorňuje výsledky použití dvou transformace.</span><span class="sxs-lookup"><span data-stu-id="2a636-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="2a636-200">![Otočení o 45 stupňů s různými středy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="2a636-200">![45 degree rotations with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="2a636-201">V předchozích příkladech jeden transformace byla použita pro každý objekt tvaru.</span><span class="sxs-lookup"><span data-stu-id="2a636-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="2a636-202">Použít více transformací obrazce (nebo jakýkoli další prvek uživatelského rozhraní), použijte <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="2a636-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a636-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="2a636-203">See Also</span></span>  
 [<span data-ttu-id="2a636-204">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="2a636-204">2D Graphics and Imaging</span></span>](../../../../docs/framework/wpf/advanced/optimizing-performance-2d-graphics-and-imaging.md)  
 [<span data-ttu-id="2a636-205">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="2a636-205">Painting with Solid Colors and Gradients Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)  
 [<span data-ttu-id="2a636-206">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="2a636-206">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="2a636-207">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="2a636-207">Walkthrough: My first WPF desktop application</span></span>](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md)  
 [<span data-ttu-id="2a636-208">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="2a636-208">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
