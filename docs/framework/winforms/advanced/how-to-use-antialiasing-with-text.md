---
title: 'Postupy: Použití vyhlazení s textem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- strings [Windows Forms], smoothing drawn
- antialiasing [Windows Forms], using with text
- text [Windows Forms], smoothing
- text [Windows Forms], antialiasing
- strings [Windows Forms], antialiasing when drawing
ms.assetid: 48fc34f3-f236-4b01-a0cb-f0752e6d22ae
ms.openlocfilehash: 64b1c27b9e8b7d405dde5add105ff2e682f8ad87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534101"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="c04b5-102">Postupy: Použití vyhlazení s textem</span><span class="sxs-lookup"><span data-stu-id="c04b5-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="c04b5-103">*Vyhlazení* odkazuje na vyhlazování nerovné okraje vykresleného obrázků a textu ke zlepšení jejich vzhled nebo čitelnost.</span><span class="sxs-lookup"><span data-stu-id="c04b5-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="c04b5-104">S managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy, můžete vygenerovat vysoce kvalitní antialiased text, jakož i nižší kvality text.</span><span class="sxs-lookup"><span data-stu-id="c04b5-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="c04b5-105">Vyšší kvalitu vykreslování obvykle trvá zpracování déle než nižší kvality vykreslování.</span><span class="sxs-lookup"><span data-stu-id="c04b5-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="c04b5-106">Chcete-li nastavit úroveň kvality text, nastavte <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnost <xref:System.Drawing.Graphics> na jeden z elementů <xref:System.Drawing.Text.TextRenderingHint> výčet</span><span class="sxs-lookup"><span data-stu-id="c04b5-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="c04b5-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="c04b5-107">Example</span></span>  
 <span data-ttu-id="c04b5-108">Následující příklad kódu kreslení textu pomocí nastavení dvou různých kvality.</span><span class="sxs-lookup"><span data-stu-id="c04b5-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
 
 <span data-ttu-id="c04b5-109">Výstup tohoto ukázkového kódu na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="c04b5-109">The following illustration shows the output of the example code:</span></span>  
  
 <span data-ttu-id="c04b5-110">![Písma textu](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span><span class="sxs-lookup"><span data-stu-id="c04b5-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c04b5-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c04b5-111">Compiling the Code</span></span>  
 <span data-ttu-id="c04b5-112">V předchozím příkladu kódu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="c04b5-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c04b5-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c04b5-113">See also</span></span>
- [<span data-ttu-id="c04b5-114">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="c04b5-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
