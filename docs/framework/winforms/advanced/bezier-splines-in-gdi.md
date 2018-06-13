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
ms.openlocfilehash: 2e247ec2bcd57c2fb2f5c32f61d38a2e7a267ff1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517570"
---
# <a name="b233zier-splines-in-gdi"></a><span data-ttu-id="656f4-102">B&#233;zier křivky v GDI +</span><span class="sxs-lookup"><span data-stu-id="656f4-102">B&#233;zier Splines in GDI+</span></span>
<span data-ttu-id="656f4-103">Bézierovy křivky je křivka určeného čtyři body: dva koncové body (p1 a p2) a dva kontrolních bodů (c1 a c2).</span><span class="sxs-lookup"><span data-stu-id="656f4-103">A Bézier spline is a curve specified by four points: two end points (p1 and p2) and two control points (c1 and c2).</span></span> <span data-ttu-id="656f4-104">Křivku začíná na p1 a p2 končí.</span><span class="sxs-lookup"><span data-stu-id="656f4-104">The curve begins at p1 and ends at p2.</span></span> <span data-ttu-id="656f4-105">Křivku nepředává prostřednictvím kontrolní body, ale kontrolní body fungovat jako magnets, stahování křivku v určitých pokynů a ovlivňování způsob, jakým zatáčkách křivku.</span><span class="sxs-lookup"><span data-stu-id="656f4-105">The curve does not pass through the control points, but the control points act as magnets, pulling the curve in certain directions and influencing the way the curve bends.</span></span> <span data-ttu-id="656f4-106">Následující obrázek znázorňuje Bézierovy křivky spolu s jeho koncových bodů a kontrolní body.</span><span class="sxs-lookup"><span data-stu-id="656f4-106">The following illustration shows a Bézier curve along with its endpoints and control points.</span></span>  
  
 <span data-ttu-id="656f4-107">![Bézierovy křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span><span class="sxs-lookup"><span data-stu-id="656f4-107">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art11a.gif "Aboutgdip02_art11a")</span></span>  
  
 <span data-ttu-id="656f4-108">Křivku začíná p1 a blíží c1 bodu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="656f4-108">The curve starts at p1 and moves toward the control point c1.</span></span> <span data-ttu-id="656f4-109">Tečný čáry na křivku P1 je řádku vykreslovány z p1 c1.</span><span class="sxs-lookup"><span data-stu-id="656f4-109">The tangent line to the curve at p1 is the line drawn from p1 to c1.</span></span> <span data-ttu-id="656f4-110">Tečný řádek v p2 koncový bod je řádku vykreslovány z c2 p2.</span><span class="sxs-lookup"><span data-stu-id="656f4-110">The tangent line at the endpoint p2 is the line drawn from c2 to p2.</span></span>  
  
