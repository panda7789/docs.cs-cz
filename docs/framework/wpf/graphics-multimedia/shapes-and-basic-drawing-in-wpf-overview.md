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
ms.openlocfilehash: 9852c811b00ee7f8d86b7c1daaaa28f28fa5a89f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57372734"
---
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="e7dee-102">Tvary a základní kresby v přehledu WPF</span><span class="sxs-lookup"><span data-stu-id="e7dee-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="e7dee-103">Toto téma poskytuje přehled o tom, jak kreslení pomocí <xref:System.Windows.Shapes.Shape> objekty.</span><span class="sxs-lookup"><span data-stu-id="e7dee-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="e7dee-104">A <xref:System.Windows.Shapes.Shape> je typ <xref:System.Windows.UIElement> , která umožňuje nakreslit obrazec na obrazovku.</span><span class="sxs-lookup"><span data-stu-id="e7dee-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="e7dee-105">Protože jsou prvky uživatelského rozhraní, <xref:System.Windows.Shapes.Shape> objekty mohou být použity uvnitř <xref:System.Windows.Controls.Panel> elementy a většina ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e7dee-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="e7dee-106">nabízí několik úrovní přístupu k grafické a vykreslovací služby.</span><span class="sxs-lookup"><span data-stu-id="e7dee-106">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="e7dee-107">V horní vrstvě <xref:System.Windows.Shapes.Shape> objekty jsou snadné použití a poskytují mnoho užitečných funkcí, jako je rozložení a zúčastnit se [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systém událostí.</span><span class="sxs-lookup"><span data-stu-id="e7dee-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  
  
  
<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="e7dee-108">Shape – objekty</span><span class="sxs-lookup"><span data-stu-id="e7dee-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="e7dee-109">poskytuje řadu připravených k použití <xref:System.Windows.Shapes.Shape> objekty.</span><span class="sxs-lookup"><span data-stu-id="e7dee-109">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="e7dee-110">Dědí všechny objekty obrazce <xref:System.Windows.Shapes.Shape> třídy.</span><span class="sxs-lookup"><span data-stu-id="e7dee-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="e7dee-111">K dispozici shape – objekty zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="e7dee-112"><xref:System.Windows.Shapes.Shape> objekty sdílejí společné následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e7dee-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
-   <span data-ttu-id="e7dee-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Popisuje, jak Vymalování obrysu obrazce.</span><span class="sxs-lookup"><span data-stu-id="e7dee-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
-   <span data-ttu-id="e7dee-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Popisuje tloušťku obrysu obrazce.</span><span class="sxs-lookup"><span data-stu-id="e7dee-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
-   <span data-ttu-id="e7dee-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Popisuje, jak je překreslit vnitřní část obrazce.</span><span class="sxs-lookup"><span data-stu-id="e7dee-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
-   <span data-ttu-id="e7dee-116">Vlastnosti dat k zadání souřadnic a vrcholy, měřeno v pixelech nezávislých na zařízení.</span><span class="sxs-lookup"><span data-stu-id="e7dee-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="e7dee-117">Protože jsou odvozeny z <xref:System.Windows.UIElement>, shape – objekty může být použit uvnitř panelů a většina ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="e7dee-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="e7dee-118"><xref:System.Windows.Controls.Canvas> Panel je obzvláště vhodný pro vytváření komplexních výkresů, protože podporuje absolutní pozici jeho podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="e7dee-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="e7dee-119"><xref:System.Windows.Shapes.Line> Třída umožňuje nakreslit čáru mezi dvěma body.</span><span class="sxs-lookup"><span data-stu-id="e7dee-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="e7dee-120">Následující příklad ukazuje několik způsobů, jak zadat řádek souřadnice a vlastností tahu.</span><span class="sxs-lookup"><span data-stu-id="e7dee-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="e7dee-121">Následující obrázek ukazuje vygenerované <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="e7dee-122">![Řádek obrázek](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="e7dee-122">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="e7dee-123">I když <xref:System.Windows.Shapes.Line> poskytuje třídy <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost nastavení nemá žádný vliv, protože <xref:System.Windows.Shapes.Line> nemá žádné oblasti.</span><span class="sxs-lookup"><span data-stu-id="e7dee-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="e7dee-124">Je jiné běžné obrazce <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="e7dee-125">Vytvoření <xref:System.Windows.Shapes.Ellipse> definováním obrazce <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e7dee-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="e7dee-126">Chcete-li nakreslit kruh, zadejte <xref:System.Windows.Shapes.Ellipse> jehož <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou hodnoty stejné.</span><span class="sxs-lookup"><span data-stu-id="e7dee-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="e7dee-127">Následující obrázek ukazuje příklad vykreslovaných <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="e7dee-128">![Obrázek Elipsa](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="e7dee-128">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="e7dee-129">Pomocí cesty a geometrie</span><span class="sxs-lookup"><span data-stu-id="e7dee-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="e7dee-130"><xref:System.Windows.Shapes.Path> Třída umožňuje kreslení křivek a obrazců složité.</span><span class="sxs-lookup"><span data-stu-id="e7dee-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="e7dee-131">Tyto křivky a obrazce se popisují pomocí <xref:System.Windows.Media.Geometry> objekty.</span><span class="sxs-lookup"><span data-stu-id="e7dee-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="e7dee-132">Použití <xref:System.Windows.Shapes.Path>, vytvoříte <xref:System.Windows.Media.Geometry> a použít ho nastavit <xref:System.Windows.Shapes.Path> objektu <xref:System.Windows.Shapes.Path.Data%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e7dee-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="e7dee-133">Existuje široká škála <xref:System.Windows.Media.Geometry> objekty lze vybírat.</span><span class="sxs-lookup"><span data-stu-id="e7dee-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="e7dee-134"><xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, A <xref:System.Windows.Media.EllipseGeometry> třídy popisují relativně jednoduché obrazce.</span><span class="sxs-lookup"><span data-stu-id="e7dee-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="e7dee-135">Pokud chcete vytvářet složitější tvary nebo vytvořit křivky, použijte <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="e7dee-136">PathGeometry – a PathSegments</span><span class="sxs-lookup"><span data-stu-id="e7dee-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="e7dee-137"><xref:System.Windows.Media.PathGeometry> objekty jsou složená z jednoho nebo více <xref:System.Windows.Media.PathFigure> objektů; každý <xref:System.Windows.Media.PathFigure> představuje různé "obrázek" nebo tvar.</span><span class="sxs-lookup"><span data-stu-id="e7dee-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="e7dee-138">Každý <xref:System.Windows.Media.PathFigure> je samotný sestávající z jednoho nebo více <xref:System.Windows.Media.PathSegment> objekty, každý představující připojených část obrázku nebo tvar.</span><span class="sxs-lookup"><span data-stu-id="e7dee-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="e7dee-139">Segment typy zahrnují následující: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, a <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="e7dee-140">V následujícím příkladu <xref:System.Windows.Shapes.Path> se používá k nakreslení kvadratické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="e7dee-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="e7dee-141">Následující obrázek ukazuje vykreslené tvaru.</span><span class="sxs-lookup"><span data-stu-id="e7dee-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="e7dee-142">![Cesta k obrázku](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="e7dee-142">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="e7dee-143">Další informace o <xref:System.Windows.Media.PathGeometry> a druhý <xref:System.Windows.Media.Geometry> třídy, najdete v článku [přehled geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e7dee-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="e7dee-144">XAML se používá zkratka syntaxe</span><span class="sxs-lookup"><span data-stu-id="e7dee-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="e7dee-145">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], můžete také použít speciální syntaxe zkrácený k popisu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="e7dee-146">V následujícím příkladu se používá zkrácený syntaxe nakreslit obrazec složité.</span><span class="sxs-lookup"><span data-stu-id="e7dee-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="e7dee-147">Následující obrázek ukazuje vykreslovaných <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="e7dee-148">![Cesta k obrázku](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="e7dee-148">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="e7dee-149"><xref:System.Windows.Shapes.Path.Data%2A> Atribut řetězec začíná příkazu "moveto" indikován M, který vytváří bod spuštění pro cestu ve službě souřadnicový systém <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="e7dee-150"><xref:System.Windows.Shapes.Path> data parametrů rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="e7dee-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="e7dee-151">Velké M označuje absolutní umístění pro nové aktuálního místa.</span><span class="sxs-lookup"><span data-stu-id="e7dee-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="e7dee-152">Malá písmena m by označoval relativních souřadnicích.</span><span class="sxs-lookup"><span data-stu-id="e7dee-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="e7dee-153">První segment je kubické Bézierovy křivky počínaje (100,200) a končící (400,175), vykresleného pomocí nich řídit body (100,25) a (400,350).</span><span class="sxs-lookup"><span data-stu-id="e7dee-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="e7dee-154">Tento segment je indikován příkaz jazyka C v <xref:System.Windows.Shapes.Path.Data%2A> atribut řetězců.</span><span class="sxs-lookup"><span data-stu-id="e7dee-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="e7dee-155">Znovu velké C určuje absolutní cestu. malá písmena c by označoval relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="e7dee-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="e7dee-156">Druhý segment začíná příkaz vodorovné absolutní "lineto" H, který určuje linií z předchozích podřízená cesta koncového bodu (400,175) do nového koncového bodu (280,175).</span><span class="sxs-lookup"><span data-stu-id="e7dee-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="e7dee-157">Protože je příkaz vodorovné "lineto", je hodnota zadaná *x*-koordinaci.</span><span class="sxs-lookup"><span data-stu-id="e7dee-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="e7dee-158">Úplná cesta syntaxi naleznete v tématu <xref:System.Windows.Shapes.Path.Data%2A> odkaz a [vytvoření tvaru použitím PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="e7dee-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="e7dee-159">Malování obrazců</span><span class="sxs-lookup"><span data-stu-id="e7dee-159">Painting Shapes</span></span>  
 <span data-ttu-id="e7dee-160"><xref:System.Windows.Media.Brush> objekty se používají k vyplnění obrazce <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.Fill%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="e7dee-161">V následujícím příkladu, stroke a výplň <xref:System.Windows.Shapes.Ellipse> jsou uvedeny.</span><span class="sxs-lookup"><span data-stu-id="e7dee-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="e7dee-162">Všimněte si, že platného vstupu pro vlastnosti štětce může být buď klíčové slovo nebo šestnáctková hodnota barvy.</span><span class="sxs-lookup"><span data-stu-id="e7dee-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="e7dee-163">Další informace o klíčových slovech dostupnou barvu najdete v tématu vlastnosti <xref:System.Windows.Media.Colors> třídy v <xref:System.Windows.Media> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e7dee-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="e7dee-164">Následující obrázek ukazuje vygenerované <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="e7dee-165">![Elipsa](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="e7dee-165">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="e7dee-166">Alternativně můžete syntax prvku vlastnosti explicitně vytvořit <xref:System.Windows.Media.SolidColorBrush> objektu k vyplnění obrazce plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="e7dee-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="e7dee-167">Následující obrázek znázorňuje vykreslené tvaru.</span><span class="sxs-lookup"><span data-stu-id="e7dee-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="e7dee-168">![Obrázek SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="e7dee-168">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="e7dee-169">Můžete také malovat stroke nebo výplň s přechody, obrázky, modely a více obrazce.</span><span class="sxs-lookup"><span data-stu-id="e7dee-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="e7dee-170">Další informace najdete v tématu [Malování plnými barvami a přechody přehled](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="e7dee-170">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="e7dee-171">Obrazce umožňující roztažení</span><span class="sxs-lookup"><span data-stu-id="e7dee-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="e7dee-172"><xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, A <xref:System.Windows.Shapes.Rectangle> mít všechny třídy <xref:System.Windows.Shapes.Shape.Stretch%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e7dee-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="e7dee-173">Tato vlastnost určuje, jak <xref:System.Windows.Shapes.Shape> je tak, aby vyplnil roztažený obsah na objekt (shape chcete kreslit) <xref:System.Windows.Shapes.Shape> místo rozložení objektu.</span><span class="sxs-lookup"><span data-stu-id="e7dee-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="e7dee-174">A <xref:System.Windows.Shapes.Shape> objektu rozložení místo představuje velikost místa <xref:System.Windows.Shapes.Shape> je přidělena systém rozložení, protože buď explicitní <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="e7dee-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="e7dee-175">Další informace o rozložení ve Windows Presentation Foundation, najdete v části [rozložení](../advanced/layout.md) Přehled.</span><span class="sxs-lookup"><span data-stu-id="e7dee-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="e7dee-176">Vlastnost Stretch má jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="e7dee-176">The Stretch property takes one of the following values:</span></span>  
  
-   <span data-ttu-id="e7dee-177"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Nejsou roztažený obsah objektu.</span><span class="sxs-lookup"><span data-stu-id="e7dee-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
-   <span data-ttu-id="e7dee-178"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Jsou roztažený obsah objektu tak, aby vyplnil místo jeho rozložení.</span><span class="sxs-lookup"><span data-stu-id="e7dee-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="e7dee-179">Poměr stran nezachová.</span><span class="sxs-lookup"><span data-stu-id="e7dee-179">Aspect ratio is not preserved.</span></span>  
  
-   <span data-ttu-id="e7dee-180"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Jsou roztažený obsah objektu tak, aby vyplnil místo jeho rozložení zachováním jeho původního poměru stran co nejvíc.</span><span class="sxs-lookup"><span data-stu-id="e7dee-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
-   <span data-ttu-id="e7dee-181"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Pro úplně naplnění jeho rozložení místo zachováním jeho původní poměr stran obrázku jsou roztažený obsah objektu.</span><span class="sxs-lookup"><span data-stu-id="e7dee-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="e7dee-182">Všimněte si, že když <xref:System.Windows.Shapes.Shape> jsou roztažený obsah objektu, <xref:System.Windows.Shapes.Shape> obrysu objektu vymalováním po roztažení.</span><span class="sxs-lookup"><span data-stu-id="e7dee-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="e7dee-183">V následujícím příkladu <xref:System.Windows.Shapes.Polygon> se používá k nakreslení velmi malý trojúhelník z (0,0) (0,1) na (1,1).</span><span class="sxs-lookup"><span data-stu-id="e7dee-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="e7dee-184"><xref:System.Windows.Shapes.Polygon> Objektu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou nastaveny na hodnotu 100, a jeho roztáhnout vlastnost je nastavena na hodnotu Fill.</span><span class="sxs-lookup"><span data-stu-id="e7dee-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="e7dee-185">V důsledku toho <xref:System.Windows.Shapes.Polygon> obsah objektu (trojúhelník) jsou roztažen tak, aby vyplnil místo větší.</span><span class="sxs-lookup"><span data-stu-id="e7dee-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="e7dee-186">Transformace obrazců</span><span class="sxs-lookup"><span data-stu-id="e7dee-186">Transforming Shapes</span></span>  
 <span data-ttu-id="e7dee-187"><xref:System.Windows.Media.Transform> Třída poskytuje způsob, jak transformace obrazců do dvourozměrné roviny.</span><span class="sxs-lookup"><span data-stu-id="e7dee-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="e7dee-188">Různé druhy transformace zahrnují otočení (<xref:System.Windows.Media.RotateTransform>), škálování (<xref:System.Windows.Media.ScaleTransform>), posun (<xref:System.Windows.Media.SkewTransform>) a překladu (<xref:System.Windows.Media.TranslateTransform>).</span><span class="sxs-lookup"><span data-stu-id="e7dee-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="e7dee-189">Běžné transformace má použít pro obrazec je otočení.</span><span class="sxs-lookup"><span data-stu-id="e7dee-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="e7dee-190">Otočíte tvar, vytvořit <xref:System.Windows.Media.RotateTransform> a určit jeho <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="e7dee-191"><xref:System.Windows.Media.RotateTransform.Angle%2A> 45 otočí element 45 stupňů doprava, kterým je úhel 90 otočí element 90 stupňů po směru hodinových ručiček, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="e7dee-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="e7dee-192">Nastavte <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> vlastnosti, pokud chcete řídicí bod o tom, které se otočí element.</span><span class="sxs-lookup"><span data-stu-id="e7dee-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="e7dee-193">Hodnoty těchto vlastností jsou vyjádřeny v souřadnicového prostoru element, který se má transformovat.</span><span class="sxs-lookup"><span data-stu-id="e7dee-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="e7dee-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula.</span><span class="sxs-lookup"><span data-stu-id="e7dee-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="e7dee-195">Nakonec se vztahují <xref:System.Windows.Media.RotateTransform> na prvek.</span><span class="sxs-lookup"><span data-stu-id="e7dee-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="e7dee-196">Pokud nechcete, aby transformací, která má být ovlivněn rozložení, nastavte obrazce <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e7dee-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="e7dee-197">V následujícím příkladu <xref:System.Windows.Media.RotateTransform> slouží k otáčet 45 stupňů obrazec o tvaru levého horního rohu (0; 0).</span><span class="sxs-lookup"><span data-stu-id="e7dee-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="e7dee-198">V následujícím příkladu jiný tvar je otočený 45 stupňů, ale tentokrát je otočený o bodu (25,50).</span><span class="sxs-lookup"><span data-stu-id="e7dee-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="e7dee-199">Na následujícím obrázku je výsledkem použití dvou transformací.</span><span class="sxs-lookup"><span data-stu-id="e7dee-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="e7dee-200">![45 stupňů rotace s různými středy](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="e7dee-200">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="e7dee-201">V předchozích příkladech byla použita jeden transformace každého objektu shape.</span><span class="sxs-lookup"><span data-stu-id="e7dee-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="e7dee-202">Použití několika transformací na tvar (nebo jiný prvek uživatelského rozhraní), použijte <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="e7dee-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7dee-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e7dee-203">See also</span></span>
- [<span data-ttu-id="e7dee-204">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="e7dee-204">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="e7dee-205">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="e7dee-205">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="e7dee-206">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="e7dee-206">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="e7dee-207">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="e7dee-207">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="e7dee-208">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="e7dee-208">Animation Overview</span></span>](animation-overview.md)
