---
title: "Postupy: Kreslení obrazce s obrysem"
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
- cpp
f1_keywords: Graphics.DrawEllipse
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
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05247d24f3db95d042cb4ac34ec6ed648ec1d997
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-an-outlined-shape"></a><span data-ttu-id="fb3cd-102">Postupy: Kreslení obrazce s obrysem</span><span class="sxs-lookup"><span data-stu-id="fb3cd-102">How to: Draw an Outlined Shape</span></span>
<span data-ttu-id="fb3cd-103">Tento příklad nevykresluje popsané výpustky a obdélníky ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="fb3cd-103">This example draws outlined ellipses and rectangles on a form.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fb3cd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="fb3cd-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#6)]
 [!code-csharp[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#6)]
 [!code-vb[System.Drawing.ConceptualHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fb3cd-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fb3cd-105">Compiling the Code</span></span>  
 <span data-ttu-id="fb3cd-106">Tuto metodu nelze volat <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="fb3cd-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="fb3cd-107">Pokud po změně velikosti nebo zakrytý jiného formuláře formuláře nebude překreslit vykresleného obsah.</span><span class="sxs-lookup"><span data-stu-id="fb3cd-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="fb3cd-108">Chcete-li obsah automaticky překreslit, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="fb3cd-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="fb3cd-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="fb3cd-109">Robust Programming</span></span>  
 <span data-ttu-id="fb3cd-110">Vždy byste měli zavolat <xref:System.IDisposable.Dispose%2A> na všechny objekty, které využívají systémové prostředky, jako například <xref:System.Drawing.Pen> a <xref:System.Drawing.Graphics> objekty.</span><span class="sxs-lookup"><span data-stu-id="fb3cd-110">You should always call <xref:System.IDisposable.Dispose%2A> on any objects that consume system resources, such as <xref:System.Drawing.Pen> and <xref:System.Drawing.Graphics> objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb3cd-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb3cd-111">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawEllipse%2A>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 <xref:System.Drawing.Graphics.DrawRectangle%2A>  
 [<span data-ttu-id="fb3cd-112">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="fb3cd-112">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="fb3cd-113">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="fb3cd-113">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [<span data-ttu-id="fb3cd-114">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fb3cd-114">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
