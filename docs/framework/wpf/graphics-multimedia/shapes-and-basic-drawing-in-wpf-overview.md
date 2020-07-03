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
# <a name="shapes-and-basic-drawing-in-wpf-overview"></a><span data-ttu-id="ca902-103">Tvary a základní kresby v přehledu WPF</span><span class="sxs-lookup"><span data-stu-id="ca902-103">Shapes and Basic Drawing in WPF Overview</span></span>
<span data-ttu-id="ca902-104">Toto téma poskytuje přehled o tom, jak kreslit s <xref:System.Windows.Shapes.Shape> objekty.</span><span class="sxs-lookup"><span data-stu-id="ca902-104">This topic gives an overview of how to draw with <xref:System.Windows.Shapes.Shape> objects.</span></span> <span data-ttu-id="ca902-105"><xref:System.Windows.Shapes.Shape>Je typ <xref:System.Windows.UIElement> , který umožňuje nakreslit obrazec na obrazovku.</span><span class="sxs-lookup"><span data-stu-id="ca902-105">A <xref:System.Windows.Shapes.Shape> is a type of <xref:System.Windows.UIElement> that enables you to draw a shape to the screen.</span></span> <span data-ttu-id="ca902-106">Vzhledem k tomu, že jsou prvky uživatelského rozhraní, <xref:System.Windows.Shapes.Shape> lze objekty použít uvnitř <xref:System.Windows.Controls.Panel> prvků a většiny ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ca902-106">Because they are UI elements, <xref:System.Windows.Shapes.Shape> objects can be used inside <xref:System.Windows.Controls.Panel> elements and most controls.</span></span>  
  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="ca902-107">nabízí několik vrstev přístupu ke grafikám a vykreslovacím službám.</span><span class="sxs-lookup"><span data-stu-id="ca902-107">offers several layers of access to graphics and rendering services.</span></span> <span data-ttu-id="ca902-108">V horní vrstvě se <xref:System.Windows.Shapes.Shape> objekty snadno používají a poskytují mnoho užitečných funkcí, jako je například rozložení a účast v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systému událostí.</span><span class="sxs-lookup"><span data-stu-id="ca902-108">At the top layer, <xref:System.Windows.Shapes.Shape> objects are easy to use and provide many useful features, such as layout and participation in the [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] event system.</span></span>  

<a name="shapes"></a>
## <a name="shape-objects"></a><span data-ttu-id="ca902-109">Objekty obrazce</span><span class="sxs-lookup"><span data-stu-id="ca902-109">Shape Objects</span></span>  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]<span data-ttu-id="ca902-110">poskytuje několik objektů připravených k použití <xref:System.Windows.Shapes.Shape> .</span><span class="sxs-lookup"><span data-stu-id="ca902-110">provides a number of ready-to-use <xref:System.Windows.Shapes.Shape> objects.</span></span>  <span data-ttu-id="ca902-111">Všechny objekty obrazce dědí z <xref:System.Windows.Shapes.Shape> třídy.</span><span class="sxs-lookup"><span data-stu-id="ca902-111">All shape objects inherit from the <xref:System.Windows.Shapes.Shape> class.</span></span> <span data-ttu-id="ca902-112">Dostupné objekty obrazce zahrnují <xref:System.Windows.Shapes.Ellipse> , <xref:System.Windows.Shapes.Line> , <xref:System.Windows.Shapes.Path> , <xref:System.Windows.Shapes.Polygon> , <xref:System.Windows.Shapes.Polyline> a <xref:System.Windows.Shapes.Rectangle> .</span><span class="sxs-lookup"><span data-stu-id="ca902-112">Available shape objects include <xref:System.Windows.Shapes.Ellipse>, <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="ca902-113"><xref:System.Windows.Shapes.Shape>objekty sdílejí následující společné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="ca902-113"><xref:System.Windows.Shapes.Shape> objects share the following common properties.</span></span>  
  
- <span data-ttu-id="ca902-114"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Popisuje, jak je vykreslen obrys tvaru.</span><span class="sxs-lookup"><span data-stu-id="ca902-114"><xref:System.Windows.Shapes.Shape.Stroke%2A>: Describes how the shape's outline is painted.</span></span>  
  
- <span data-ttu-id="ca902-115"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Popisuje tloušťku obrysu tvaru.</span><span class="sxs-lookup"><span data-stu-id="ca902-115"><xref:System.Windows.Shapes.Shape.StrokeThickness%2A>: Describes the thickness of the shape's outline.</span></span>  
  
- <span data-ttu-id="ca902-116"><xref:System.Windows.Shapes.Shape.Fill%2A>: Popisuje, jak je vykreslen vnitřní prvek obrazce.</span><span class="sxs-lookup"><span data-stu-id="ca902-116"><xref:System.Windows.Shapes.Shape.Fill%2A>: Describes how the interior of the shape is painted.</span></span>  
  
