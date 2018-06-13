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
ms.openlocfilehash: 842c1fb0b73533fd2e87474b9e8cfa282eba2a70
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33523107"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="a625b-102">Postupy: Použití vyhlazení s textem</span><span class="sxs-lookup"><span data-stu-id="a625b-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="a625b-103">*Vyhlazení* odkazuje na vyhlazování nerovné okraje vykresleného grafiky a text na zlepšení jejich vzhled a přehlednosti.</span><span class="sxs-lookup"><span data-stu-id="a625b-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="a625b-104">S spravovaný [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] třídy, může vykreslit vysoké kvality antialiased text a také nižší kvalitu textu.</span><span class="sxs-lookup"><span data-stu-id="a625b-104">With the managed [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="a625b-105">Vyšší kvalitu vykreslování obvykle trvá zpracování déle než nižší kvalitu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="a625b-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="a625b-106">Úrovně kvality text, nastavit <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnost <xref:System.Drawing.Graphics> na jeden z elementů <xref:System.Drawing.Text.TextRenderingHint> – výčet</span><span class="sxs-lookup"><span data-stu-id="a625b-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="a625b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="a625b-107">Example</span></span>  
 <span data-ttu-id="a625b-108">Následující příklad kódu kreslení textu pomocí dvě jinou kvalitu nastavení.</span><span class="sxs-lookup"><span data-stu-id="a625b-108">The following code example draws text with two different quality settings.</span></span>  
  
 <span data-ttu-id="a625b-109">Následující obrázek znázorňuje výstup cod ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="a625b-109">The following illustration shows the output of the cod example code.</span></span>  
  
 <span data-ttu-id="a625b-110">![Text písem](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span><span class="sxs-lookup"><span data-stu-id="a625b-110">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext10.png "FontsText10")</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a625b-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a625b-111">Compiling the Code</span></span>  
 <span data-ttu-id="a625b-112">V předchozím příkladu kódu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="a625b-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a625b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a625b-113">See Also</span></span>  
 [<span data-ttu-id="a625b-114">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="a625b-114">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
