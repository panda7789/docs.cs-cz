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
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="28457-102">Tvary a základní kresby v přehledu WPF</span><span class="sxs-lookup"><span data-stu-id="28457-102">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="28457-103">Toto téma poskytuje přehled o <xref:System.Windows.Shapes.Shape> tom, jak kreslit s objekty.</span><span class="sxs-lookup"><span data-stu-id="28457-103">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="28457-104">A <xref:System.Windows.Shapes.Shape> je <xref:System.Windows.UIElement> typ, který umožňuje nakreslit obrazec na obrazovku.</span><span class="sxs-lookup"><span data-stu-id="28457-104">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="28457-105">Vzhledem k tomu, <xref:System.Windows.Shapes.Shape> že se <xref:System.Windows.Controls.Panel> jedná o prvky uživatelského rozhraní, objekty lze použít uvnitř prvky a většinu ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="28457-105">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="28457-106">nabízí několik vrstev přístupu ke grafickým a vykreslovací službám.</span><span class="sxs-lookup"><span data-stu-id="28457-106">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="28457-107">V horní vrstvě <xref:System.Windows.Shapes.Shape> jsou objekty snadno použitelné a poskytují mnoho užitečných funkcí, jako je rozložení a účast v systému [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] událostí.</span><span class="sxs-lookup"><span data-stu-id="28457-107">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>
## <a name="shape-objects"></a><span data-ttu-id="28457-108">Objekty obrazce</span><span class="sxs-lookup"><span data-stu-id="28457-108">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="28457-109">poskytuje řadu objektů připravených <xref:System.Windows.Shapes.Shape> k použití.</span><span class="sxs-lookup"><span data-stu-id="28457-109">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="28457-110">Všechny objekty obrazce dědí z <xref:System.Windows.Shapes.Shape> třídy.</span><span class="sxs-lookup"><span data-stu-id="28457-110">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="28457-111">Mezi dostupné <xref:System.Windows.Shapes.Ellipse>objekty tvarů patří <xref:System.Windows.Shapes.Line>, , <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, a <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="28457-111">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="28457-112"><xref:System.Windows.Shapes.Shape>objekty sdílejí následující společné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="28457-112"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="28457-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Popisuje, jak je obrys obrazce malovaný.</span><span class="sxs-lookup"><span data-stu-id="28457-113"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="28457-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Popisuje tloušťku obrysu obrazce.</span><span class="sxs-lookup"><span data-stu-id="28457-114"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="28457-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Popisuje, jak je vnitřek tvaru malovaný.</span><span class="sxs-lookup"><span data-stu-id="28457-115"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="28457-116">Vlastnosti dat pro určení souřadnic a vrcholů, měřeno v pixelech nezávislých na zařízení.</span><span class="sxs-lookup"><span data-stu-id="28457-116">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="28457-117">Protože jsou <xref:System.Windows.UIElement>odvozeny z , objekty tvarů lze použít uvnitř panelů a většinu ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="28457-117">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="28457-118">Panel <xref:System.Windows.Controls.Canvas> je obzvláště dobrou volbou pro vytváření složitých výkresů, protože podporuje absolutní umístění podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="28457-118">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="28457-119">Třída <xref:System.Windows.Shapes.Line> umožňuje nakreslit čáru mezi dvěma body.</span><span class="sxs-lookup"><span data-stu-id="28457-119">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="28457-120">Následující příklad ukazuje několik způsobů, jak určit souřadnice čáry a vlastnosti tahu.</span><span class="sxs-lookup"><span data-stu-id="28457-120">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="28457-121">Následující obrázek znázorňuje vykreslenou <xref:System.Windows.Shapes.Line>.</span><span class="sxs-lookup"><span data-stu-id="28457-121">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="28457-122">![Obrázek čáry](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="28457-122">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="28457-123">Přestože <xref:System.Windows.Shapes.Line> třída poskytuje <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost, nastavení nemá žádný <xref:System.Windows.Shapes.Line> vliv, protože nemá žádnou oblast.</span><span class="sxs-lookup"><span data-stu-id="28457-123">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="28457-124">Dalším běžným <xref:System.Windows.Shapes.Ellipse>tvarem je .</span><span class="sxs-lookup"><span data-stu-id="28457-124">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="28457-125"><xref:System.Windows.Shapes.Ellipse> Vytvořte definováním vlastností <xref:System.Windows.FrameworkElement.Width%2A> obrazce a <xref:System.Windows.FrameworkElement.Height%2A> jeho vlastností.</span><span class="sxs-lookup"><span data-stu-id="28457-125">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="28457-126">Chcete-li nakreslit <xref:System.Windows.Shapes.Ellipse> kružnici, určete, jejichž <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> hodnoty jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="28457-126">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="28457-127">Následující obrázek znázorňuje příklad <xref:System.Windows.Shapes.Ellipse>vykresleného obrázku .</span><span class="sxs-lookup"><span data-stu-id="28457-127">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="28457-128">![Ilustrace elipsy](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="28457-128">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a><span data-ttu-id="28457-129">Použití cest a geometrií</span><span class="sxs-lookup"><span data-stu-id="28457-129">Using Paths and Geometries</span></span>  
 <span data-ttu-id="28457-130">Třída <xref:System.Windows.Shapes.Path> umožňuje kreslit křivky a složité tvary.</span><span class="sxs-lookup"><span data-stu-id="28457-130">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="28457-131">Tyto křivky a tvary <xref:System.Windows.Media.Geometry> jsou popsány pomocí objektů.</span><span class="sxs-lookup"><span data-stu-id="28457-131">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="28457-132">Chcete-li <xref:System.Windows.Shapes.Path>použít , <xref:System.Windows.Media.Geometry> vytvořte a <xref:System.Windows.Shapes.Path> použijte jej <xref:System.Windows.Shapes.Path.Data%2A> k nastavení vlastnosti objektu.</span><span class="sxs-lookup"><span data-stu-id="28457-132">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="28457-133">Existuje celá řada <xref:System.Windows.Media.Geometry> objektů z čeho vybírat.</span><span class="sxs-lookup"><span data-stu-id="28457-133">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="28457-134"><xref:System.Windows.Media.LineGeometry>Třídy <xref:System.Windows.Media.RectangleGeometry>, <xref:System.Windows.Media.EllipseGeometry> a popisují relativně jednoduché tvary.</span><span class="sxs-lookup"><span data-stu-id="28457-134">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="28457-135">Chcete-li vytvořit složitější tvary nebo <xref:System.Windows.Media.PathGeometry>vytvořit křivky, použijte .</span><span class="sxs-lookup"><span data-stu-id="28457-135">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="28457-136">PathGeometry a Segmenty cesty</span><span class="sxs-lookup"><span data-stu-id="28457-136">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="28457-137"><xref:System.Windows.Media.PathGeometry>objekty se skládají <xref:System.Windows.Media.PathFigure> z jednoho nebo více objektů; každý <xref:System.Windows.Media.PathFigure> představuje jiný "obrázek" nebo tvar.</span><span class="sxs-lookup"><span data-stu-id="28457-137"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="28457-138">Každý <xref:System.Windows.Media.PathFigure> z nich se skládá <xref:System.Windows.Media.PathSegment> z jednoho nebo více objektů, z nichž každý představuje připojenou část obrázku nebo tvaru.</span><span class="sxs-lookup"><span data-stu-id="28457-138">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="28457-139">Typy segmentů zahrnují <xref:System.Windows.Media.LineSegment> <xref:System.Windows.Media.BezierSegment>následující: <xref:System.Windows.Media.ArcSegment>, a .</span><span class="sxs-lookup"><span data-stu-id="28457-139">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="28457-140">V následujícím příkladu <xref:System.Windows.Shapes.Path> se a používá k nakreslení kvadratické Bezierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="28457-140">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="28457-141">Následující obrázek znázorňuje vykreslený obrazec.</span><span class="sxs-lookup"><span data-stu-id="28457-141">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="28457-142">![Ilustrace cesta](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="28457-142">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="28457-143">Další informace <xref:System.Windows.Media.PathGeometry> o ostatních <xref:System.Windows.Media.Geometry> třídách naleznete v tématu [Přehled geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="28457-143">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="28457-144">Zkrácená syntaxe XAML</span><span class="sxs-lookup"><span data-stu-id="28457-144">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="28457-145">V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]souboru můžete také použít speciální zkrácenou syntaxi k popisu <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="28457-145">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="28457-146">V následujícím příkladu se zkrácená syntaxe používá k nakreslení složitého tvaru.</span><span class="sxs-lookup"><span data-stu-id="28457-146">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="28457-147">Následující obrázek znázorňuje vykreslenou <xref:System.Windows.Shapes.Path>.</span><span class="sxs-lookup"><span data-stu-id="28457-147">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="28457-148">![Ilustrace cesta](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="28457-148">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="28457-149">Řetězec <xref:System.Windows.Shapes.Path.Data%2A> atributu začíná příkazem "moveto", označeným M, který vytváří počáteční bod pro cestu <xref:System.Windows.Controls.Canvas>v souřadnicovém systému .</span><span class="sxs-lookup"><span data-stu-id="28457-149">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="28457-150"><xref:System.Windows.Shapes.Path>parametry dat rozlišují malá a velká písmena.</span><span class="sxs-lookup"><span data-stu-id="28457-150"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="28457-151">Velké město M označuje absolutní umístění nového aktuálního bodu.</span><span class="sxs-lookup"><span data-stu-id="28457-151">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="28457-152">Malé písmeno m by znamenalo relativní souřadnice.</span><span class="sxs-lookup"><span data-stu-id="28457-152">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="28457-153">První segment je kubická Bezierova křivka začínající na (100 200) a končící na (400 175), nakreslená pomocí dvou kontrolních bodů (100 25) a (400 350).</span><span class="sxs-lookup"><span data-stu-id="28457-153">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="28457-154">Tento segment je označen příkazem <xref:System.Windows.Shapes.Path.Data%2A> C v řetězci atributu.</span><span class="sxs-lookup"><span data-stu-id="28457-154">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="28457-155">Opět platí, že kapitál C označuje absolutní cestu; malá písmena c by naznačovala relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="28457-155">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="28457-156">Druhý segment začíná absolutním vodorovným příkazem "lineto" H, který určuje čáru nakreslenou z koncového bodu předchozí podcesty (400 175) na nový koncový bod (280 175).</span><span class="sxs-lookup"><span data-stu-id="28457-156">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="28457-157">Vzhledem k tomu, že se jedná o horizontální příkaz "lineto", zadaná hodnota je souřadnice *x.*</span><span class="sxs-lookup"><span data-stu-id="28457-157">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="28457-158">Úplnou syntaxi cesty <xref:System.Windows.Shapes.Path.Data%2A> naleznete v odkazu a [vytvoření obrazce pomocí pathgeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="28457-158">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a><span data-ttu-id="28457-159">Obrazobrazové malby</span><span class="sxs-lookup"><span data-stu-id="28457-159">Painting Shapes</span></span>  
 <span data-ttu-id="28457-160"><xref:System.Windows.Media.Brush>objekty se používají k <xref:System.Windows.Shapes.Shape.Stroke%2A> malování <xref:System.Windows.Shapes.Shape.Fill%2A>tvaru a .</span><span class="sxs-lookup"><span data-stu-id="28457-160"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="28457-161">V následujícím příkladu <xref:System.Windows.Shapes.Ellipse> jsou určeny tah a výplň.</span><span class="sxs-lookup"><span data-stu-id="28457-161">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="28457-162">Všimněte si, že platný vstup pro vlastnosti stopy může být hodnota klíčového slova nebo šestnáctkové barvy.</span><span class="sxs-lookup"><span data-stu-id="28457-162">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="28457-163">Další informace o dostupných klíčových slovech barev naleznete v <xref:System.Windows.Media.Colors> vlastnostech třídy v oboru <xref:System.Windows.Media> názvů.</span><span class="sxs-lookup"><span data-stu-id="28457-163">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="28457-164">Následující obrázek znázorňuje vykreslenou <xref:System.Windows.Shapes.Ellipse>.</span><span class="sxs-lookup"><span data-stu-id="28457-164">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="28457-165">![Elipsu](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="28457-165">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="28457-166">Případně můžete použít syntaxi prvku vlastnosti <xref:System.Windows.Media.SolidColorBrush> k explicitnímu vytvoření objektu, který obrazec namaluje plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="28457-166">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="28457-167">Následující obrázek znázorňuje vykreslený obrazec.</span><span class="sxs-lookup"><span data-stu-id="28457-167">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="28457-168">![SolidColorBrush ilustrace](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="28457-168">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="28457-169">Můžete také malovat tah nebo výplň pomocí přechodů, obrazů, vzorků a dalších.</span><span class="sxs-lookup"><span data-stu-id="28457-169">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="28457-170">Další informace naleznete v tématu [Malování plnými barvami a přechody Přehled](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="28457-170">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a><span data-ttu-id="28457-171">Roztažitelné tvary</span><span class="sxs-lookup"><span data-stu-id="28457-171">Stretchable Shapes</span></span>  
 <span data-ttu-id="28457-172"><xref:System.Windows.Shapes.Line>Vlastnosti <xref:System.Windows.Shapes.Path> <xref:System.Windows.Shapes.Polygon>mají <xref:System.Windows.Shapes.Polyline>, <xref:System.Windows.Shapes.Rectangle> , , <xref:System.Windows.Shapes.Shape.Stretch%2A> , a třídy.</span><span class="sxs-lookup"><span data-stu-id="28457-172">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="28457-173">Tato vlastnost určuje, <xref:System.Windows.Shapes.Shape> jak je obsah objektu (tvar, který má <xref:System.Windows.Shapes.Shape> být nakreslen) roztažen tak, aby vyplnil prostor rozvržení objektu.</span><span class="sxs-lookup"><span data-stu-id="28457-173">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="28457-174">Prostor <xref:System.Windows.Shapes.Shape> rozložení objektu je velikost <xref:System.Windows.Shapes.Shape> místa, které je přiděleno systémem rozložení, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> z důvodu explicitního a nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> a <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení.</span><span class="sxs-lookup"><span data-stu-id="28457-174">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="28457-175">Další informace o rozložení v nadaci Windows Presentation Foundation najdete v [tématu Přehled rozložení.](../advanced/layout.md)</span><span class="sxs-lookup"><span data-stu-id="28457-175">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="28457-176">Stretch Vlastnost má jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="28457-176">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="28457-177"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Obsah objektu není roztažený.</span><span class="sxs-lookup"><span data-stu-id="28457-177"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="28457-178"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen tak, aby vyplnil prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="28457-178"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="28457-179">Poměr stran není zachován.</span><span class="sxs-lookup"><span data-stu-id="28457-179">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="28457-180"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Obsah objektu je co nejvíce roztažen tak, aby vyplnil prostor rozvržení při zachování původního poměru stran.</span><span class="sxs-lookup"><span data-stu-id="28457-180"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="28457-181"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen tak, aby zcela vyplnil prostor rozvržení při zachování původního poměru stran.</span><span class="sxs-lookup"><span data-stu-id="28457-181"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="28457-182">Všimněte si, <xref:System.Windows.Shapes.Shape> že když je obsah <xref:System.Windows.Shapes.Shape> objektu roztažený, obrys objektu je po roztažení vymalován.</span><span class="sxs-lookup"><span data-stu-id="28457-182">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="28457-183">V následujícím příkladu <xref:System.Windows.Shapes.Polygon> se a používá k nakreslení velmi malého trojúhelníku od (0,0) do (0,1) do (1,1).</span><span class="sxs-lookup"><span data-stu-id="28457-183">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="28457-184">Objekt <xref:System.Windows.Shapes.Polygon> je <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> jsou nastaveny na 100 a jeho stretch vlastnost je nastavena na Fill.</span><span class="sxs-lookup"><span data-stu-id="28457-184">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="28457-185">V důsledku toho <xref:System.Windows.Shapes.Polygon> je obsah objektu (trojúhelník) roztažen tak, aby vyplnil větší prostor.</span><span class="sxs-lookup"><span data-stu-id="28457-185">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="28457-186">Transformace obrazců</span><span class="sxs-lookup"><span data-stu-id="28457-186">Transforming Shapes</span></span>  
 <span data-ttu-id="28457-187">Třída <xref:System.Windows.Media.Transform> poskytuje prostředky k transformaci tvarů ve dvourozměrné rovině.</span><span class="sxs-lookup"><span data-stu-id="28457-187">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="28457-188">Mezi různé typy transformace<xref:System.Windows.Media.RotateTransform>patří otočení<xref:System.Windows.Media.ScaleTransform>(<xref:System.Windows.Media.SkewTransform>), měřítko<xref:System.Windows.Media.TranslateTransform>( ), zkosení ( ) a překlad ( ).</span><span class="sxs-lookup"><span data-stu-id="28457-188">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="28457-189">Běžnou transformací, která se má použít na obrazec, je otočení.</span><span class="sxs-lookup"><span data-stu-id="28457-189">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="28457-190">Chcete-li obrazec <xref:System.Windows.Media.RotateTransform> otočit, <xref:System.Windows.Media.RotateTransform.Angle%2A>vytvořte a určete jeho .</span><span class="sxs-lookup"><span data-stu-id="28457-190">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="28457-191">45 <xref:System.Windows.Media.RotateTransform.Angle%2A> otočí prvek o 45 stupňů ve směru hodinových ručiček; úhel 90 otočí prvek o 90 stupňů ve směru hodinových ručiček; a tak dále.</span><span class="sxs-lookup"><span data-stu-id="28457-191">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="28457-192">Nastavte <xref:System.Windows.Media.RotateTransform.CenterX%2A> vlastnosti a, <xref:System.Windows.Media.RotateTransform.CenterY%2A> pokud chcete řídit bod, o který je prvek otočen.</span><span class="sxs-lookup"><span data-stu-id="28457-192">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="28457-193">Tyto hodnoty vlastností jsou vyjádřeny v souřadnicovém prostoru prvku, který je transformován.</span><span class="sxs-lookup"><span data-stu-id="28457-193">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="28457-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A>a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula.</span><span class="sxs-lookup"><span data-stu-id="28457-194"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="28457-195">Nakonec použít <xref:System.Windows.Media.RotateTransform> prvek.</span><span class="sxs-lookup"><span data-stu-id="28457-195">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="28457-196">Pokud nechcete, aby transformace ovlivnila rozložení, nastavte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost obrazce.</span><span class="sxs-lookup"><span data-stu-id="28457-196">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="28457-197">V následujícím příkladu <xref:System.Windows.Media.RotateTransform> se a používá k otočení obrazce o 45 stupňů kolem levého horního rohu obrazce (0,0).</span><span class="sxs-lookup"><span data-stu-id="28457-197">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="28457-198">V dalším příkladu je jiný obrazec otočen o 45 stupňů, ale tentokrát se otočí kolem bodu (25,50).</span><span class="sxs-lookup"><span data-stu-id="28457-198">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="28457-199">Následující obrázek znázorňuje výsledky použití dvou transformací.</span><span class="sxs-lookup"><span data-stu-id="28457-199">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="28457-200">![Otočení o 45 stupňů s různými středovými body](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="28457-200">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="28457-201">V předchozích příkladech byla na každý objekt tvaru použita jedna transformace.</span><span class="sxs-lookup"><span data-stu-id="28457-201">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="28457-202">Chcete-li použít více transformací na obrazec (nebo jakýkoli jiný prvek rozhraní), použijte <xref:System.Windows.Media.TransformGroup>.</span><span class="sxs-lookup"><span data-stu-id="28457-202">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28457-203">Viz také</span><span class="sxs-lookup"><span data-stu-id="28457-203">See also</span></span>

- [<span data-ttu-id="28457-204">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="28457-204">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="28457-205">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="28457-205">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="28457-206">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="28457-206">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="28457-207">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="28457-207">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="28457-208">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="28457-208">Animation Overview</span></span>](animation-overview.md)
