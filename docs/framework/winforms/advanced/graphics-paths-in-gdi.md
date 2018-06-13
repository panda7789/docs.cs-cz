---
title: Cesty grafiky v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], paths
- GDI+, drawing paths
- paths [Windows Forms], drawing
- drawing [Windows Forms], paths
ms.assetid: a5500dec-666c-41fd-9da3-2169dd89c5eb
ms.openlocfilehash: 66d30b949fbfe8190b9e2ae2ea7896ac36bf0bac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523885"
---
# <a name="graphics-paths-in-gdi"></a><span data-ttu-id="83ed6-102">Cesty grafiky v GDI+</span><span class="sxs-lookup"><span data-stu-id="83ed6-102">Graphics Paths in GDI+</span></span>
<span data-ttu-id="83ed6-103">Cesty se vytvoří kombinací řádků, obdélníků a jednoduchý křivek.</span><span class="sxs-lookup"><span data-stu-id="83ed6-103">Paths are formed by combining lines, rectangles, and simple curves.</span></span> <span data-ttu-id="83ed6-104">Odvolat z [přehled vektorové grafiky](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) , následující základní stavební bloky ukázaly jako nejvhodnější pro vykreslování obrázků:</span><span class="sxs-lookup"><span data-stu-id="83ed6-104">Recall from the [Vector Graphics Overview](../../../../docs/framework/winforms/advanced/vector-graphics-overview.md) that the following basic building blocks have proven to be the most useful for drawing pictures:</span></span>  
  
-   <span data-ttu-id="83ed6-105">řádky</span><span class="sxs-lookup"><span data-stu-id="83ed6-105">Lines</span></span>  
  
-   <span data-ttu-id="83ed6-106">Obdélníků</span><span class="sxs-lookup"><span data-stu-id="83ed6-106">Rectangles</span></span>  
  
-   <span data-ttu-id="83ed6-107">Symbol tří teček</span><span class="sxs-lookup"><span data-stu-id="83ed6-107">Ellipses</span></span>  
  
-   <span data-ttu-id="83ed6-108">Oblouky</span><span class="sxs-lookup"><span data-stu-id="83ed6-108">Arcs</span></span>  
  
-   <span data-ttu-id="83ed6-109">Mnohoúhelníky</span><span class="sxs-lookup"><span data-stu-id="83ed6-109">Polygons</span></span>  
  
-   <span data-ttu-id="83ed6-110">Základní křivky vyhlazení</span><span class="sxs-lookup"><span data-stu-id="83ed6-110">Cardinal splines</span></span>  
  
-   <span data-ttu-id="83ed6-111">Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="83ed6-111">Bézier splines</span></span>  
  
 <span data-ttu-id="83ed6-112">V rozhraní GDI + <xref:System.Drawing.Drawing2D.GraphicsPath> objekt umožňuje shromažďovat posloupnost tyto stavební bloky do jedné jednotky.</span><span class="sxs-lookup"><span data-stu-id="83ed6-112">In GDI+, the <xref:System.Drawing.Drawing2D.GraphicsPath> object allows you to collect a sequence of these building blocks into a single unit.</span></span> <span data-ttu-id="83ed6-113">Celé řady čar, obdélníků, mnohoúhelníky a křivek pak lze rozlišovat pomocí jednoho volání <xref:System.Drawing.Graphics.DrawPath%2A> metodu <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="83ed6-113">The entire sequence of lines, rectangles, polygons, and curves can then be drawn with one call to the <xref:System.Drawing.Graphics.DrawPath%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="83ed6-114">Následující obrázek znázorňuje cestu vytvořit kombinací řádek, oblouk, Bézierovy křivky a křivky mohutnosti.</span><span class="sxs-lookup"><span data-stu-id="83ed6-114">The following illustration shows a path created by combining a line, an arc, a Bézier spline, and a cardinal spline.</span></span>  
  
 <span data-ttu-id="83ed6-115">![Cesta](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span><span class="sxs-lookup"><span data-stu-id="83ed6-115">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art14.gif "Aboutgdip02_art14")</span></span>  
  
