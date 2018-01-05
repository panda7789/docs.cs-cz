---
title: "Postupy: kreslení sekvence B &#233; zier křivky vyhlazení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- splines [Windows Forms], drawing Bezier
- Bezier splines [Windows Forms], drawing sequence of
ms.assetid: 37a0bedb-20c2-4cf0-91fa-a5509e826b30
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f5bdd9ae29dcbb8397d2fe645e240572aad32a19
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-sequence-of-b233zier-splines"></a><span data-ttu-id="0bc21-102">Postupy: kreslení sekvence B &#233; zier křivky vyhlazení</span><span class="sxs-lookup"><span data-stu-id="0bc21-102">How to: Draw a Sequence of B&#233;zier Splines</span></span>
<span data-ttu-id="0bc21-103">Můžete použít <xref:System.Drawing.Graphics.DrawBeziers%2A> metodu <xref:System.Drawing.Graphics> připojené třída pro kreslení sekvence Bézierových křivek.</span><span class="sxs-lookup"><span data-stu-id="0bc21-103">You can use the <xref:System.Drawing.Graphics.DrawBeziers%2A> method of the <xref:System.Drawing.Graphics> class to draw a sequence of connected Bézier splines.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0bc21-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0bc21-104">Example</span></span>  
 <span data-ttu-id="0bc21-105">Následující příklad nakreslí křivku, který se skládá ze dvou připojené Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="0bc21-105">The following example draws a curve that consists of two connected Bézier splines.</span></span> <span data-ttu-id="0bc21-106">Koncový bod první Bézierovy křivky je počáteční bod druhý Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="0bc21-106">The endpoint of the first Bézier spline is the start point of the second Bézier spline.</span></span>  
  
 <span data-ttu-id="0bc21-107">Následující obrázek znázorňuje připojené křivky společně s sedm body.</span><span class="sxs-lookup"><span data-stu-id="0bc21-107">The following illustration shows the connected splines along with the seven points.</span></span>  
  
 <span data-ttu-id="0bc21-108">![Bézierovy křivky](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span><span class="sxs-lookup"><span data-stu-id="0bc21-108">![Bezier Spline](../../../../docs/framework/winforms/advanced/media/bezierspline2.png "BezierSpline2")</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ConstructingDrawingCurves#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingCurves/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0bc21-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0bc21-109">Compiling the Code</span></span>  
 <span data-ttu-id="0bc21-110">V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="0bc21-110">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bc21-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="0bc21-111">See Also</span></span>  
 [<span data-ttu-id="0bc21-112">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0bc21-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="0bc21-113">Bézierovy křivky v GDI+</span><span class="sxs-lookup"><span data-stu-id="0bc21-113">Bézier Splines in GDI+</span></span>](../../../../docs/framework/winforms/advanced/bezier-splines-in-gdi.md)  
 [<span data-ttu-id="0bc21-114">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="0bc21-114">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)
