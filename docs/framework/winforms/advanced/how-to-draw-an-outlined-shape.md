---
title: 'Postupy: Kreslení obrazce s obrysem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.DrawEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- drawing [Windows Forms], shapes
- circular shapes
- forms [Windows Forms], drawing circular shapes
- circles
- outlined shapes [Windows Forms], examples
- outlined shapes [Windows Forms], drawing
- drawing [Windows Forms], circular shapes
- shapes [Windows Forms], drawing
ms.assetid: f4f9214c-607e-407d-8cdd-6549f0278451
ms.openlocfilehash: 019bbc19cc4b26c42f8539eccd93ec4ff87fab12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004143"
---
# <a name="how-to-draw-an-outlined-shape"></a><span data-ttu-id="b5b02-102">Postupy: Kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="b5b02-102">How to: Draw an Outlined Shape</span></span>
<span data-ttu-id="b5b02-103">V tomto příkladu nakreslí na formuláři osnovy symbol tří teček a obdélníky.</span><span class="sxs-lookup"><span data-stu-id="b5b02-103">This example draws outlined ellipses and rectangles on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5b02-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b5b02-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b5b02-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b5b02-105">Compiling the Code</span></span>  
 <span data-ttu-id="b5b02-106">Tuto metodu nelze volat <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="b5b02-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="b5b02-107">Vykreslený obsah aktivním, pokud je velikost nebo zakryto jiný formulář. formuláře.</span><span class="sxs-lookup"><span data-stu-id="b5b02-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="b5b02-108">Chcete-li obsah automaticky repaint, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="b5b02-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="b5b02-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="b5b02-109">Robust Programming</span></span>  
 <span data-ttu-id="b5b02-110">Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> a <xref:System.Drawing.Graphics> objekty.</span><span class="sxs-lookup"><span data-stu-id="b5b02-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5b02-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b5b02-111">See also</span></span>

- <xref:System.Drawing.Graphics.DrawEllipse%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Graphics.DrawRectangle%2A>
- [<span data-ttu-id="b5b02-112">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="b5b02-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="b5b02-113">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="b5b02-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="b5b02-114">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b5b02-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
