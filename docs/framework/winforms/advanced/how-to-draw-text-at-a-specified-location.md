---
title: 'Postupy: Kreslení textu v určeném umístění'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing at specified locations [Windows Forms]
- drawing text
- drawing text [Windows Forms], specified locations [Windows Forms]
- Windows Forms, drawing text at a specified location
ms.assetid: 60816423-1c38-465e-980d-2c2b64d74086
ms.openlocfilehash: 3f54da182e6cc1489eadba6fa1d3cef683c3ba51
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59075506"
---
# <a name="how-to-draw-text-at-a-specified-location"></a><span data-ttu-id="07dd7-102">Postupy: Kreslení textu v určeném umístění</span><span class="sxs-lookup"><span data-stu-id="07dd7-102">How to: Draw Text at a Specified Location</span></span>
<span data-ttu-id="07dd7-103">Při provádění vlastní kreslení můžete nakreslit text v jedné vodorovnou horizontální čáru od k určitému bodu.</span><span class="sxs-lookup"><span data-stu-id="07dd7-103">When you perform custom drawing, you can draw text in a single horizontal line starting at a specified point.</span></span> <span data-ttu-id="07dd7-104">Tímto způsobem můžete nakreslit text pomocí <xref:System.Drawing.Graphics.DrawString%2A> přetížené metody <xref:System.Drawing.Graphics> třídu, která přijímá <xref:System.Drawing.Point> nebo <xref:System.Drawing.PointF> parametru.</span><span class="sxs-lookup"><span data-stu-id="07dd7-104">You can draw text in this manner by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Point> or <xref:System.Drawing.PointF> parameter.</span></span> <span data-ttu-id="07dd7-105"><xref:System.Drawing.Graphics.DrawString%2A> Také vyžaduje metodu <xref:System.Drawing.Brush> a</span><span class="sxs-lookup"><span data-stu-id="07dd7-105">The <xref:System.Drawing.Graphics.DrawString%2A> method also requires a <xref:System.Drawing.Brush> and</span></span> <xref:System.Drawing.Font>  
  
 <span data-ttu-id="07dd7-106">Můžete také použít <xref:System.Windows.Forms.TextRenderer.DrawText%2A> přetížené metody <xref:System.Windows.Forms.TextRenderer> , která přijímá <xref:System.Drawing.Point>.</span><span class="sxs-lookup"><span data-stu-id="07dd7-106">You can also use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Point>.</span></span> <xref:System.Windows.Forms.TextRenderer.DrawText%2A> <span data-ttu-id="07dd7-107">také vyžaduje <xref:System.Drawing.Color> a <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="07dd7-107">also requires a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="07dd7-108">Následující obrázek znázorňuje výstup textu při použití vykreslit k určitému bodu <xref:System.Drawing.Graphics.DrawString%2A> přetížené metody.</span><span class="sxs-lookup"><span data-stu-id="07dd7-108">The following illustration shows the output of text drawn at a specified point when you use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method.</span></span>  
  
 ![Snímek obrazovky zobrazující výstup textu v určeném okamžiku.](./media/how-to-draw-text-at-a-specified-location/font-text-specified-point.png)  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="07dd7-110">Chcete-li nakreslit řádek textu pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="07dd7-110">To draw a line of text with GDI+</span></span>  
  
1.  <span data-ttu-id="07dd7-111">Použití <xref:System.Drawing.Graphics.DrawString%2A> předejte text, který má <xref:System.Drawing.Point> nebo <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, a <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="07dd7-111">Use the <xref:System.Drawing.Graphics.DrawString%2A> method, passing the text you want, <xref:System.Drawing.Point> or <xref:System.Drawing.PointF>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#30)]
     [!code-vb[System.Drawing.AlignDrawnText#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#30)]  
  
### <a name="to-draw-a-line-of-text-with-gdi"></a><span data-ttu-id="07dd7-112">Chcete-li nakreslit řádek textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="07dd7-112">To draw a line of text with GDI</span></span>  
  
1.  <span data-ttu-id="07dd7-113">Použití <xref:System.Windows.Forms.TextRenderer.DrawText%2A> předejte text, který má <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, a <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="07dd7-113">Use the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method, passing the text you want, <xref:System.Drawing.Point>, <xref:System.Drawing.Font>, and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#40](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#40)]
     [!code-vb[System.Drawing.AlignDrawnText#40](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#40)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="07dd7-114">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="07dd7-114">Compiling the Code</span></span>  
 <span data-ttu-id="07dd7-115">Vyžadovat v předchozích příkladech:</span><span class="sxs-lookup"><span data-stu-id="07dd7-115">The previous examples require:</span></span>  
  
-   <xref:System.Windows.Forms.PaintEventArgs>  `e`<span data-ttu-id="07dd7-116">, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="07dd7-116">, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07dd7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="07dd7-117">See also</span></span>

- [<span data-ttu-id="07dd7-118">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="07dd7-118">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="07dd7-119">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="07dd7-119">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="07dd7-120">Postupy: Vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="07dd7-120">How to: Construct Font Families and Fonts</span></span>](how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="07dd7-121">Postupy: Kreslení zalomeného textu do obdélníku</span><span class="sxs-lookup"><span data-stu-id="07dd7-121">How to: Draw Wrapped Text in a Rectangle</span></span>](how-to-draw-wrapped-text-in-a-rectangle.md)
