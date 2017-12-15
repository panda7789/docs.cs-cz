---
title: "Postupy: Kreslení textu v určeném umístění"
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
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fe6e8563b19ef18b89ad970f3ca35bf5f0782a32
ms.sourcegitcommit: 8ed4ebc15b5ef89d06a7507dc9d5e306e30accf7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/14/2017
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="fb597-102">Postupy: Kreslení textu v určeném umístění</span><span class="sxs-lookup"><span data-stu-id="fb597-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="fb597-103">Při provádění vlastní kreslení je nakreslit text ve vodorovném jeden řádek začínající na zadaný bod.</span><span class="sxs-lookup"><span data-stu-id="fb597-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="fb597-104">Tímto způsobem můžete nakreslit text pomocí <xref:System.Drawing.Graphics.DrawString%2A> přetížený metodu <xref:System.Drawing.Graphics> třídu, která přebírá <xref:System.Drawing.Point> nebo <xref:System.Drawing.PointF> parametr.</span><span class="sxs-lookup"><span data-stu-id="fb597-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="fb597-105"><xref:System.Drawing.Graphics.DrawString%2A> Metoda také vyžaduje, <xref:System.Drawing.Brush> a<xref:System.Drawing.Font></span><span class="sxs-lookup"><span data-stu-id="fb597-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and <xref:System.Drawing.Font></span></span>  
  
 <span data-ttu-id="fb597-106">Můžete také <xref:System.Windows.Forms.TextRenderer.DrawText%2A> přetížený metodu <xref:System.Windows.Forms.TextRenderer> , která má <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="fb597-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <span data-ttu-id="fb597-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A>také vyžaduje <xref:System.Drawing.Color> a <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="fb597-107"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="fb597-108">Následující obrázek ukazuje výstup textu vykreslovat Zadaný bod při použití <xref:System.Drawing.Graphics.DrawString%2A> metodu přetížených.</span><span class="sxs-lookup"><span data-stu-id="fb597-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 <span data-ttu-id="fb597-109">![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")</span><span class="sxs-lookup"><span data-stu-id="fb597-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext1.png "csfontstext1")</span></span>  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="fb597-110">Kreslení na řádku textu pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="fb597-110">To draw a line of text with GDI+</span></span>  
  
1.  <span data-ttu-id="fb597-111">Použití <xref:System.Drawing.Graphics.DrawString%2A> metodu předáním text, který má, <xref:System.Drawing.Point> nebo <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, a <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="fb597-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="fb597-112">Kreslení na řádku textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="fb597-112">To draw a line of text with GDI</span></span>  
  
1.  <span data-ttu-id="fb597-113">Použití <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metodu předáním text, který má, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, a <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="fb597-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fb597-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fb597-114">Compiling the Code</span></span>  
 <span data-ttu-id="fb597-115">Vyžadovat v předchozích příkladech:</span><span class="sxs-lookup"><span data-stu-id="fb597-115">The previous examples require:</span></span>  
  
-   <span data-ttu-id="fb597-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="fb597-116"><xref:System.Windows.Forms.PaintEventArgs>  `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fb597-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="fb597-117">See Also</span></span>  
 [<span data-ttu-id="fb597-118">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="fb597-118">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="fb597-119">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="fb597-119">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="fb597-120">Postupy: Vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="fb597-120">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [<span data-ttu-id="fb597-121">Postupy: Kreslení zalomeného textu do obdélníku</span><span class="sxs-lookup"><span data-stu-id="fb597-121">How to: Draw Wrapped Text in a Rectangle</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-wrapped-text-in-a-rectangle.md)
