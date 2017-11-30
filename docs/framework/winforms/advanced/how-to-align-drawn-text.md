---
title: "Postupy: Zarovnání vykresleného textu"
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
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a2f2f6bd088ad58277839cf7e32a98d67ca3bd15
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-align-drawn-text"></a><span data-ttu-id="7c395-102">Postupy: Zarovnání vykresleného textu</span><span class="sxs-lookup"><span data-stu-id="7c395-102">How to: Align Drawn Text</span></span>
<span data-ttu-id="7c395-103">Při provádění vlastní kreslení, můžete často center vykresleného textu ve formuláři nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="7c395-103">When you perform custom drawing, you may often want to center drawn text on a form or control.</span></span> <span data-ttu-id="7c395-104">Můžete snadno zarovnat text vykreslené s <xref:System.Drawing.Graphics.DrawString%2A> nebo <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody vytváření správné formátování objektu a nastavením příznaků příslušný formát.</span><span class="sxs-lookup"><span data-stu-id="7c395-104">You can easily align text drawn with the <xref:System.Drawing.Graphics.DrawString%2A> or <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods by creating the correct formatting object and setting the appropriate format flags.</span></span>  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a><span data-ttu-id="7c395-105">Kreslení zarovnaný na střed textu pomocí GDI + (tkanicí stažení)</span><span class="sxs-lookup"><span data-stu-id="7c395-105">To draw centered text with GDI+ (DrawString)</span></span>  
  
1.  <span data-ttu-id="7c395-106">Použití <xref:System.Drawing.StringFormat> s příslušnou <xref:System.Drawing.Graphics.DrawString%2A> metoda zadat text zarovnaný na střed.</span><span class="sxs-lookup"><span data-stu-id="7c395-106">Use a <xref:System.Drawing.StringFormat> with the appropriate <xref:System.Drawing.Graphics.DrawString%2A> method to specify centered text.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a><span data-ttu-id="7c395-107">Kreslení zarovnaný na střed textu pomocí GDI (DrawText)</span><span class="sxs-lookup"><span data-stu-id="7c395-107">To draw centered text with GDI (DrawText)</span></span>  
  
1.  <span data-ttu-id="7c395-108">Použití <xref:System.Windows.Forms.TextFormatFlags> výčtu pro zabalení a také vodorovně a svisle zarovnání textu pomocí odpovídající <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="7c395-108">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration for wrapping as well as vertically and horizontally centering text with the appropriate <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7c395-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7c395-109">Compiling the Code</span></span>  
 <span data-ttu-id="7c395-110">V předchozích příkladech kódu jsou navrženy pro používání s formuláři Windows a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="7c395-110">The preceding code examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c395-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c395-111">See Also</span></span>  
 [<span data-ttu-id="7c395-112">Postupy: kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="7c395-112">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="7c395-113">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="7c395-113">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="7c395-114">Postupy: vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="7c395-114">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
