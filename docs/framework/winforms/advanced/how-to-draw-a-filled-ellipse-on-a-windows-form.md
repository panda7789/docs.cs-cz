---
title: 'Postupy: Kreslení plné elipsy ve formuláři Windows'
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
ms.openlocfilehash: 42316cd0d55b5154b21b4462157e044b30674ebd
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57716277"
---
# <a name="how-to-draw-a-filled-ellipse-on-a-windows-form"></a><span data-ttu-id="6b59b-102">Postupy: Kreslení plné elipsy ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="6b59b-102">How to: Draw a Filled Ellipse on a Windows Form</span></span>
<span data-ttu-id="6b59b-103">V tomto příkladu kreslení plné elipsy ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="6b59b-103">This example draws a filled ellipse on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b59b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b59b-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#1)]
 [!code-csharp[System.Drawing.ConceptualHowTos#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#1)]
 [!code-vb[System.Drawing.ConceptualHowTos#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6b59b-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="6b59b-105">Compiling the Code</span></span>  
 <span data-ttu-id="6b59b-106">Tuto metodu nelze volat <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="6b59b-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="6b59b-107">Vykreslený obsah aktivním, pokud je velikost nebo zakryto jiný formulář. formuláře.</span><span class="sxs-lookup"><span data-stu-id="6b59b-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="6b59b-108">Chcete-li obsah automaticky repaint, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6b59b-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6b59b-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="6b59b-109">Robust Programming</span></span>  
 <span data-ttu-id="6b59b-110">Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Brush> a <xref:System.Drawing.Graphics> objekty.</span><span class="sxs-lookup"><span data-stu-id="6b59b-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b59b-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b59b-111">See also</span></span>
- [<span data-ttu-id="6b59b-112">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="6b59b-112">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="6b59b-113">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="6b59b-113">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="6b59b-114">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="6b59b-114">Alpha Blending Lines and Fills</span></span>](alpha-blending-lines-and-fills.md)
- [<span data-ttu-id="6b59b-115">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="6b59b-115">Using a Brush to Fill Shapes</span></span>](using-a-brush-to-fill-shapes.md)
