---
title: B&#233;zier křivky v GDI +
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines
- splines [Windows Forms], Bezier
- GDI+, Bezier splines
ms.assetid: 5774ce1e-87d4-4bc7-88c4-4862052781b8
ms.openlocfilehash: ff4e9eb18610b70c88e057d3d44020321bbb9f4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59107325"
---
# <a name="b233zier-splines-in-gdi"></a><span data-ttu-id="50860-102">B&#233;zier křivky v GDI +</span><span class="sxs-lookup"><span data-stu-id="50860-102">B&#233;zier Splines in GDI+</span></span>
<span data-ttu-id="50860-103">Bézierovy křivky je křivka určené čtyři body: dva koncové body (p1 a p2) a dva kontrolních bodů (c1 a c2).</span><span class="sxs-lookup"><span data-stu-id="50860-103">A Bézier spline is a curve specified by four points: two end points (p1 and p2) and two control points (c1 and c2).</span></span> <span data-ttu-id="50860-104">Křivky začíná p1 a p2 končí.</span><span class="sxs-lookup"><span data-stu-id="50860-104">The curve begins at p1 and ends at p2.</span></span> <span data-ttu-id="50860-105">Křivka neprochází přes kontrolních bodů, ale kontrolní body fungují jako magnets stahování křivky v některých směrech a vliv na způsob, jakým zatáčkách křivky.</span><span class="sxs-lookup"><span data-stu-id="50860-105">The curve does not pass through the control points, but the control points act as magnets, pulling the curve in certain directions and influencing the way the curve bends.</span></span> <span data-ttu-id="50860-106">Následující obrázek znázorňuje Bézierovy křivky spolu s jeho koncových bodů a kontrolní body.</span><span class="sxs-lookup"><span data-stu-id="50860-106">The following illustration shows a Bézier curve along with its endpoints and control points.</span></span>  
  
 <span data-ttu-id="50860-107">![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span><span class="sxs-lookup"><span data-stu-id="50860-107">![Bezier Splines](./media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span></span>  
  
 <span data-ttu-id="50860-108">Křivka začíná p1 a blíží c1 bodu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50860-108">The curve starts at p1 and moves toward the control point c1.</span></span> <span data-ttu-id="50860-109">Tečný čáry na křivku P1 je linií z p1 c1.</span><span class="sxs-lookup"><span data-stu-id="50860-109">The tangent line to the curve at p1 is the line drawn from p1 to c1.</span></span> <span data-ttu-id="50860-110">Tečný řádek na p2 koncový bod je linií z c2 p2.</span><span class="sxs-lookup"><span data-stu-id="50860-110">The tangent line at the endpoint p2 is the line drawn from c2 to p2.</span></span>  
  
## <a name="drawing-bzier-splines"></a><span data-ttu-id="50860-111">Kreslení Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="50860-111">Drawing Bézier Splines</span></span>  
 <span data-ttu-id="50860-112">Na kreslení Bézierovy křivky, je třeba instance <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Pen>.</span><span class="sxs-lookup"><span data-stu-id="50860-112">To draw a Bézier spline, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Pen>.</span></span> <span data-ttu-id="50860-113">Instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawBezier%2A> metody a <xref:System.Drawing.Pen> uloží atributy, například šířku a barvu čáry použité k vykreslení křivky.</span><span class="sxs-lookup"><span data-stu-id="50860-113">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawBezier%2A> method, and the <xref:System.Drawing.Pen> stores attributes, such as width and color, of the line used to render the curve.</span></span> <span data-ttu-id="50860-114"><xref:System.Drawing.Pen> Je předán jako argumenty, které mají <xref:System.Drawing.Graphics.DrawBezier%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="50860-114">The <xref:System.Drawing.Pen> is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawBezier%2A> method.</span></span> <span data-ttu-id="50860-115">Zbývající argumenty předané <xref:System.Drawing.Graphics.DrawBezier%2A> metody jsou koncové body a body ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="50860-115">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawBezier%2A> method are the endpoints and the control points.</span></span> <span data-ttu-id="50860-116">Následující příklad kreslení Bézierovy křivky s počáteční bod (0, 0), řídit body (40, 20) a (80, 150) a koncový bod (100, 10):</span><span class="sxs-lookup"><span data-stu-id="50860-116">The following example draws a Bézier spline with starting point (0, 0), control points (40, 20) and (80, 150), and ending point (100, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#71](~/samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](~/samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 <span data-ttu-id="50860-117">Následující obrázek znázorňuje křivku, kontrolní body a tečný dva řádky.</span><span class="sxs-lookup"><span data-stu-id="50860-117">The following illustration shows the curve, the control points, and two tangent lines.</span></span>  
  
 <span data-ttu-id="50860-118">![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span><span class="sxs-lookup"><span data-stu-id="50860-118">![Bezier Splines](./media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span></span>  
  
 <span data-ttu-id="50860-119">Bézierovy křivky byly původně vyvinutý Pierre Bézierovy pro programátory v automobilový průmysl.</span><span class="sxs-lookup"><span data-stu-id="50860-119">Bézier splines were originally developed by Pierre Bézier for design in the automotive industry.</span></span> <span data-ttu-id="50860-120">Se od té doby ukázaly být užitečné v mnoha typech engineeringových návrhu a se také používají k definování obrysy písma.</span><span class="sxs-lookup"><span data-stu-id="50860-120">They have since proven to be useful in many types of computer-aided design and are also used to define the outlines of fonts.</span></span> <span data-ttu-id="50860-121">Bézierovy křivky může přinést širokou škálu tvary, z nichž některé jsou zobrazené na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="50860-121">Bézier splines can yield a wide variety of shapes, some of which are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="50860-122">![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span><span class="sxs-lookup"><span data-stu-id="50860-122">![Paths](./media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50860-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="50860-123">See also</span></span>

- <xref:System.Drawing.Graphics?displayProperty=nameWithType>
- <xref:System.Drawing.Pen?displayProperty=nameWithType>
- [<span data-ttu-id="50860-124">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="50860-124">Lines, Curves, and Shapes</span></span>](lines-curves-and-shapes.md)
- [<span data-ttu-id="50860-125">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="50860-125">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
- [<span data-ttu-id="50860-126">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="50860-126">How to: Create Graphics Objects for Drawing</span></span>](how-to-create-graphics-objects-for-drawing.md)
- [<span data-ttu-id="50860-127">Postupy: Vytvoření pera</span><span class="sxs-lookup"><span data-stu-id="50860-127">How to: Create a Pen</span></span>](how-to-create-a-pen.md)
