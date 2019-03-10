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
ms.openlocfilehash: 598706b381d12b8e820747ca872146bdb5e300c7
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57722630"
---
# <a name="how-to-draw-an-outlined-shape"></a><span data-ttu-id="c7358-102">Postupy: Kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="c7358-102">How to: Draw an Outlined Shape</span></span>
<span data-ttu-id="c7358-103">V tomto příkladu nakreslí na formuláři osnovy symbol tří teček a obdélníky.</span><span class="sxs-lookup"><span data-stu-id="c7358-103">This example draws outlined ellipses and rectangles on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7358-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7358-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c7358-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c7358-105">Compiling the Code</span></span>  
 <span data-ttu-id="c7358-106">Tuto metodu nelze volat <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="c7358-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="c7358-107">Vykreslený obsah aktivním, pokud je velikost nebo zakryto jiný formulář. formuláře.</span><span class="sxs-lookup"><span data-stu-id="c7358-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="c7358-108">Chcete-li obsah automaticky repaint, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c7358-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="c7358-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c7358-109">Robust Programming</span></span>  
 <span data-ttu-id="c7358-110">Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> a <xref:System.Drawing.Graphics> objekty.</span><span class="sxs-lookup"><span data-stu-id="c7358-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7358-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7358-111">See also</span></span>
- <xref:System.Drawing.Graphics.DrawEllipse%2A>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- <xref:System.Drawing.Graphics.DrawRectangle%2A>
- [<span data-ttu-id="c7358-112">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="c7358-112">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="c7358-113">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="c7358-113">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
- [<span data-ttu-id="c7358-114">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c7358-114">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
