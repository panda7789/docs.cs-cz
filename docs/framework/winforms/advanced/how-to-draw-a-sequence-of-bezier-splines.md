---
title: 'Postupy: Kreslení sekvence B&#233;zier křivek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
ms.openlocfilehash: 976787f5830282a581d05a9c24d1f83dceca4b25
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168152"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="e702b-102">Postupy: Kreslení sekvence B&#233;zier křivek</span><span class="sxs-lookup"><span data-stu-id="e702b-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="e702b-103">Můžete použít <xref:System.Drawing.Graphics.DrawBeziers%2A> metodu <xref:System.Drawing.Graphics> připojené třídy kreslení sekvence Bézierových křivek.</span><span class="sxs-lookup"><span data-stu-id="e702b-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e702b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e702b-104">Example</span></span>  
 <span data-ttu-id="e702b-105">Následující příklad nakreslí křivku, která se skládá ze dvou připojených Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="e702b-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="e702b-106">Koncový bod první Bézierovy křivky se počáteční bod druhý Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="e702b-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="e702b-107">Následující obrázek znázorňuje připojených křivky spolu s sedm body:</span><span class="sxs-lookup"><span data-stu-id="e702b-107">The following illustration shows the connected splines along with the seven points:</span></span>  
  
 ![Obrázek znázorňující, připojené křivky spolu s sedm bodů.](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e702b-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e702b-109">Compiling the Code</span></span>  
 <span data-ttu-id="e702b-110">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="e702b-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e702b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e702b-111">See also</span></span>

- [<span data-ttu-id="e702b-112">Grafika a kreslení v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e702b-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="e702b-113">Bézierovy křivky v GDI+</span><span class="sxs-lookup"><span data-stu-id="e702b-113">Bézier Splines in GDI+</span></span>](bezier-splines-in-gdi.md)
- [<span data-ttu-id="e702b-114">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="e702b-114">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