## <a name="drawing-bzier-splines"></a><span data-ttu-id="656f4-111">Kreslení Bézierovy křivky</span><span class="sxs-lookup"><span data-stu-id="656f4-111">Drawing Bézier Splines</span></span>  
 <span data-ttu-id="656f4-112">Kreslení Bézierovy křivky, je třeba instanci <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Pen>.</span><span class="sxs-lookup"><span data-stu-id="656f4-112">To draw a Bézier spline, you need an instance of the <xref:System.Drawing.Graphics> class and a <xref:System.Drawing.Pen>.</span></span> <span data-ttu-id="656f4-113">Instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawBezier%2A> metody a <xref:System.Drawing.Pen> ukládá atributy, jako například šířku a barvu čáry použité k vykreslení křivku.</span><span class="sxs-lookup"><span data-stu-id="656f4-113">The instance of the <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.DrawBezier%2A> method, and the <xref:System.Drawing.Pen> stores attributes, such as width and color, of the line used to render the curve.</span></span> <span data-ttu-id="656f4-114"><xref:System.Drawing.Pen> Se předá jako jeden z argumenty, které mají <xref:System.Drawing.Graphics.DrawBezier%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="656f4-114">The <xref:System.Drawing.Pen> is passed as one of the arguments to the <xref:System.Drawing.Graphics.DrawBezier%2A> method.</span></span> <span data-ttu-id="656f4-115">Zbývající argumenty předaný <xref:System.Drawing.Graphics.DrawBezier%2A> metoda jsou koncové body a kontrolní body.</span><span class="sxs-lookup"><span data-stu-id="656f4-115">The remaining arguments passed to the <xref:System.Drawing.Graphics.DrawBezier%2A> method are the endpoints and the control points.</span></span> <span data-ttu-id="656f4-116">Následující příklad nevykresluje Bézierovy křivky s výchozí bod (0, 0), řídit body (40, 20) a (80, 150) a koncový bod (100, 10):</span><span class="sxs-lookup"><span data-stu-id="656f4-116">The following example draws a Bézier spline with starting point (0, 0), control points (40, 20) and (80, 150), and ending point (100, 10):</span></span>  
  
 [!code-csharp[LinesCurvesAndShapes#71](../../../../samples/snippets/csharp/VS_Snippets_Winforms/LinesCurvesAndShapes/CS/Class1.cs#71)]
 [!code-vb[LinesCurvesAndShapes#71](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/LinesCurvesAndShapes/VB/Class1.vb#71)]  
  
 <span data-ttu-id="656f4-117">Následující obrázek znázorňuje křivku, kontrolní body a tečný dva řádky.</span><span class="sxs-lookup"><span data-stu-id="656f4-117">The following illustration shows the curve, the control points, and two tangent lines.</span></span>  
  
 <span data-ttu-id="656f4-118">![Bézierovy křivky](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span><span class="sxs-lookup"><span data-stu-id="656f4-118">![Bezier Splines](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art12.gif "Aboutgdip02_art12")</span></span>  
  
 <span data-ttu-id="656f4-119">Bézierovy křivky byly původně vyvinuté Pierre Bézierovy návrh v automobilu odvětví.</span><span class="sxs-lookup"><span data-stu-id="656f4-119">Bézier splines were originally developed by Pierre Bézier for design in the automotive industry.</span></span> <span data-ttu-id="656f4-120">Tyto ukázaly od jako užitečné v mnoha typech počítačový návrhu a také slouží k určení jsou podrobněji popsány dále písem.</span><span class="sxs-lookup"><span data-stu-id="656f4-120">They have since proven to be useful in many types of computer-aided design and are also used to define the outlines of fonts.</span></span> <span data-ttu-id="656f4-121">Bézierovy křivky přispět širokou škálu tvarů, z nichž některé jsou uvedeny na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="656f4-121">Bézier splines can yield a wide variety of shapes, some of which are shown in the following illustration.</span></span>  
  
 <span data-ttu-id="656f4-122">![Cesty](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span><span class="sxs-lookup"><span data-stu-id="656f4-122">![Paths](../../../../docs/framework/winforms/advanced/media/aboutgdip02-art13.gif "Aboutgdip02_art13")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="656f4-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="656f4-123">See Also</span></span>  
 <xref:System.Drawing.Graphics?displayProperty=nameWithType>  
 <xref:System.Drawing.Pen?displayProperty=nameWithType>  
 [<span data-ttu-id="656f4-124">Čáry, křivky a obrazce</span><span class="sxs-lookup"><span data-stu-id="656f4-124">Lines, Curves, and Shapes</span></span>](../../../../docs/framework/winforms/advanced/lines-curves-and-shapes.md)  
 [<span data-ttu-id="656f4-125">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="656f4-125">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 [<span data-ttu-id="656f4-126">Postupy: Vytváření grafických objektů pro kreslení</span><span class="sxs-lookup"><span data-stu-id="656f4-126">How to: Create Graphics Objects for Drawing</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [<span data-ttu-id="656f4-127">Postupy: Vytvoření pera</span><span class="sxs-lookup"><span data-stu-id="656f4-127">How to: Create a Pen</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-pen.md)
