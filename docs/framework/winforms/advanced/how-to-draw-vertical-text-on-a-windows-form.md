---
title: "Postupy: Kreslení svislého textu v rozhraní Windows Forms"
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
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 76da7be50f9e12454e16e08ec4db494585fae613
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="ab86e-102">Postupy: Kreslení svislého textu v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ab86e-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="ab86e-103">Následující příklad kódu ukazuje, jak kreslení svislého textu ve formuláři pomocí <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="ab86e-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab86e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ab86e-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ab86e-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="ab86e-105">Compiling the Code</span></span>  
 <span data-ttu-id="ab86e-106">Tuto metodu nelze volat <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="ab86e-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="ab86e-107">Pokud po změně velikosti nebo zakrytý jiného formuláře formuláře nebude překreslit vykresleného obsah.</span><span class="sxs-lookup"><span data-stu-id="ab86e-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="ab86e-108">Chcete-li obsah automaticky překreslit, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="ab86e-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ab86e-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="ab86e-109">Robust Programming</span></span>  
 <span data-ttu-id="ab86e-110">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="ab86e-110">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="ab86e-111">Písmo Arial není nainstalována.</span><span class="sxs-lookup"><span data-stu-id="ab86e-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab86e-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="ab86e-112">See Also</span></span>  
 <xref:System.Drawing.Graphics.DrawString%2A>  
 <xref:System.Drawing.StringFormat.FormatFlags%2A>  
 <xref:System.Drawing.StringFormatFlags>  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 [<span data-ttu-id="ab86e-113">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="ab86e-113">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 [<span data-ttu-id="ab86e-114">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="ab86e-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
