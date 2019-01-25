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
ms.openlocfilehash: 4afe3eb7c3525dac856751331117e0980063faad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54602946"
---
# <a name="how-to-draw-wrapped-text-in-a-rectangle"></a><span data-ttu-id="114a5-102">Postupy: Kreslení zalomeného textu do obdélníku</span><span class="sxs-lookup"><span data-stu-id="114a5-102">How to: Draw Wrapped Text in a Rectangle</span></span>
<span data-ttu-id="114a5-103">Můžete nakreslit zalamování textu do obdélníku pomocí <xref:System.Drawing.Graphics.DrawString%2A> přetížené metody <xref:System.Drawing.Graphics> třídu, která přijímá <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.RectangleF> parametru.</span><span class="sxs-lookup"><span data-stu-id="114a5-103">You can draw wrapped text in a rectangle by using the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method of the <xref:System.Drawing.Graphics> class that takes a <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF> parameter.</span></span> <span data-ttu-id="114a5-104">Budete taky používat <xref:System.Drawing.Brush> a <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="114a5-104">You will also use a <xref:System.Drawing.Brush> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="114a5-105">Můžete také nakreslit zalamování textu do obdélníku pomocí <xref:System.Windows.Forms.TextRenderer.DrawText%2A> přetížené metody <xref:System.Windows.Forms.TextRenderer> , která přijímá <xref:System.Drawing.Rectangle> a <xref:System.Windows.Forms.TextFormatFlags> parametru.</span><span class="sxs-lookup"><span data-stu-id="114a5-105">You can also draw wrapped text in a rectangle by using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method of the <xref:System.Windows.Forms.TextRenderer> that takes a <xref:System.Drawing.Rectangle> and a <xref:System.Windows.Forms.TextFormatFlags> parameter.</span></span> <span data-ttu-id="114a5-106">Budete taky používat <xref:System.Drawing.Color> a <xref:System.Drawing.Font>.</span><span class="sxs-lookup"><span data-stu-id="114a5-106">You will also use a <xref:System.Drawing.Color> and a <xref:System.Drawing.Font>.</span></span>  
  
 <span data-ttu-id="114a5-107">Následující obrázek znázorňuje výstup textu vykreslen v obdélníku použijete <xref:System.Drawing.Graphics.DrawString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="114a5-107">The following illustration shows the output of text drawn in the rectangle when you use the <xref:System.Drawing.Graphics.DrawString%2A> method.</span></span>  
  
 <span data-ttu-id="114a5-108">![Písma textu](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")</span><span class="sxs-lookup"><span data-stu-id="114a5-108">![Fonts Text](../../../../docs/framework/winforms/advanced/media/csfontstext2.png "csfontstext2")</span></span>  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="114a5-109">Kreslení zalomeného textu do obdélníku pomocí GDI +</span><span class="sxs-lookup"><span data-stu-id="114a5-109">To draw wrapped text in a rectangle with GDI+</span></span>  
  
1.  <span data-ttu-id="114a5-110">Použití <xref:System.Drawing.Graphics.DrawString%2A> přetížené metody předáním text, který má <xref:System.Drawing.Rectangle> nebo <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> a <xref:System.Drawing.Brush>.</span><span class="sxs-lookup"><span data-stu-id="114a5-110">Use the <xref:System.Drawing.Graphics.DrawString%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle> or <xref:System.Drawing.RectangleF>, <xref:System.Drawing.Font> and <xref:System.Drawing.Brush>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#50)]
     [!code-vb[System.Drawing.AlignDrawnText#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#50)]  
  
### <a name="to-draw-wrapped-text-in-a-rectangle-with-gdi"></a><span data-ttu-id="114a5-111">Kreslení zalomeného textu do obdélníku pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="114a5-111">To draw wrapped text in a rectangle with GDI</span></span>  
  
1.  <span data-ttu-id="114a5-112">Použití <xref:System.Windows.Forms.TextFormatFlags> hodnotu výčtu text by měl být uzavřen s <xref:System.Windows.Forms.TextRenderer.DrawText%2A> přetížené metody předáním text, který má <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> a <xref:System.Drawing.Color>.</span><span class="sxs-lookup"><span data-stu-id="114a5-112">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration value to specify the text should be wrapped with the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> overloaded method, passing the text you want, <xref:System.Drawing.Rectangle>, <xref:System.Drawing.Font> and <xref:System.Drawing.Color>.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#60)]
     [!code-vb[System.Drawing.AlignDrawnText#60](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#60)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="114a5-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="114a5-113">Compiling the Code</span></span>  
 <span data-ttu-id="114a5-114">Vyžadovat v předchozích příkladech:</span><span class="sxs-lookup"><span data-stu-id="114a5-114">The previous examples require:</span></span>  
  
-   <span data-ttu-id="114a5-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="114a5-115"><xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="114a5-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="114a5-116">See also</span></span>
- [<span data-ttu-id="114a5-117">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="114a5-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="114a5-118">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="114a5-118">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [<span data-ttu-id="114a5-119">Postupy: Vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="114a5-119">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
- [<span data-ttu-id="114a5-120">Postupy: Kreslení textu v určeném umístění</span><span class="sxs-lookup"><span data-stu-id="114a5-120">How to: Draw Text at a Specified Location</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-at-a-specified-location.md)
