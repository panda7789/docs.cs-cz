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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59168152"
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="474ae-102">Postupy: Kreslení sekvence B&#233;zier křivek</span><span class="sxs-lookup"><span data-stu-id="474ae-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="474ae-103">Můžete použít <xref:System.Drawing.Graphics.DrawBeziers%2A> metodu <xref:System.Drawing.Graphics> připojené třídy kreslení sekvence Bézierových křivek.</span><span class="sxs-lookup"><span data-stu-id="474ae-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="474ae-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="474ae-104">Example</span></span>  
 <span data-ttu-id="474ae-105">Následující příklad nakreslí křivku, která se skládá ze dvou připojených Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="474ae-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="474ae-106">Koncový bod první Bézierovy křivky se počáteční bod druhý Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="474ae-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="474ae-107">Následující obrázek znázorňuje připojených křivky spolu s sedm body:</span><span class="sxs-lookup"><span data-stu-id="474ae-107">The following illustration shows the connected splines along with the seven points:</span></span>  
  
 ![Obrázek znázorňující, připojené křivky spolu s sedm bodů.](./media/how-to-draw-a-sequence-of-bezier-splines/bezier-spline-seven-points.png)  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="474ae-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="474ae-109">Compiling the Code</span></span>  
 <span data-ttu-id="474ae-110">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="474ae-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="474ae-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="474ae-111">See also</span></span>

- [<span data-ttu-id="474ae-112">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="474ae-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="474ae-113">Bézierovy křivky v GDI+</span><span class="sxs-lookup"><span data-stu-id="474ae-113">Bézier Splines in GDI+</span></span>](bezier-splines-in-gdi.md)
- [<span data-ttu-id="474ae-114">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="474ae-114">Constructing and Drawing Curves</span></span>](constructing-and-drawing-curves.md)
