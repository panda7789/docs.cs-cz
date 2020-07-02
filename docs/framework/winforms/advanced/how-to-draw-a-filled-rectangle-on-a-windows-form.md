---
title: 'Postupy: Kreslení plného obdélníku v rozhraní Windows Form'
description: Naučte se programově nakreslit plný obdélník na formuláři Windows. Přečtěte si také informace o kompilování kódu.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillRectangle
helpviewer_keywords:
- drawing [Windows Forms], rectangles
- rectangles [Windows Forms], drawing
- drawing rectangles
ms.assetid: d656a93c-987d-4809-aafd-493fe17450f0
ms.openlocfilehash: 0ad8ec97000e29b2194a9eda713aa43d5557b44c
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621636"
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="3b919-104">Postupy: Kreslení plného obdélníku v rozhraní Windows Form</span><span class="sxs-lookup"><span data-stu-id="3b919-104">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="3b919-105">Tento příklad nakreslí vyplněný obdélník na formuláři.</span><span class="sxs-lookup"><span data-stu-id="3b919-105">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b919-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3b919-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="3b919-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="3b919-107">Compiling the Code</span></span>  
 <span data-ttu-id="3b919-108">Tuto metodu nelze volat v <xref:System.Windows.Forms.Form.Load> obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="3b919-108">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="3b919-109">Nakreslený obsah nebude překreslen v případě, že dojde ke změně velikosti formuláře nebo jeho skrytí jiným formulářem.</span><span class="sxs-lookup"><span data-stu-id="3b919-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="3b919-110">Chcete-li obsah automaticky překreslit, měli byste přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metodu.</span><span class="sxs-lookup"><span data-stu-id="3b919-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="3b919-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="3b919-111">Robust Programming</span></span>  
 <span data-ttu-id="3b919-112">Vždy byste měli volat <xref:System.IDisposable.Dispose%2A> všechny objekty, které využívají systémové prostředky, například <xref:System.Drawing.Brush> a <xref:System.Drawing.Graphics> objekty.</span><span class="sxs-lookup"><span data-stu-id="3b919-112">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b919-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b919-113">See also</span></span>

- <xref:System.Drawing.Graphics.FillRectangle%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="3b919-114">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="3b919-114">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="3b919-115">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3b919-115">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="3b919-116">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="3b919-116">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="3b919-117">Štětce a vyplněné obrazce v GDI+</span><span class="sxs-lookup"><span data-stu-id="3b919-117">Brushes and Filled Shapes in GDI+</span></span>](brushes-and-filled-shapes-in-gdi.md)