- <span data-ttu-id="ca902-117">Vlastnosti dat pro určení souřadnic a vrcholů měřených v pixelech nezávislých na zařízení.</span><span class="sxs-lookup"><span data-stu-id="ca902-117">Data properties to specify coordinates and vertices, measured in device-independent pixels.</span></span>  
  
 <span data-ttu-id="ca902-118">Vzhledem k tomu, že jsou odvozeny z <xref:System.Windows.UIElement> , lze použít objekty obrazce uvnitř panelů a většiny ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ca902-118">Because they derive from <xref:System.Windows.UIElement>, shape objects can be used inside panels and most controls.</span></span> <span data-ttu-id="ca902-119"><xref:System.Windows.Controls.Canvas>Panel je zvlášť dobrý volbou pro vytváření složitých kreseb, protože podporuje absolutní umístění svých podřízených objektů.</span><span class="sxs-lookup"><span data-stu-id="ca902-119">The <xref:System.Windows.Controls.Canvas> panel is a particularly good choice for creating complex drawings because it supports absolute positioning of its child objects.</span></span>  
  
 <span data-ttu-id="ca902-120"><xref:System.Windows.Shapes.Line>Třída umožňuje nakreslit čáru mezi dvěma body.</span><span class="sxs-lookup"><span data-stu-id="ca902-120">The <xref:System.Windows.Shapes.Line> class enables you to draw a line between two points.</span></span> <span data-ttu-id="ca902-121">Následující příklad ukazuje několik způsobů určení souřadnic řádků a vlastností tahu.</span><span class="sxs-lookup"><span data-stu-id="ca902-121">The following example shows several ways to specify line coordinates and stroke properties.</span></span>  
  
 [!code-xaml[drawingwithshapeelements#LineExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/DrawingWithShapeElements/CS/lineexample.xaml#lineexample1)]  
  
 [!code-cpp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/cpp/VS_Snippets_Wpf/ShapesProcedural/CPP/ShapesProcedural.cpp#shapesproceduralline)]
 [!code-csharp[shapesprocedural#ShapesProceduralLine](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapesProcedural/Csharp/ShapesProcedural.cs#shapesproceduralline)]
 [!code-vb[shapesprocedural#ShapesProceduralLine](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ShapesProcedural/VisualBasic/ShapesProceduralVB.vb#shapesproceduralline)]  
  
 <span data-ttu-id="ca902-122">Vykreslení znázorňuje následující obrázek <xref:System.Windows.Shapes.Line> .</span><span class="sxs-lookup"><span data-stu-id="ca902-122">The following image shows the rendered <xref:System.Windows.Shapes.Line>.</span></span>  
  
 <span data-ttu-id="ca902-123">![Čára – ilustrace](./media/shape-ovw-line2.gif "shape_ovw_line2")</span><span class="sxs-lookup"><span data-stu-id="ca902-123">![Line illustration](./media/shape-ovw-line2.gif "shape_ovw_line2")</span></span>  
  
 <span data-ttu-id="ca902-124">I když <xref:System.Windows.Shapes.Line> Třída poskytuje <xref:System.Windows.Shapes.Shape.Fill%2A> vlastnost, nastavení nemá žádný vliv, protože <xref:System.Windows.Shapes.Line> nemá žádnou oblast.</span><span class="sxs-lookup"><span data-stu-id="ca902-124">Although the <xref:System.Windows.Shapes.Line> class does provide a <xref:System.Windows.Shapes.Shape.Fill%2A> property, setting it has no effect because a <xref:System.Windows.Shapes.Line> has no area.</span></span>  
  
 <span data-ttu-id="ca902-125">Dalším běžným obrazcem je <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="ca902-125">Another common shape is the <xref:System.Windows.Shapes.Ellipse>.</span></span>  <span data-ttu-id="ca902-126">Vytvořte <xref:System.Windows.Shapes.Ellipse> pomocí definováním <xref:System.Windows.FrameworkElement.Width%2A> vlastností a vlastností obrazce <xref:System.Windows.FrameworkElement.Height%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca902-126">Create an <xref:System.Windows.Shapes.Ellipse> by defining the shape's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties.</span></span> <span data-ttu-id="ca902-127">Chcete-li nakreslit kruh, zadejte, <xref:System.Windows.Shapes.Ellipse> jejichž <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> hodnoty a jsou stejné.</span><span class="sxs-lookup"><span data-stu-id="ca902-127">To draw a circle, specify an <xref:System.Windows.Shapes.Ellipse> whose <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> values are equal.</span></span>  
  
 [!code-xaml[ShapeOverviews#ShapesOVW1](~/samples/snippets/csharp/VS_Snippets_Wpf/ShapeOverviews/CS/Window1.xaml#shapesovw1)]  
  
 [!code-csharp[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/CSharp/SetBackgroundColorOfShapeExample.cs#setbackgroundcolorofshapecodeexamplewholepage)]
 [!code-vb[brushesmiscsnippets_procedural_snip#SetBackgroundColorOfShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesMiscSnippets_procedural_snip/visualbasic/setbackgroundcolorofshapeexample.vb#setbackgroundcolorofshapecodeexamplewholepage)]  
  
 <span data-ttu-id="ca902-128">Následující obrázek ukazuje příklad vykreslené <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="ca902-128">The following image shows an example of a rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="ca902-129">![Elipsa – ilustrace](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span><span class="sxs-lookup"><span data-stu-id="ca902-129">![Ellipse illustration](./media/shape-ovw-ellipse2.png "shape_ovw_ellipse2")</span></span>  
  
<a name="paths"></a>
## <a name="using-paths-and-geometries"></a><span data-ttu-id="ca902-130">Používání cest a geometrií</span><span class="sxs-lookup"><span data-stu-id="ca902-130">Using Paths and Geometries</span></span>  
 <span data-ttu-id="ca902-131"><xref:System.Windows.Shapes.Path>Třída umožňuje nakreslit křivky a složité tvary.</span><span class="sxs-lookup"><span data-stu-id="ca902-131">The <xref:System.Windows.Shapes.Path> class enables you to draw curves and complex shapes.</span></span> <span data-ttu-id="ca902-132">Tyto křivky a tvary jsou popsány pomocí <xref:System.Windows.Media.Geometry> objektů.</span><span class="sxs-lookup"><span data-stu-id="ca902-132">These curves and shapes are described using <xref:System.Windows.Media.Geometry> objects.</span></span> <span data-ttu-id="ca902-133">Chcete-li použít <xref:System.Windows.Shapes.Path> , vytvoříte <xref:System.Windows.Media.Geometry> a použijete jej k nastavení <xref:System.Windows.Shapes.Path> vlastnosti objektu <xref:System.Windows.Shapes.Path.Data%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca902-133">To use a <xref:System.Windows.Shapes.Path>, you create a <xref:System.Windows.Media.Geometry> and use it to set the <xref:System.Windows.Shapes.Path> object's <xref:System.Windows.Shapes.Path.Data%2A> property.</span></span>  
  
 <span data-ttu-id="ca902-134">Existuje řada <xref:System.Windows.Media.Geometry> objektů, ze kterých si můžete vybrat.</span><span class="sxs-lookup"><span data-stu-id="ca902-134">There are a variety of <xref:System.Windows.Media.Geometry> objects to choose from.</span></span> <span data-ttu-id="ca902-135"><xref:System.Windows.Media.LineGeometry>Třídy, <xref:System.Windows.Media.RectangleGeometry> a <xref:System.Windows.Media.EllipseGeometry> popisují relativně jednoduché tvary.</span><span class="sxs-lookup"><span data-stu-id="ca902-135">The <xref:System.Windows.Media.LineGeometry>, <xref:System.Windows.Media.RectangleGeometry>, and <xref:System.Windows.Media.EllipseGeometry> classes describe relatively simple shapes.</span></span> <span data-ttu-id="ca902-136">Chcete-li vytvořit složitější tvary nebo vytvořit křivky, použijte <xref:System.Windows.Media.PathGeometry> .</span><span class="sxs-lookup"><span data-stu-id="ca902-136">To create more complex shapes or create curves, use a <xref:System.Windows.Media.PathGeometry>.</span></span>  
  
<a name="pathgeometry"></a>
### <a name="pathgeometry-and-pathsegments"></a><span data-ttu-id="ca902-137">PathGeometry a PathSegments</span><span class="sxs-lookup"><span data-stu-id="ca902-137">PathGeometry and PathSegments</span></span>  
 <span data-ttu-id="ca902-138"><xref:System.Windows.Media.PathGeometry>objekty se skládají z jednoho nebo více <xref:System.Windows.Media.PathFigure> objektů; každá <xref:System.Windows.Media.PathFigure> představuje jiný "obrázek" nebo tvar.</span><span class="sxs-lookup"><span data-stu-id="ca902-138"><xref:System.Windows.Media.PathGeometry> objects are comprised of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="ca902-139">Každá <xref:System.Windows.Media.PathFigure> z nich se skládá z jednoho nebo více <xref:System.Windows.Media.PathSegment> objektů, z nichž každý představuje připojenou část obrázku nebo tvaru.</span><span class="sxs-lookup"><span data-stu-id="ca902-139">Each <xref:System.Windows.Media.PathFigure> is itself comprised of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="ca902-140">Typy segmentů zahrnují následující: <xref:System.Windows.Media.LineSegment> , <xref:System.Windows.Media.BezierSegment> , a <xref:System.Windows.Media.ArcSegment> .</span><span class="sxs-lookup"><span data-stu-id="ca902-140">Segment types include the following: <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.BezierSegment>, and <xref:System.Windows.Media.ArcSegment>.</span></span>  
  
 <span data-ttu-id="ca902-141">V následujícím příkladu <xref:System.Windows.Shapes.Path> je použit k nakreslení kvadratické Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="ca902-141">In the following example, a <xref:System.Windows.Shapes.Path> is used to draw a quadratic Bezier curve.</span></span>  
  
 [!code-xaml[geometrysample#34](~/samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#34)]  
  
 <span data-ttu-id="ca902-142">Vykreslený obrazec znázorňuje následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="ca902-142">The following image shows the rendered shape.</span></span>  
  
 <span data-ttu-id="ca902-143">![Ilustrace cesty](./media/shape-ovw-path2.gif "shape_ovw_path2")</span><span class="sxs-lookup"><span data-stu-id="ca902-143">![Path illustration](./media/shape-ovw-path2.gif "shape_ovw_path2")</span></span>  
  
 <span data-ttu-id="ca902-144">Další informace o <xref:System.Windows.Media.PathGeometry> a dalších <xref:System.Windows.Media.Geometry> třídách naleznete v [přehledu geometrie](geometry-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ca902-144">For more information about <xref:System.Windows.Media.PathGeometry> and the other <xref:System.Windows.Media.Geometry> classes, see the [Geometry Overview](geometry-overview.md).</span></span>  
  
<a name="pathdatastring"></a>
### <a name="xaml-abbreviated-syntax"></a><span data-ttu-id="ca902-145">Syntaxe XAML s zkratkou</span><span class="sxs-lookup"><span data-stu-id="ca902-145">XAML Abbreviated Syntax</span></span>  
 <span data-ttu-id="ca902-146">V aplikaci [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] můžete použít také speciální zkrácenou syntaxi k popisu <xref:System.Windows.Shapes.Path> .</span><span class="sxs-lookup"><span data-stu-id="ca902-146">In [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], you may also use a special abbreviated syntax to describe a <xref:System.Windows.Shapes.Path>.</span></span> <span data-ttu-id="ca902-147">V následujícím příkladu je použita zkrácená syntaxe pro vykreslení složitého tvaru.</span><span class="sxs-lookup"><span data-stu-id="ca902-147">In the following example, abbreviated syntax is used to draw a complex shape.</span></span>  
  
```xaml  
      <Path Stroke="DarkGoldenRod" StrokeThickness="3"
Data="M 100,200 C 100,25 400,350 400,175 H 280" />  
```  
  
 <span data-ttu-id="ca902-148">Následující obrázek znázorňuje vykreslený <xref:System.Windows.Shapes.Path> .</span><span class="sxs-lookup"><span data-stu-id="ca902-148">The following image shows a rendered <xref:System.Windows.Shapes.Path>.</span></span>  
  
 <span data-ttu-id="ca902-149">![Ilustrace cesty](./media/shape-ovw-path.PNG "shape_ovw_path")</span><span class="sxs-lookup"><span data-stu-id="ca902-149">![Path illustration](./media/shape-ovw-path.PNG "shape_ovw_path")</span></span>  
  
 <span data-ttu-id="ca902-150"><xref:System.Windows.Shapes.Path.Data%2A>Řetězec atributu začíná příkazem "MoveTo", který je označen M, který vytváří počáteční bod pro cestu v souřadnicovém systému <xref:System.Windows.Controls.Canvas> .</span><span class="sxs-lookup"><span data-stu-id="ca902-150">The <xref:System.Windows.Shapes.Path.Data%2A> attribute string begins with the "moveto" command, indicated by M, which establishes a start point for the path in the coordinate system of the <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="ca902-151"><xref:System.Windows.Shapes.Path>v parametrech dat se rozlišují velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="ca902-151"><xref:System.Windows.Shapes.Path> data parameters are case-sensitive.</span></span> <span data-ttu-id="ca902-152">Velké písmeno M označuje absolutní umístění pro nový aktuální bod.</span><span class="sxs-lookup"><span data-stu-id="ca902-152">The capital M indicates an absolute location for the new current point.</span></span> <span data-ttu-id="ca902-153">Malé písmeno m značí relativní souřadnice.</span><span class="sxs-lookup"><span data-stu-id="ca902-153">A lowercase m would indicate relative coordinates.</span></span> <span data-ttu-id="ca902-154">První segment je krychle Bézierovy křivky, která začíná na (100 200) a končí (400 175), vykreslená pomocí dvou řídicích bodů (100, 25) a (400 350).</span><span class="sxs-lookup"><span data-stu-id="ca902-154">The first segment is a cubic Bezier curve beginning at (100,200) and ending at (400,175), drawn using the two control points (100,25) and (400,350).</span></span> <span data-ttu-id="ca902-155">Tento segment je označen příkazem jazyka C v <xref:System.Windows.Shapes.Path.Data%2A> řetězci atributu.</span><span class="sxs-lookup"><span data-stu-id="ca902-155">This segment is indicated by the C command in the <xref:System.Windows.Shapes.Path.Data%2A> attribute string.</span></span> <span data-ttu-id="ca902-156">Opět velké písmeno C označuje absolutní cestu; Malé písmeno c indikuje relativní cestu.</span><span class="sxs-lookup"><span data-stu-id="ca902-156">Again, the capital C indicates an absolute path; the lowercase c would indicate a relative path.</span></span>  
  
 <span data-ttu-id="ca902-157">Druhý segment začíná absolutní horizontální příkazem "LineTo" H, který určuje řádek nakreslený z předchozí koncového bodu dílčí cesty (400 175) do nového koncového bodu (280 175).</span><span class="sxs-lookup"><span data-stu-id="ca902-157">The second segment begins with an absolute horizontal "lineto" command H, which specifies a line drawn from the preceding subpath's endpoint (400,175) to a new endpoint (280,175).</span></span> <span data-ttu-id="ca902-158">Vzhledem k tomu, že se jedná o horizontální příkaz "LineTo", zadaná hodnota je souřadnice *x*.</span><span class="sxs-lookup"><span data-stu-id="ca902-158">Because it is a horizontal "lineto" command, the value specified is an *x*-coordinate.</span></span>  
  
 <span data-ttu-id="ca902-159">Úplnou syntaxi cesty naleznete v <xref:System.Windows.Shapes.Path.Data%2A> odkazu a [vytvoření tvaru pomocí PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span><span class="sxs-lookup"><span data-stu-id="ca902-159">For the complete path syntax, see the <xref:System.Windows.Shapes.Path.Data%2A> reference and [Create a Shape by Using a PathGeometry](how-to-create-a-shape-by-using-a-pathgeometry.md).</span></span>  
  
<a name="fillpaint"></a>
## <a name="painting-shapes"></a><span data-ttu-id="ca902-160">Vybarvení tvarů</span><span class="sxs-lookup"><span data-stu-id="ca902-160">Painting Shapes</span></span>  
 <span data-ttu-id="ca902-161"><xref:System.Windows.Media.Brush>objekty slouží k malování <xref:System.Windows.Shapes.Shape.Stroke%2A> a <xref:System.Windows.Shapes.Shape.Fill%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca902-161"><xref:System.Windows.Media.Brush> objects are used to paint a shape's <xref:System.Windows.Shapes.Shape.Stroke%2A> and <xref:System.Windows.Shapes.Shape.Fill%2A>.</span></span> <span data-ttu-id="ca902-162">V následujícím příkladu je zadán tah a výplň <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="ca902-162">In the following example, the stroke and fill of an <xref:System.Windows.Shapes.Ellipse> are specified.</span></span> <span data-ttu-id="ca902-163">Všimněte si, že platný vstup pro vlastnosti štětce může být buď klíčové slovo, nebo hexadecimální hodnota barvy.</span><span class="sxs-lookup"><span data-stu-id="ca902-163">Note that valid input for brush properties can be either a keyword or hexadecimal color value.</span></span> <span data-ttu-id="ca902-164">Další informace o dostupných barevných klíčových klíčích naleznete v tématu vlastnosti <xref:System.Windows.Media.Colors> třídy v <xref:System.Windows.Media> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="ca902-164">For more information about available color keywords, see properties of the <xref:System.Windows.Media.Colors> class in the <xref:System.Windows.Media> namespace.</span></span>  
  
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
  
 <span data-ttu-id="ca902-165">Vykreslení znázorňuje následující obrázek <xref:System.Windows.Shapes.Ellipse> .</span><span class="sxs-lookup"><span data-stu-id="ca902-165">The following image shows the rendered <xref:System.Windows.Shapes.Ellipse>.</span></span>  
  
 <span data-ttu-id="ca902-166">![Elipsa](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span><span class="sxs-lookup"><span data-stu-id="ca902-166">![An ellipse](./media/shape-ovw-ellipsefill.PNG "shape_ovw_ellipsefill")</span></span>  
  
 <span data-ttu-id="ca902-167">Alternativně můžete použít syntaxi elementu vlastnosti k explicitnímu vytvoření <xref:System.Windows.Media.SolidColorBrush> objektu pro malování tvaru plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="ca902-167">Alternatively, you can use property element syntax to explicitly create a <xref:System.Windows.Media.SolidColorBrush> object to paint the shape with a solid color.</span></span>  
  
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
  
 <span data-ttu-id="ca902-168">Následující ilustrace znázorňuje vykreslený obrazec.</span><span class="sxs-lookup"><span data-stu-id="ca902-168">The following illustration shows the rendered shape.</span></span>  
  
 <span data-ttu-id="ca902-169">![Obrázek SolidColorBrush](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span><span class="sxs-lookup"><span data-stu-id="ca902-169">![SolidColorBrush illustration](./media/shape-ovw-solidcolorbrush.PNG "shape_ovw_solidcolorbrush")</span></span>  
  
 <span data-ttu-id="ca902-170">Můžete také malovat tahy nebo výplň obrazce pomocí přechodů, obrázků, vzorů a dalších.</span><span class="sxs-lookup"><span data-stu-id="ca902-170">You can also paint a shape's stroke or fill with gradients, images, patterns, and more.</span></span> <span data-ttu-id="ca902-171">Další informace najdete v tématu [Přehled malování plnými barvami a přechody](painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ca902-171">For more information, see the [Painting with Solid Colors and Gradients Overview](painting-with-solid-colors-and-gradients-overview.md).</span></span>  
  
<a name="stretchableshapessection"></a>
## <a name="stretchable-shapes"></a><span data-ttu-id="ca902-172">Roztažené obrazce</span><span class="sxs-lookup"><span data-stu-id="ca902-172">Stretchable Shapes</span></span>  
 <span data-ttu-id="ca902-173"><xref:System.Windows.Shapes.Line> <xref:System.Windows.Shapes.Path> Všechny třídy,,, <xref:System.Windows.Shapes.Polygon> <xref:System.Windows.Shapes.Polyline> a <xref:System.Windows.Shapes.Rectangle> mají <xref:System.Windows.Shapes.Shape.Stretch%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ca902-173">The <xref:System.Windows.Shapes.Line>, <xref:System.Windows.Shapes.Path>, <xref:System.Windows.Shapes.Polygon>, <xref:System.Windows.Shapes.Polyline>, and <xref:System.Windows.Shapes.Rectangle> classes all have a <xref:System.Windows.Shapes.Shape.Stretch%2A> property.</span></span> <span data-ttu-id="ca902-174">Tato vlastnost určuje, jak <xref:System.Windows.Shapes.Shape> je obsah objektu (tvar, který má být vykreslen) roztažen tak, aby vyplnil <xref:System.Windows.Shapes.Shape> prostor rozložení objektu.</span><span class="sxs-lookup"><span data-stu-id="ca902-174">This property determines how a <xref:System.Windows.Shapes.Shape> object's contents (the shape to be drawn) is stretched to fill the <xref:System.Windows.Shapes.Shape> object's layout space.</span></span> <span data-ttu-id="ca902-175"><xref:System.Windows.Shapes.Shape>Prostor rozložení objektu je množství místa, které <xref:System.Windows.Shapes.Shape> je přiděleno systémem rozložení, z důvodu explicitního <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> nastavení nebo z důvodu jeho <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> nastavení a.</span><span class="sxs-lookup"><span data-stu-id="ca902-175">A <xref:System.Windows.Shapes.Shape> object's layout space is the amount of space the <xref:System.Windows.Shapes.Shape> is allocated by the layout system, because of either an explicit <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> setting or because of its <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> and <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> settings.</span></span> <span data-ttu-id="ca902-176">Další informace o rozložení v Windows Presentation Foundation najdete v tématu Přehled [rozložení](../advanced/layout.md) .</span><span class="sxs-lookup"><span data-stu-id="ca902-176">For additional information on layout in Windows Presentation Foundation, see [Layout](../advanced/layout.md) overview.</span></span>  
  
 <span data-ttu-id="ca902-177">Vlastnost Stretch přijímá jednu z následujících hodnot:</span><span class="sxs-lookup"><span data-stu-id="ca902-177">The Stretch property takes one of the following values:</span></span>  
  
- <span data-ttu-id="ca902-178"><xref:System.Windows.Media.Stretch.None>: <xref:System.Windows.Shapes.Shape> Obsah objektu není roztažen.</span><span class="sxs-lookup"><span data-stu-id="ca902-178"><xref:System.Windows.Media.Stretch.None>: The <xref:System.Windows.Shapes.Shape> object's contents are not stretched.</span></span>  
  
- <span data-ttu-id="ca902-179"><xref:System.Windows.Media.Stretch.Fill>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen tak, aby vyplnil jeho prostor rozložení.</span><span class="sxs-lookup"><span data-stu-id="ca902-179"><xref:System.Windows.Media.Stretch.Fill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to fill its layout space.</span></span>  <span data-ttu-id="ca902-180">Poměr stran není zachován.</span><span class="sxs-lookup"><span data-stu-id="ca902-180">Aspect ratio is not preserved.</span></span>  
  
- <span data-ttu-id="ca902-181"><xref:System.Windows.Media.Stretch.Uniform>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen co nejvíce, aby bylo možné vyplnit jeho prostor rozložení a přitom zachovat jeho původní poměr stran.</span><span class="sxs-lookup"><span data-stu-id="ca902-181"><xref:System.Windows.Media.Stretch.Uniform>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched as much as possible to fill its layout space while preserving its original aspect ratio.</span></span>  
  
- <span data-ttu-id="ca902-182"><xref:System.Windows.Media.Stretch.UniformToFill>: <xref:System.Windows.Shapes.Shape> Obsah objektu je roztažen tak, aby zcela vyplnil své místo rozložení při zachování původního poměru stran.</span><span class="sxs-lookup"><span data-stu-id="ca902-182"><xref:System.Windows.Media.Stretch.UniformToFill>: The <xref:System.Windows.Shapes.Shape> object's contents are stretched to completely fill its layout space while preserving its original aspect ratio.</span></span>  
  
 <span data-ttu-id="ca902-183">Všimněte si, že při <xref:System.Windows.Shapes.Shape> roztažení obsahu objektu <xref:System.Windows.Shapes.Shape> je obrys objektu vykreslen po roztažení.</span><span class="sxs-lookup"><span data-stu-id="ca902-183">Note that, when a <xref:System.Windows.Shapes.Shape> object's contents are stretched, the <xref:System.Windows.Shapes.Shape> object's outline is painted after the stretching.</span></span>  
  
 <span data-ttu-id="ca902-184">V následujícím příkladu <xref:System.Windows.Shapes.Polygon> se používá k nakreslení velmi malého trojúhelníku od (0, 0) do (0, 1) do (1, 1).</span><span class="sxs-lookup"><span data-stu-id="ca902-184">In the following example, a <xref:System.Windows.Shapes.Polygon> is used to draw a very small triangle from (0,0) to (0,1) to (1,1).</span></span> <span data-ttu-id="ca902-185"><xref:System.Windows.Shapes.Polygon>Objekt <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> je nastaven na 100 a jeho vlastnost Stretch je nastavena na hodnotu Fill.</span><span class="sxs-lookup"><span data-stu-id="ca902-185">The <xref:System.Windows.Shapes.Polygon> object's <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> are set to 100, and its stretch property is set to Fill.</span></span> <span data-ttu-id="ca902-186">V důsledku toho je <xref:System.Windows.Shapes.Polygon> obsah objektu (trojúhelník) roztažen tak, aby vyplnil větší prostor.</span><span class="sxs-lookup"><span data-stu-id="ca902-186">As a result, the <xref:System.Windows.Shapes.Polygon> object's contents (the triangle) are stretched to fill the larger space.</span></span>  
  
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
## <a name="transforming-shapes"></a><span data-ttu-id="ca902-187">Transformace obrazců</span><span class="sxs-lookup"><span data-stu-id="ca902-187">Transforming Shapes</span></span>  
 <span data-ttu-id="ca902-188"><xref:System.Windows.Media.Transform>Třída poskytuje prostředky pro transformaci tvarů v dvourozměrné rovině.</span><span class="sxs-lookup"><span data-stu-id="ca902-188">The <xref:System.Windows.Media.Transform> class provides the means to transform shapes in a two-dimensional plane.</span></span>  <span data-ttu-id="ca902-189">Mezi různé typy transformace patří rotace ( <xref:System.Windows.Media.RotateTransform> ), Scale ( <xref:System.Windows.Media.ScaleTransform> ), zkosit ( <xref:System.Windows.Media.SkewTransform> ) a Translation ( <xref:System.Windows.Media.TranslateTransform> ).</span><span class="sxs-lookup"><span data-stu-id="ca902-189">The different types of transformation include rotation (<xref:System.Windows.Media.RotateTransform>), scale (<xref:System.Windows.Media.ScaleTransform>), skew (<xref:System.Windows.Media.SkewTransform>), and translation (<xref:System.Windows.Media.TranslateTransform>).</span></span>  
  
 <span data-ttu-id="ca902-190">Společná transformace, která se má použít na obrazec, je rotace.</span><span class="sxs-lookup"><span data-stu-id="ca902-190">A common transform to apply to a shape is a rotation.</span></span>  <span data-ttu-id="ca902-191">Chcete-li otočit tvar, vytvořte <xref:System.Windows.Media.RotateTransform> a zadejte jeho <xref:System.Windows.Media.RotateTransform.Angle%2A> .</span><span class="sxs-lookup"><span data-stu-id="ca902-191">To rotate a shape, create a <xref:System.Windows.Media.RotateTransform> and specify its <xref:System.Windows.Media.RotateTransform.Angle%2A>.</span></span> <span data-ttu-id="ca902-192"><xref:System.Windows.Media.RotateTransform.Angle%2A>Z 45 otočit element 45 stupňů po směru hodinových ručiček; úhel 90 otočí element o 90 stupňů po směru hodinových ručiček a tak dále.</span><span class="sxs-lookup"><span data-stu-id="ca902-192">An <xref:System.Windows.Media.RotateTransform.Angle%2A> of 45 rotates the element 45 degrees clockwise; an angle of 90 rotates the element 90 degrees clockwise; and so on.</span></span> <span data-ttu-id="ca902-193">Nastavte <xref:System.Windows.Media.RotateTransform.CenterX%2A> vlastnosti a, <xref:System.Windows.Media.RotateTransform.CenterY%2A> Pokud chcete určit, kde má být prvek otočen.</span><span class="sxs-lookup"><span data-stu-id="ca902-193">Set the <xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> properties if you want to control the point about which the element is rotated.</span></span> <span data-ttu-id="ca902-194">Tyto hodnoty vlastností se vyjadřují v souřadnicovém prostoru elementu, který se transformuje.</span><span class="sxs-lookup"><span data-stu-id="ca902-194">These property values are expressed in the coordinate space of the element being transformed.</span></span> <span data-ttu-id="ca902-195"><xref:System.Windows.Media.RotateTransform.CenterX%2A>a <xref:System.Windows.Media.RotateTransform.CenterY%2A> mají výchozí hodnoty nula.</span><span class="sxs-lookup"><span data-stu-id="ca902-195"><xref:System.Windows.Media.RotateTransform.CenterX%2A> and <xref:System.Windows.Media.RotateTransform.CenterY%2A> have default values of zero.</span></span> <span data-ttu-id="ca902-196">Nakonec použijte <xref:System.Windows.Media.RotateTransform> pro element.</span><span class="sxs-lookup"><span data-stu-id="ca902-196">Finally, apply the <xref:System.Windows.Media.RotateTransform> to the element.</span></span> <span data-ttu-id="ca902-197">Pokud nechcete, aby transformace ovlivnila rozložení, nastavte <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost tvaru.</span><span class="sxs-lookup"><span data-stu-id="ca902-197">If you don't want the transform to affect layout, set the shape's <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="ca902-198">V následujícím příkladu <xref:System.Windows.Media.RotateTransform> se používá k otočení tvaru 45 stupňů kolem levého horního rohu obrazce (0, 0).</span><span class="sxs-lookup"><span data-stu-id="ca902-198">In the following example, a <xref:System.Windows.Media.RotateTransform> is used to rotate a shape 45 degrees about the shape's top left corner (0,0).</span></span>  
  
 [!code-xaml[transformssample#14](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#14)]  
  
 <span data-ttu-id="ca902-199">V dalším příkladu je další tvar otočený 45 stupňů, ale tentokrát se otáčí kolem bodu (25, 50).</span><span class="sxs-lookup"><span data-stu-id="ca902-199">In the next example, another shape is rotated 45 degrees, but this time it's rotated about the point (25,50).</span></span>  
  
 [!code-xaml[transformssample#15](~/samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/RotateTransformExample.xaml#15)]  
  
 <span data-ttu-id="ca902-200">Následující ilustrace znázorňuje výsledky použití dvou transformací.</span><span class="sxs-lookup"><span data-stu-id="ca902-200">The following illustration shows the results of applying the two transforms.</span></span>  
  
 <span data-ttu-id="ca902-201">![45 stupňů otočení s různými centry](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span><span class="sxs-lookup"><span data-stu-id="ca902-201">![45 degree rotations with different center points](./media/wcpsdk-graphicsmm-rotatetransform45degrees.gif "wcpsdk_graphicsmm_rotatetransform45degrees")</span></span>  
  
 <span data-ttu-id="ca902-202">V předchozích příkladech se u každého objektu Shape použila jedna transformace.</span><span class="sxs-lookup"><span data-stu-id="ca902-202">In the previous examples, a single transform was applied to each shape object.</span></span> <span data-ttu-id="ca902-203">Chcete-li použít více transformací na tvar (nebo jakýkoli jiný prvek uživatelského rozhraní), použijte <xref:System.Windows.Media.TransformGroup> .</span><span class="sxs-lookup"><span data-stu-id="ca902-203">To apply multiple transforms to a shape (or any other UI element), use a <xref:System.Windows.Media.TransformGroup>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca902-204">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca902-204">See also</span></span>

- [<span data-ttu-id="ca902-205">2D grafika a obrázky</span><span class="sxs-lookup"><span data-stu-id="ca902-205">2D Graphics and Imaging</span></span>](../advanced/optimizing-performance-2d-graphics-and-imaging.md)
- [<span data-ttu-id="ca902-206">Přehled malování plnými barvami a přechody</span><span class="sxs-lookup"><span data-stu-id="ca902-206">Painting with Solid Colors and Gradients Overview</span></span>](painting-with-solid-colors-and-gradients-overview.md)
- [<span data-ttu-id="ca902-207">Přehled geometrie</span><span class="sxs-lookup"><span data-stu-id="ca902-207">Geometry Overview</span></span>](geometry-overview.md)
- [<span data-ttu-id="ca902-208">Návod: Moje první desktopová aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="ca902-208">Walkthrough: My first WPF desktop application</span></span>](../getting-started/walkthrough-my-first-wpf-desktop-application.md)
- [<span data-ttu-id="ca902-209">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="ca902-209">Animation Overview</span></span>](animation-overview.md)
