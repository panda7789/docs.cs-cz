---
title: "Postupy: Kreslení plného obdélníku v rozhraní Windows Form"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 17d143c0c265fea876d084ebc21663d93553fe9d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-a-filled-rectangle-on-a-windows-form"></a><span data-ttu-id="f5d61-102">Postupy: Kreslení plného obdélníku v rozhraní Windows Form</span><span class="sxs-lookup"><span data-stu-id="f5d61-102">How to: Draw a Filled Rectangle on a Windows Form</span></span>
<span data-ttu-id="f5d61-103">Tento příklad Kreslení plného obdélníku ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="f5d61-103">This example draws a filled rectangle on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5d61-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5d61-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#2)]
 [!code-csharp[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#2)]
 [!code-vb[System.Drawing.ConceptualHowTos#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#2)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f5d61-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f5d61-105">Compiling the Code</span></span>  
 <span data-ttu-id="f5d61-106">Tuto metodu nelze volat <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="f5d61-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="f5d61-107">Pokud po změně velikosti nebo zakrytý jiného formuláře formuláře nebude překreslit vykresleného obsah.</span><span class="sxs-lookup"><span data-stu-id="f5d61-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="f5d61-108">Chcete-li obsah automaticky překreslit, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="f5d61-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="f5d61-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="f5d61-109">Robust Programming</span></span>  
 <span data-ttu-id="f5d61-110">Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Brush> a <xref:System.Drawing.Graphics> objekty.</span><span class="sxs-lookup"><span data-stu-id="f5d61-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Brush> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5d61-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5d61-111">See Also</span></span>  
 <xref:System.Drawing.Graphics.FillRectangle%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="f5d61-112">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="f5d61-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="f5d61-113">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f5d61-113">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="f5d61-114">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="f5d61-114">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="f5d61-115">Štětce a vyplněné obrazce v GDI+</span><span class="sxs-lookup"><span data-stu-id="f5d61-115">Brushes and Filled Shapes in GDI+</span></span>](../../../../docs/framework/winforms/advanced/brushes-and-filled-shapes-in-gdi.md)
