---
title: 'Postupy: Kreslení textu pomocí GDI'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
ms.openlocfilehash: 3d5b79e82185c044314ff8807b86835ef6a87c45
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505904"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="41f93-102">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="41f93-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="41f93-103">S <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metodu <xref:System.Windows.Forms.TextRenderer> třídy, funkce se zpřístupní GDI pro kreslení textu na formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="41f93-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access GDI functionality for drawing text on a form or control.</span></span> <span data-ttu-id="41f93-104">Vykreslování textu GDI obvykle nabízí lepší výkon a přesnější text měření než rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="41f93-104">GDI text rendering typically offers better performance and more accurate text measuring than GDI+.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="41f93-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> třídy nejsou podporovány pro tisk.</span><span class="sxs-lookup"><span data-stu-id="41f93-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="41f93-106">Při tisku, vždy používejte <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="41f93-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41f93-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="41f93-107">Example</span></span>  
 <span data-ttu-id="41f93-108">Následující příklad kódu ukazuje, jak na více řádků v rámci obdélníku pomocí vykreslení textu <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="41f93-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="41f93-109">K vykreslení textu pomocí <xref:System.Windows.Forms.TextRenderer> třídy, je nutné <xref:System.Drawing.IDeviceContext>, například <xref:System.Drawing.Graphics> a <xref:System.Drawing.Font>, umístění pro kreslení textu a barvy, ve kterém má být vykreslena.</span><span class="sxs-lookup"><span data-stu-id="41f93-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="41f93-110">Volitelně můžete zadat formátování s použitím textu <xref:System.Windows.Forms.TextFormatFlags> výčtu.</span><span class="sxs-lookup"><span data-stu-id="41f93-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="41f93-111">Další informace o získání <xref:System.Drawing.Graphics>, naleznete v tématu [jak: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="41f93-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="41f93-112">Další informace o vytváření <xref:System.Drawing.Font>, naleznete v tématu [jak: Vytváření rodin písem a písem](how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="41f93-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="41f93-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="41f93-113">Compiling the Code</span></span>  
 <span data-ttu-id="41f93-114">V předchozím příkladu kódu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="41f93-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41f93-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41f93-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="41f93-116">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="41f93-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
