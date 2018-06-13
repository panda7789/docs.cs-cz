---
title: 'Postupy: Kreslení plné elipsy v rozhraní Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Graphics.FillEllipse
helpviewer_keywords:
- ellipses [Windows Forms], drawing
- circles [Windows Forms], drawing
- circular shapes
- drawing [Windows Forms], ellipses
- shapes [Windows Forms], drawing
- forms [Windows Forms], drawing ellipses
ms.assetid: 781db806-950d-4c5b-b022-493f7fd0c4a8
ms.openlocfilehash: b892670031e795ecd27b194cdf2cf818f4af6254
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521430"
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a><span data-ttu-id="eb584-102">Postupy: Kreslení plné elipsy v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb584-102">How to: Draw a Filled Ellipse on a Windows Form</span></span>
<span data-ttu-id="eb584-103">Tento příklad kreslení plné elipsy ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="eb584-103">This example draws a filled ellipse on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eb584-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb584-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="eb584-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="eb584-105">Compiling the Code</span></span>  
 <span data-ttu-id="eb584-106">Tuto metodu nelze volat <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="eb584-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="eb584-107">Pokud po změně velikosti nebo zakrytý jiného formuláře formuláře nebude překreslit vykresleného obsah.</span><span class="sxs-lookup"><span data-stu-id="eb584-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="eb584-108">Chcete-li obsah automaticky překreslit, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="eb584-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="eb584-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="eb584-109">Robust Programming</span></span>  
 <span data-ttu-id="eb584-110">Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Brush> a <xref:System.Drawing.Graphics> objekty.</span><span class="sxs-lookup"><span data-stu-id="eb584-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb584-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb584-111">See Also</span></span>  
 [<span data-ttu-id="eb584-112">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eb584-112">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="eb584-113">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="eb584-113">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="eb584-114">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="eb584-114">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [<span data-ttu-id="eb584-115">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="eb584-115">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
