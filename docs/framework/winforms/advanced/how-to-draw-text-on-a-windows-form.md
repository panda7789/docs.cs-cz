---
title: "Postupy: Kreslení textu v rozhraní Windows Forms"
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
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23919145a04bb4b3d1674b153649aca2228364eb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-text-on-a-windows-form"></a><span data-ttu-id="1bf0e-102">Postupy: Kreslení textu v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1bf0e-102">How to: Draw Text on a Windows Form</span></span>
<span data-ttu-id="1bf0e-103">Následující příklad kódu ukazuje, jak používat <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> kreslení textu ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1bf0e-103">The following code example shows how to use the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> to draw text on a form.</span></span> <span data-ttu-id="1bf0e-104">Alternativně můžete použít <xref:System.Windows.Forms.TextRenderer> pro kreslení textu ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="1bf0e-104">Alternatively, you can use <xref:System.Windows.Forms.TextRenderer> for drawing text on a form.</span></span> <span data-ttu-id="1bf0e-105">Další informace najdete v tématu [postupy: kreslení textu pomocí GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md).</span><span class="sxs-lookup"><span data-stu-id="1bf0e-105">For more information, see [How to: Draw Text with GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf0e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bf0e-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1bf0e-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1bf0e-107">Compiling the Code</span></span>  
 <span data-ttu-id="1bf0e-108">Nelze volat <xref:System.Drawing.Graphics.DrawString%2A> metoda v <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="1bf0e-108">You cannot call the <xref:System.Drawing.Graphics.DrawString%2A> method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="1bf0e-109">Pokud po změně velikosti nebo zakrytý jiného formuláře formuláře nebude překreslit vykresleného obsah.</span><span class="sxs-lookup"><span data-stu-id="1bf0e-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="1bf0e-110">Chcete-li obsah automaticky překreslit, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="1bf0e-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1bf0e-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="1bf0e-111">Robust Programming</span></span>  
 <span data-ttu-id="1bf0e-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="1bf0e-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="1bf0e-113">Písmo Arial není nainstalována.</span><span class="sxs-lookup"><span data-stu-id="1bf0e-113">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf0e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bf0e-114">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Windows.Forms.TextRenderer.DrawText%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.TextFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="1bf0e-115">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="1bf0e-115">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="1bf0e-116">Postupy: kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="1bf0e-116">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