## <a name="using-a-path"></a><span data-ttu-id="83ed6-116">Pomocí cesty</span><span class="sxs-lookup"><span data-stu-id="83ed6-116">Using a Path</span></span>  
 <span data-ttu-id="83ed6-117"><xref:System.Drawing.Drawing2D.GraphicsPath> Třída poskytuje následující metody pro vytvoření posloupnost položek, které se mají vykreslovat: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (pro základní křivky vyhlazení), a <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span><span class="sxs-lookup"><span data-stu-id="83ed6-117">The <xref:System.Drawing.Drawing2D.GraphicsPath> class provides the following methods for creating a sequence of items to be drawn: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangle%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddEllipse%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddPolygon%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> (for cardinal splines), and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBezier%2A>.</span></span> <span data-ttu-id="83ed6-118">Každá z těchto metod je přetížena; To znamená jednotlivé metody podporují několik různých parametr seznamy.</span><span class="sxs-lookup"><span data-stu-id="83ed6-118">Each of these methods is overloaded; that is, each method supports several different parameter lists.</span></span> <span data-ttu-id="83ed6-119">Například jeden varianta <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda přijímá čtyři celá čísla a další varianta <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> metoda obdrží dvě <xref:System.Drawing.Point> objekty.</span><span class="sxs-lookup"><span data-stu-id="83ed6-119">For example, one variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives four integers, and another variation of the <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> method receives two <xref:System.Drawing.Point> objects.</span></span>  
  
 <span data-ttu-id="83ed6-120">Metody pro přidání řádků, obdélníků a Bézierových křivek na cestu, mají množném čísle doprovodné metody, které přidejte několik položek do cesty v jediném volání: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, a <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span><span class="sxs-lookup"><span data-stu-id="83ed6-120">The methods for adding lines, rectangles, and Bézier splines to a path have plural companion methods that add several items to the path in a single call: <xref:System.Drawing.Drawing2D.GraphicsPath.AddLines%2A>, <xref:System.Drawing.Drawing2D.GraphicsPath.AddRectangles%2A>, and <xref:System.Drawing.Drawing2D.GraphicsPath.AddBeziers%2A>.</span></span> <span data-ttu-id="83ed6-121">Navíc <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> metody mají metody Průvodce vyhledáváním, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> a <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, přidá výsečového nebo uzavřené křivky k cestě.</span><span class="sxs-lookup"><span data-stu-id="83ed6-121">Also, the <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddArc%2A> methods have companion methods, <xref:System.Drawing.Drawing2D.GraphicsPath.AddClosedCurve%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddPie%2A>, that add a closed curve or pie to the path.</span></span>  
  
 <span data-ttu-id="83ed6-122">Kreslení cestu, musíte <xref:System.Drawing.Graphics> objekt, <xref:System.Drawing.Pen> objekt a <xref:System.Drawing.Drawing2D.GraphicsPath> objektu.</span><span class="sxs-lookup"><span data-stu-id="83ed6-122">To draw a path, you need a <xref:System.Drawing.Graphics> object, a <xref:System.Drawing.Pen> object, and a <xref:System.Drawing.Drawing2D.GraphicsPath> object.</span></span> <span data-ttu-id="83ed6-123"><xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawPath%2A> metody a <xref:System.Drawing.Pen> objekt ukládá atributy, jako například šířku a barvu čáry použité k vykreslení cestu.</span><span class="sxs-lookup"><span data-stu-id="83ed6-123">The <xref:System.Drawing.Graphics> object provides the <xref:System.Drawing.Graphics.DrawPath%2A> method, and the <xref:System.Drawing.Pen> object stores attributes, such as width and color, of the line used to render the path.</span></span> <span data-ttu-id="83ed6-124"><xref:System.Drawing.Drawing2D.GraphicsPath> Objekt ukládá řady čar a křivek, které tvoří cestu.</span><span class="sxs-lookup"><span data-stu-id="83ed6-124">The <xref:System.Drawing.Drawing2D.GraphicsPath> object stores the sequence of lines and curves that make up the path.</span></span> <span data-ttu-id="83ed6-125"><xref:System.Drawing.Pen> Objektu a <xref:System.Drawing.Drawing2D.GraphicsPath> objekt jsou předány jako argumenty, které mají <xref:System.Drawing.Graphics.DrawPath%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="83ed6-125">The <xref:System.Drawing.Pen> object and the <xref:System.Drawing.Drawing2D.GraphicsPath> object are passed as arguments to the <xref:System.Drawing.Graphics.DrawPath%2A> method.</span></span> <span data-ttu-id="83ed6-126">Následující příklad nevykresluje cestu, která se skládá z řádku, třemi tečkami a Bézierovy křivky:</span><span class="sxs-lookup"><span data-stu-id="83ed6-126">The following example draws a path that consists of a line, an ellipse, and a Bézier spline:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#101](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#101)]
 [!code-vb[LinesCurvesAndShapes#101](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#101)]  
  
 <span data-ttu-id="83ed6-127">Následující obrázek ukazuje cestu.</span><span class="sxs-lookup"><span data-stu-id="83ed6-127">The following illustration shows the path.</span></span>  
  
 <span data-ttu-id="83ed6-128">![Cesta](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span><span class="sxs-lookup"><span data-stu-id="83ed6-128">![Path](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art15.gif "Aboutgdip02_art15")</span></span>  
  
 <span data-ttu-id="83ed6-129">Kromě přidání čar, obdélníků a křivek na cestu, můžete přidat cesty na cestu.</span><span class="sxs-lookup"><span data-stu-id="83ed6-129">In addition to adding lines, rectangles, and curves to a path, you can add paths to a path.</span></span> <span data-ttu-id="83ed6-130">To umožňuje zkombinovat existující cesty k vytvoření složitých cesty.</span><span class="sxs-lookup"><span data-stu-id="83ed6-130">This allows you to combine existing paths to form large, complex paths.</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#102](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#102)]
 [!code-vb[LinesCurvesAndShapes#102](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#102)]  
  
 <span data-ttu-id="83ed6-131">Existují dva další položky, které můžete přidat do cesty: řetězce a koláče.</span><span class="sxs-lookup"><span data-stu-id="83ed6-131">There are two other items you can add to a path: strings and pies.</span></span> <span data-ttu-id="83ed6-132">Výsečový je část vnitřek elipsy.</span><span class="sxs-lookup"><span data-stu-id="83ed6-132">A pie is a portion of the interior of an ellipse.</span></span> <span data-ttu-id="83ed6-133">Následující příklad vytvoří cestu z oblouk, křivky mohutnosti, řetězec a výsečový:</span><span class="sxs-lookup"><span data-stu-id="83ed6-133">The following example creates a path from an arc, a cardinal spline, a string, and a pie:</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#103](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#103)]
 [!code-vb[LinesCurvesAndShapes#103](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#103)]  
  
 <span data-ttu-id="83ed6-134">Následující obrázek ukazuje cestu.</span><span class="sxs-lookup"><span data-stu-id="83ed6-134">The following illustration shows the path.</span></span> <span data-ttu-id="83ed6-135">Všimněte si, že cestu nemusí být připojen; oblouk, křivky mohutnosti, string a kruhový jsou oddělené.</span><span class="sxs-lookup"><span data-stu-id="83ed6-135">Note that a path does not have to be connected; the arc, cardinal spline, string, and pie are separated.</span></span>  
  
 <span data-ttu-id="83ed6-136">![Cesty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span><span class="sxs-lookup"><span data-stu-id="83ed6-136">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art16.gif "Aboutgdip02_Art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83ed6-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="83ed6-137">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath?displayProperty=nameWithType>  
 <xref:System.Drawing.Point?displayProperty=nameWithType>  
 [<span data-ttu-id="83ed6-138">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="83ed6-138">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="83ed6-139">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="83ed6-139">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="83ed6-140">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="83ed6-140">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)
