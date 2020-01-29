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
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="49edc-102">Tvary a základní kresby v přehledu WPF</span><span class="sxs-lookup"><span data-stu-id="49edc-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="49edc-103">Toto téma poskytuje přehled o tom, jak kreslit pomocí <xref:System.Windows.Shapes.Shape> objektů.</span><span class="sxs-lookup"><span data-stu-id="49edc-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="49edc-104"><xref:System.Windows.Shapes.Shape> je typ <xref:System.Windows.UIElement>, který umožňuje nakreslit obrazec na obrazovku.</span><span class="sxs-lookup"><span data-stu-id="49edc-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="49edc-105">Vzhledem k tomu, že jsou prvky uživatelského rozhraní, <xref:System.Windows.Shapes.Shape> objekty lze použít uvnitř <xref:System.Windows.Controls.Panel> prvků a většiny ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="49edc-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <span data-ttu-id="49edc-106">nabízí několik vrstev přístupu ke grafikám a vykreslovacím službám.</span><span class="sxs-lookup"><span data-stu-id="49edc-106">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="49edc-107">V horní vrstvě <xref:System.Windows.Shapes.Shape> objekty snadno použít a poskytují mnoho užitečných funkcí, jako je například rozložení a účast v systému událostí [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="49edc-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>   
## <a name="shape-objects"></a><span data-ttu-id="49edc-108">Objekty obrazce</span><span class="sxs-lookup"><span data-stu-id="49edc-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <span data-ttu-id="49edc-109">poskytuje řadu <xref:System.Windows.Shapes.Shape> objektů připravených k použití.</span><span class="sxs-lookup"><span data-stu-id="49edc-109">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="49edc-110">Všechny objekty obrazce dědí z třídy <xref:System.Windows.Shapes.Shape>.</span><span class="sxs-lookup"><span data-stu-id="49edc-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="49edc-111">Dostupné objekty obrazce zahrnují <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>a <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="49edc-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="49edc-112"><xref:System.Windows.Shapes.Shape> objektů sdílí následující společné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="49edc-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="49edc-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: popisuje, jak je vykreslen Obrys obrazce.</span><span class="sxs-lookup"><span data-stu-id="49edc-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="49edc-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: popisuje tloušťku obrysu tvaru.</span><span class="sxs-lookup"><span data-stu-id="49edc-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="49edc-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: popisuje, jak se vykreslit vnitřní část obrazce.</span><span class="sxs-lookup"><span data-stu-id="49edc-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="49edc-116">Vlastnosti dat pro určení souřadnic a vrcholů měřených v pixelech nezávislých na zařízení.</span><span class="sxs-lookup"><span data-stu-id="49edc-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="49edc-117">Vzhledem k tomu, že jsou odvozeny od <xref:System.Windows.UIElement>, lze objekty obrazce použít uvnitř panelů a většiny ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="49edc-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="49edc-118"><xref:System.Windows.Controls.Canvas> panel je zvlášť dobrým výběrem pro vytváření složitých kreseb, protože podporuje absolutní umístění svých podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="49edc-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="49edc-119">Třída <xref:System.Windows.Shapes.Line> umožňuje nakreslit čáru mezi dvěma body.</span><span class="sxs-lookup"><span data-stu-id="49edc-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="49edc-120">Následující příklad ukazuje několik způsobů určení souřadnic řádků a vlastností tahu.</span><span class="sxs-lookup"><span data-stu-id="49edc-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="49edc-121">Následující obrázek znázorňuje vykreslený <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="49edc-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="49edc-122">![Čára – ilustrace](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="49edc-122">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="49edc-123">I když třída <xref:System.Windows.Shapes.Line> poskytuje vlastnost <xref:System.Windows.Shapes.Shape.Fill%2A>, nastavení nemá žádný vliv, protože <xref:System.Windows.Shapes.Line> nemá žádnou oblast.</span><span class="sxs-lookup"><span data-stu-id="49edc-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="49edc-124">Dalším běžným obrazcem je <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="49edc-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="49edc-125">Vytvořte <xref:System.Windows.Shapes.Ellipse> definováním vlastností <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> obrazce.</span><span class="sxs-lookup"><span data-stu-id="49edc-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="49edc-126">Chcete-li nakreslit kruh, určete <xref:System.Windows.Shapes.Ellipse>, jehož hodnoty <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="49edc-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="49edc-127">Následující obrázek ukazuje příklad vykreslené <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="49edc-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="49edc-128">![Elipsa – ilustrace](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="49edc-128">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>   
## <a name="using-paths-and-geometries"></a><span data-ttu-id="49edc-129">Používání cest a geometrií</span><span class="sxs-lookup"><span data-stu-id="49edc-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="49edc-130">Třída <xref:System.Windows.Shapes.Path> umožňuje kreslení křivek a složitých tvarů.</span><span class="sxs-lookup"><span data-stu-id="49edc-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="49edc-131">Tyto křivky a tvary jsou popsány pomocí <xref:System.Windows.Media.Geometry> objektů.</span><span class="sxs-lookup"><span data-stu-id="49edc-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="49edc-132">Chcete-li použít <xref:System.Windows.Shapes.Path>, vytvořte <xref:System.Windows.Media.Geometry> a použijte jej k nastavení vlastnosti <xref:System.Windows.Shapes.Path.Data%2A> objektu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="49edc-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="49edc-133">Existuje řada objektů <xref:System.Windows.Media.Geometry>, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="49edc-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="49edc-134">Třídy <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>a <xref:System.Windows.Media.EllipseGeometry> popisují relativně jednoduché tvary.</span><span class="sxs-lookup"><span data-stu-id="49edc-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="49edc-135">K vytvoření složitějších tvarů nebo vytváření křivek použijte <xref:System.Windows.Media.PathGeometry>.</span><span class="sxs-lookup"><span data-stu-id="49edc-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>   
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="49edc-136">PathGeometry a PathSegments</span><span class="sxs-lookup"><span data-stu-id="49edc-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="49edc-137">objekty <xref:System.Windows.Media.PathGeometry> se skládají z jednoho nebo více objektů <xref:System.Windows.Media.PathFigure>; Každý <xref:System.Windows.Media.PathFigure> představuje jiný obrázek nebo tvar.</span><span class="sxs-lookup"><span data-stu-id="49edc-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="49edc-138">Každý <xref:System.Windows.Media.PathFigure> se skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý představuje připojenou část obrázku nebo tvaru.</span><span class="sxs-lookup"><span data-stu-id="49edc-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="49edc-139">Typy segmentů zahrnují následující: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>a <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="49edc-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="49edc-140">V následujícím příkladu je použita <xref:System.Windows.Shapes.Path> k nakreslení kvadratické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="49edc-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="49edc-141">Vykreslený obrazec znázorňuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="49edc-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="49edc-142">![Ilustrace cesty](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="49edc-142">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="49edc-143">Další informace o <xref:System.Windows.Media.PathGeometry> a dalších třídách <xref:System.Windows.Media.Geometry> naleznete v [přehledu geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="49edc-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>   
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="49edc-144">Syntaxe XAML s zkratkou</span><span class="sxs-lookup"><span data-stu-id="49edc-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="49edc-145">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete k popisu <xref:System.Windows.Shapes.Path>použít také speciální zkrácenou syntaxi.</span><span class="sxs-lookup"><span data-stu-id="49edc-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="49edc-146">V následujícím příkladu je použita zkrácená syntaxe pro vykreslení složitého tvaru.</span><span class="sxs-lookup"><span data-stu-id="49edc-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"   
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="49edc-147">Následující obrázek znázorňuje vykreslený <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="49edc-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="49edc-148">![Ilustrace cesty](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="49edc-148">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="49edc-149">Řetězec atributu <xref:System.Windows.Shapes.Path.Data%2A> začíná příkazem "MoveTo", který je označen M, který vytváří počáteční bod pro cestu v souřadnicovém systému <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="49edc-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="49edc-150">parametry <xref:System.Windows.Shapes.Path> dat rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="49edc-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="49edc-151">Velké písmeno M označuje absolutní umístění pro nový aktuální bod.</span><span class="sxs-lookup"><span data-stu-id="49edc-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="49edc-152">Malé písmeno m značí relativní souřadnice.</span><span class="sxs-lookup"><span data-stu-id="49edc-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="49edc-153">První segment je krychle Bézierovy křivky, která začíná na (100 200) a končí (400 175), vykreslená pomocí dvou řídicích bodů (100, 25) a (400 350).</span><span class="sxs-lookup"><span data-stu-id="49edc-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="49edc-154">Tento segment je označen příkazem jazyka C v řetězci atributu <xref:System.Windows.Shapes.Path.Data%2A>.</span><span class="sxs-lookup"><span data-stu-id="49edc-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="49edc-155">Opět velké písmeno C označuje absolutní cestu; Malé písmeno c indikuje relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="49edc-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="49edc-156">Druhý segment začíná absolutní horizontální příkazem "LineTo" H, který určuje řádek nakreslený z předchozí koncového bodu dílčí cesty (400 175) do nového koncového bodu (280 175).</span><span class="sxs-lookup"><span data-stu-id="49edc-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="49edc-157">Vzhledem k tomu, že se jedná o horizontální příkaz "LineTo", zadaná hodnota je souřadnice *x*.</span><span class="sxs-lookup"><span data-stu-id="49edc-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="49edc-158">Úplnou syntaxi cesty najdete v odkazu na <xref:System.Windows.Shapes.Path.Data%2A> a [vytvoření tvaru pomocí PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="49edc-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>   
## <a name="painting-shapes"></a><span data-ttu-id="49edc-159">Vybarvení tvarů</span><span class="sxs-lookup"><span data-stu-id="49edc-159">Painting Shapes</span></span>  
 <span data-ttu-id="49edc-160"><xref:System.Windows.Media.Brush> objektů se používají k vykreslování <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.Fill%2A>obrazce.</span><span class="sxs-lookup"><span data-stu-id="49edc-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="49edc-161">V následujícím příkladu jsou zadány tahy a Fill <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="49edc-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="49edc-162">Všimněte si, že platný vstup pro vlastnosti štětce může být buď klíčové slovo, nebo hexadecimální hodnota barvy.</span><span class="sxs-lookup"><span data-stu-id="49edc-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="49edc-163">Další informace o dostupných barevných klíčových klíčích naleznete v tématu vlastnosti <xref:System.Windows.Media.Colors> třídy v oboru názvů <xref:System.Windows.Media>.</span><span class="sxs-lookup"><span data-stu-id="49edc-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="49edc-164">Následující obrázek znázorňuje vykreslený <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="49edc-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="49edc-165">![Elipsa](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="49edc-165">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="49edc-166">Alternativně můžete použít syntaxi elementu Property k explicitnímu vytvoření objektu <xref:System.Windows.Media.SolidColorBrush> k vykreslování tvaru plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="49edc-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="49edc-167">Následující ilustrace znázorňuje vykreslený obrazec.</span><span class="sxs-lookup"><span data-stu-id="49edc-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="49edc-168">![Obrázek SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="49edc-168">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="49edc-169">Můžete také malovat tahy nebo výplň obrazce pomocí přechodů, obrázků, vzorů a dalších.</span><span class="sxs-lookup"><span data-stu-id="49edc-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="49edc-170">Další informace najdete v tématu [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="49edc-170">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>   
## <a name="stretchable-shapes"></a><span data-ttu-id="49edc-171">Roztažené obrazce</span><span class="sxs-lookup"><span data-stu-id="49edc-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="49edc-172">Třídy <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>a <xref:System.Windows.Shapes.Rectangle> mají vlastnost <xref:System.Windows.Shapes.Shape.Stretch%2A>.</span><span class="sxs-lookup"><span data-stu-id="49edc-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="49edc-173">Tato vlastnost určuje, jak má být obsah objektu <xref:System.Windows.Shapes.Shape> (tvar, který má být vykreslen) roztažen tak, aby vyplnil prostor rozložení objektu <xref:System.Windows.Shapes.Shape>.</span><span class="sxs-lookup"><span data-stu-id="49edc-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="49edc-174">Prostor rozložení <xref:System.Windows.Shapes.Shape>ho objektu je množství místa, které <xref:System.Windows.Shapes.Shape> přiděluje systém rozložení, z důvodu explicitního <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A>ho nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="49edc-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="49edc-175">Další informace o rozložení v Windows Presentation Foundation najdete v tématu Přehled [rozložení](../advanced/layout.md) .</span><span class="sxs-lookup"><span data-stu-id="49edc-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="49edc-176">Vlastnost Stretch přijímá jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="49edc-176">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="49edc-177"><xref:System.Windows.Media.Stretch.None>: obsah objektu <xref:System.Windows.Shapes.Shape> se roztáhne.</span><span class="sxs-lookup"><span data-stu-id="49edc-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="49edc-178"><xref:System.Windows.Media.Stretch.Fill>: obsah objektu <xref:System.Windows.Shapes.Shape> je roztažen tak, aby vyplnil jeho prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="49edc-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="49edc-179">Poměr stran není zachován.</span><span class="sxs-lookup"><span data-stu-id="49edc-179">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="49edc-180"><xref:System.Windows.Media.Stretch.Uniform>: obsah <xref:System.Windows.Shapes.Shape> objektu se roztáhne co nejvíce, aby se vyplnil jeho prostor rozložení a přitom se zachovává jeho původní poměr stran.</span><span class="sxs-lookup"><span data-stu-id="49edc-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="49edc-181"><xref:System.Windows.Media.Stretch.UniformToFill>: obsah objektu <xref:System.Windows.Shapes.Shape> se roztáhne, aby se úplně vyplnil jeho prostor rozložení a přitom se zachovává jeho původní poměr stran.</span><span class="sxs-lookup"><span data-stu-id="49edc-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="49edc-182">Všimněte si, že při roztažení obsahu <xref:System.Windows.Shapes.Shape>ho objektu je obrys objektu <xref:System.Windows.Shapes.Shape> vykreslen po roztažení.</span><span class="sxs-lookup"><span data-stu-id="49edc-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="49edc-183">V následujícím příkladu se <xref:System.Windows.Shapes.Polygon> používá k nakreslení velmi malého trojúhelníku od (0, 0) do (0, 1) do (1, 1).</span><span class="sxs-lookup"><span data-stu-id="49edc-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="49edc-184"><xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> objektu <xref:System.Windows.Shapes.Polygon> jsou nastaveny na 100 a vlastnost Stretch je nastavená na Fill.</span><span class="sxs-lookup"><span data-stu-id="49edc-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="49edc-185">V důsledku toho je obsah objektu <xref:System.Windows.Shapes.Polygon> (trojúhelník) roztažen tak, aby vyplnil větší prostor.</span><span class="sxs-lookup"><span data-stu-id="49edc-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="49edc-186">Transformace obrazců</span><span class="sxs-lookup"><span data-stu-id="49edc-186">Transforming Shapes</span></span>  
 <span data-ttu-id="49edc-187">Třída <xref:System.Windows.Media.Transform> poskytuje prostředky pro transformaci tvarů v dvojrozměrné rovině.</span><span class="sxs-lookup"><span data-stu-id="49edc-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="49edc-188">Mezi různé typy transformace patří rotace (<xref:System.Windows.Media.RotateTransform>), Scale (<xref:System.Windows.Media.ScaleTransform>), zkosit (<xref:System.Windows.Media.SkewTransform>) a Translation (<xref:System.Windows.Media.TranslateTransform>).</span><span class="sxs-lookup"><span data-stu-id="49edc-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="49edc-189">Společná transformace, která se má použít na obrazec, je rotace.</span><span class="sxs-lookup"><span data-stu-id="49edc-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="49edc-190">Chcete-li otočit tvar, vytvořte <xref:System.Windows.Media.RotateTransform> a zadejte jeho <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span><span class="sxs-lookup"><span data-stu-id="49edc-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="49edc-191"><xref:System.Windows.Media.RotateTransform.Angle%2A> 45 otočí element 45 stupňů po směru hodinových ručiček. úhel 90 otočí element 90 stupňů po směru hodinových ručiček. a tak dále.</span><span class="sxs-lookup"><span data-stu-id="49edc-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="49edc-192">Nastavte vlastnosti <xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A>, pokud chcete určit, kde se má prvek otočit.</span><span class="sxs-lookup"><span data-stu-id="49edc-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="49edc-193">Tyto hodnoty vlastností se vyjadřují v souřadnicovém prostoru elementu, který se transformuje.</span><span class="sxs-lookup"><span data-stu-id="49edc-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="49edc-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula.</span><span class="sxs-lookup"><span data-stu-id="49edc-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="49edc-195">Nakonec použijte <xref:System.Windows.Media.RotateTransform> pro element.</span><span class="sxs-lookup"><span data-stu-id="49edc-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="49edc-196">Pokud nechcete, aby transformace ovlivnila rozložení, nastavte vlastnost <xref:System.Windows.UIElement.RenderTransform%2A> obrazce.</span><span class="sxs-lookup"><span data-stu-id="49edc-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="49edc-197">V následujícím příkladu se <xref:System.Windows.Media.RotateTransform> používá k otočení tvaru 45 stupňů kolem levého horního rohu obrazce (0, 0).</span><span class="sxs-lookup"><span data-stu-id="49edc-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="49edc-198">V dalším příkladu je další tvar otočený 45 stupňů, ale tentokrát se otáčí kolem bodu (25, 50).</span><span class="sxs-lookup"><span data-stu-id="49edc-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="49edc-199">Následující ilustrace znázorňuje výsledky použití dvou transformací.</span><span class="sxs-lookup"><span data-stu-id="49edc-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="49edc-200">![45 stupňů otočení s různými centry](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="49edc-200">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="49edc-201">V předchozích příkladech se u každého objektu Shape použila jedna transformace.</span><span class="sxs-lookup"><span data-stu-id="49edc-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="49edc-202">Chcete-li použít více transformací na tvar (nebo jakýkoli jiný prvek uživatelského rozhraní), použijte <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="49edc-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49edc-203">Viz také:</span><span class="sxs-lookup"><span data-stu-id="49edc-203">See also</span></span>

- [<span data-ttu-id="49edc-204">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="49edc-204">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="49edc-205">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="49edc-205">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="49edc-206">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="49edc-206">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="49edc-207">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="49edc-207">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="49edc-208">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="49edc-208">Animation Overview</span></span>](animation-overview.md)
