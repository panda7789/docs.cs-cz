---
title: "Postupy: Kreslení textu pomocí GDI"
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
- GDI [Windows Forms], drawing text [Windows Forms]
- text [Windows Forms], drawing with TextRenderer
- drawing [Windows Forms], text
- Windows Forms, drawing text with GDI
ms.assetid: 2a19fe5d-2ace-451c-94db-01cb1118ef7b
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6c7fb4d8c6bd93481935a9f2ef7dd4b34af7e71
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-draw-text-with-gdi"></a><span data-ttu-id="9d94e-102">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="9d94e-102">How to: Draw Text with GDI</span></span>
<span data-ttu-id="9d94e-103">S <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metoda v <xref:System.Windows.Forms.TextRenderer> třída, dostanete [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] funkce pro kreslení textu na formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9d94e-103">With the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method in the <xref:System.Windows.Forms.TextRenderer> class, you can access [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] functionality for drawing text on a form or control.</span></span> [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)]<span data-ttu-id="9d94e-104">vykreslování textu obvykle nabízí lepší výkon a přesnější text měření než [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9d94e-104"> text rendering typically offers better performance and more accurate text measuring than [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d94e-105"><xref:System.Windows.Forms.TextRenderer.DrawText%2A> Metody <xref:System.Windows.Forms.TextRenderer> třídy nejsou podporovány pro tisk.</span><span class="sxs-lookup"><span data-stu-id="9d94e-105">The <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods of the <xref:System.Windows.Forms.TextRenderer> class are not supported for printing.</span></span> <span data-ttu-id="9d94e-106">Při tisku, vždy nutné použít <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="9d94e-106">When printing, always use the <xref:System.Drawing.Graphics.DrawString%2A> methods of the <xref:System.Drawing.Graphics> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d94e-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d94e-107">Example</span></span>  
 <span data-ttu-id="9d94e-108">Následující příklad kódu ukazuje, jak kreslení textu na více řádků v obdélníku pomocí <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9d94e-108">The following code example demonstrates how to draw text on multiple lines within a rectangle using the <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
 [!code-csharp[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/CS/Form1.cs#7)]
 [!code-vb[System.Windows.Forms.TextRendererExamples#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TextRendererExamples/VB/Form1.vb#7)]  
  
 <span data-ttu-id="9d94e-109">K vykreslení textu pomocí <xref:System.Windows.Forms.TextRenderer> třídy, musíte <xref:System.Drawing.IDeviceContext>, například <xref:System.Drawing.Graphics> a <xref:System.Drawing.Font>, umístění k vykreslení a barvy, ve kterém mají být vykresleny textu.</span><span class="sxs-lookup"><span data-stu-id="9d94e-109">To render text with the <xref:System.Windows.Forms.TextRenderer> class, you need an <xref:System.Drawing.IDeviceContext>, such as a <xref:System.Drawing.Graphics> and a <xref:System.Drawing.Font>, a location to draw the text, and the color in which it should be drawn.</span></span> <span data-ttu-id="9d94e-110">Volitelně můžete zadat text formátování s použitím <xref:System.Windows.Forms.TextFormatFlags> výčtu.</span><span class="sxs-lookup"><span data-stu-id="9d94e-110">Optionally, you can specify the text formatting by using the <xref:System.Windows.Forms.TextFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="9d94e-111">Další informace o získání <xref:System.Drawing.Graphics>, najdete v části [postupy: vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span><span class="sxs-lookup"><span data-stu-id="9d94e-111">For more information about obtaining a <xref:System.Drawing.Graphics>, see [How to: Create Graphics Objects for Drawing](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md).</span></span> <span data-ttu-id="9d94e-112">Další informace o vytváření <xref:System.Drawing.Font>, najdete v části [postupy: vytváření rodin písem a písem](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span><span class="sxs-lookup"><span data-stu-id="9d94e-112">For more information about constructing a <xref:System.Drawing.Font>, see [How to: Construct Font Families and Fonts](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9d94e-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9d94e-113">Compiling the Code</span></span>  
 <span data-ttu-id="9d94e-114">V předchozím příkladu kódu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="9d94e-114">The preceding code example is designed for use with Windows Forms, and it requires the <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d94e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d94e-115">See Also</span></span>  
 <xref:System.Windows.Forms.TextRenderer>  
 <xref:System.Drawing.Font>  
 <xref:System.Drawing.Color>  
 <xref:System.Drawing.Color>  
 [<span data-ttu-id="9d94e-116">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="9d94e-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
