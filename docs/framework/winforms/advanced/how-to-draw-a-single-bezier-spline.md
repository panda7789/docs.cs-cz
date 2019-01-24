---
title: 'Postupy: Kreslení jedné B&#233;zier křivky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Bezier splines [Windows Forms], drawing
- drawing [Windows Forms], Bezier splines
ms.assetid: f4f3fe30-f0a6-4743-ac91-11310cebea9f
ms.openlocfilehash: 32fc09c7525b40daea8c8705c43100cea0c052bc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676455"
---
# <a name="how-to-draw-a-single-b233zier-spline"></a><span data-ttu-id="901c1-102">Postupy: Kreslení jedné B&#233;zier křivky</span><span class="sxs-lookup"><span data-stu-id="901c1-102">How to: Draw a Single B&#233;zier Spline</span></span>
<span data-ttu-id="901c1-103">Bézierovy křivky definoval čtyři body: počáteční bod, dva kontrolních bodů a koncový bod.</span><span class="sxs-lookup"><span data-stu-id="901c1-103">A Bézier spline is defined by four points: a start point, two control points, and an endpoint.</span></span>  
  
## <a name="example"></a><span data-ttu-id="901c1-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="901c1-104">Example</span></span>  
 <span data-ttu-id="901c1-105">Následující příklad kreslení Bézierovy křivky s počáteční bod (10, 100) a koncového bodu (200, 100).</span><span class="sxs-lookup"><span data-stu-id="901c1-105">The following example draws a Bézier spline with start point (10, 100) and endpoint (200, 100).</span></span> <span data-ttu-id="901c1-106">Ovládací prvek body jsou (100, 10) a (150, 150).</span><span class="sxs-lookup"><span data-stu-id="901c1-106">The control points are (100, 10) and (150, 150).</span></span>  
  
 <span data-ttu-id="901c1-107">Následující obrázek znázorňuje výsledný Bézierovy křivky spolu s jeho počáteční bod, kontrolní body a koncový bod.</span><span class="sxs-lookup"><span data-stu-id="901c1-107">The following illustration shows the resulting Bézier spline along with its start point, control points, and endpoint.</span></span> <span data-ttu-id="901c1-108">Tento obrázek také ukazuje konvexní trupu křivky, který je tvořen čtyři body sítě s rovné čáry mnohoúhelníku.</span><span class="sxs-lookup"><span data-stu-id="901c1-108">The illustration also shows the spline's convex hull, which is a polygon formed by connecting the four points with straight lines.</span></span>  
  
 <span data-ttu-id="901c1-109">![Bézierova křivka](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span><span class="sxs-lookup"><span data-stu-id="901c1-109">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline1.png "BezierSpline1")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="901c1-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="901c1-110">Compiling the Code</span></span>  
 <span data-ttu-id="901c1-111">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="901c1-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="901c1-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="901c1-112">See also</span></span>
- <xref:System.Drawing.Graphics.DrawBezier%2A>
- [<span data-ttu-id="901c1-113">Bézierovy křivky v GDI+</span><span class="sxs-lookup"><span data-stu-id="901c1-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)
- [<span data-ttu-id="901c1-114">Postupy: Kreslení sekvence Bézierových křivek</span><span class="sxs-lookup"><span data-stu-id="901c1-114">How to: Draw a Sequence of Bézier Splines</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-a-sequence-of-bezier-splines.md)
