---
title: 'Postupy: Kreslení zalomeného textu do obdélníku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, drawing text in a rectangle
- text [Windows Forms], drawing in a rectangle
- strings [Windows Forms], drawing in a rectangle
ms.assetid: e1fb432a-dc90-48b5-9b6b-acc14507133d
ms.openlocfilehash: c753be6a200f166e59e1330c7dbcf1fadc7588a6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524970"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="b380e-102">Postupy: Kreslení zalomeného textu do obdélníku</span><span class="sxs-lookup"><span data-stu-id="b380e-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="b380e-103">Zalamování textu můžete kreslení v obdélníku pomocí <xref:System.Drawing.Graphics.DrawString%2A> přetížený metodu <xref:System.Drawing.Graphics> třídu, která přebírá <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.RectangleF> parametr.</span><span class="sxs-lookup"><span data-stu-id="b380e-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="b380e-104">Budete taky používat <xref:System.Drawing.Brush> a <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="b380e-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="b380e-105">Zalamování textu můžete také kreslení v obdélníku pomocí <xref:System.Windows.Forms.TextRenderer.DrawText%2A> přetížený metodu <xref:System.Windows.Forms.TextRenderer> , která má <xref:System.Drawing.Rectangle> a <xref:System.Windows.Forms.TextFormatFlags> parametr.</span><span class="sxs-lookup"><span data-stu-id="b380e-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="b380e-106">Budete taky používat <xref:System.Drawing.Color> a <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="b380e-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="b380e-107">Následující obrázek ukazuje výstup textu vykresluje v obdélníku, při použití <xref:System.Drawing.Graphics.DrawString%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="b380e-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method.</span></span>  
  
 <span data-ttu-id="b380e-108">![Text písem](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")</span><span class="sxs-lookup"><span data-stu-id="b380e-108">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")</span></span>  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="b380e-109">Kreslení zalomeného textu do obdélníku pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="b380e-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1.  <span data-ttu-id="b380e-110">Použití <xref:System.Drawing.Graphics.DrawString%2A> metodu, předávání text, který má, přetížených <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> a <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="b380e-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="b380e-111">Kreslení zalomeného textu do obdélníku pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="b380e-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1.  <span data-ttu-id="b380e-112">Použití <xref:System.Windows.Forms.TextFormatFlags> hodnota výčtu Určuje text by měl být uzavřen s <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metodu, předávání text, který má, přetížených <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> a <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="b380e-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b380e-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b380e-113">Compiling the Code</span></span>  
 <span data-ttu-id="b380e-114">Vyžadovat v předchozích příkladech:</span><span class="sxs-lookup"><span data-stu-id="b380e-114">The previous examples require:</span></span>  
  
-   <span data-ttu-id="b380e-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="b380e-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b380e-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="b380e-116">See Also</span></span>  
 [<span data-ttu-id="b380e-117">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="b380e-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [<span data-ttu-id="b380e-118">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="b380e-118">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="b380e-119">Postupy: Vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="b380e-119">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)  
 [<span data-ttu-id="b380e-120">Postupy: Kreslení textu v určeném umístění</span><span class="sxs-lookup"><span data-stu-id="b380e-120">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
