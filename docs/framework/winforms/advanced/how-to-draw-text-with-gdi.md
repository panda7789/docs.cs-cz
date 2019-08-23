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
ms.openlocfilehash: 3ed2b5c94e4a38a5873a34e61287c4038cab5cbb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956545"
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="e09ff-102">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="e09ff-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="e09ff-103"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Pomocí metody<xref:System.Windows.Forms.TextRenderer> ve třídě můžete získat přístup k funkcím GDI pro vykreslování textu ve formuláři nebo ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="e09ff-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access GDI functionality for drawing text on a form or control.</span></span> <span data-ttu-id="e09ff-104">Vykreslování textu GDI obvykle nabízí lepší výkon a přesnější měření textu než GDI+.</span><span class="sxs-lookup"><span data-stu-id="e09ff-104">GDI text rendering typically offers better performance and more accurate text measuring than GDI+.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e09ff-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody<xref:System.Windows.Forms.TextRenderer> třídy nejsou podporovány pro tisk.</span><span class="sxs-lookup"><span data-stu-id="e09ff-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="e09ff-106">Při tisku vždy používejte <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="e09ff-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e09ff-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="e09ff-107">Example</span></span>  
 <span data-ttu-id="e09ff-108">Následující příklad kódu ukazuje, jak kreslit text na více řádcích v rámci obdélníku pomocí <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="e09ff-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="e09ff-109">Chcete-li vykreslit <xref:System.Windows.Forms.TextRenderer> text s třídou, <xref:System.Drawing.IDeviceContext>budete potřebovat, <xref:System.Drawing.Font>například <xref:System.Drawing.Graphics> , a, umístění pro vykreslení textu a barvu, ve které má být vykreslen.</span><span class="sxs-lookup"><span data-stu-id="e09ff-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="e09ff-110">Volitelně můžete určit formátování textu pomocí <xref:System.Windows.Forms.TextFormatFlags> výčtu.</span><span class="sxs-lookup"><span data-stu-id="e09ff-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="e09ff-111">Další informace o tom <xref:System.Drawing.Graphics>, jak získat, najdete v tématu [How to: Vytvoření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="e09ff-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="e09ff-112">Další informace o konstrukci a <xref:System.Drawing.Font>naleznete v tématu [How to: Sestavte rodiny písem](how-to-construct-font-families-and-fonts.md)a písma.</span><span class="sxs-lookup"><span data-stu-id="e09ff-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e09ff-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e09ff-113">Compiling the Code</span></span>  
 <span data-ttu-id="e09ff-114">Předchozí příklad kódu je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, <xref:System.Windows.Forms.PaintEventHandler>který je parametrem.</span><span class="sxs-lookup"><span data-stu-id="e09ff-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e09ff-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e09ff-115">See also</span></span>

- <xref:System.Windows.Forms.TextRenderer>
- <xref:System.Drawing.Font>
- <xref:System.Drawing.Color>
- [<span data-ttu-id="e09ff-116">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="e09ff-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
