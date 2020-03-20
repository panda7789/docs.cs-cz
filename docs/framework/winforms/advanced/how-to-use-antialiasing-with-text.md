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
ms.openlocfilehash: 632ed329173d134495a424b34ca7c71e402607bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182474"
---
# <a name="how-to-use-antialiasing-with-text"></a><span data-ttu-id="724f6-102">Postupy: Použití vyhlazení s textem</span><span class="sxs-lookup"><span data-stu-id="724f6-102">How to: Use Antialiasing with Text</span></span>
<span data-ttu-id="724f6-103">*Vyhlazení* mů e být namátkovat zubaté okraje nakreslené grafiky a textu, aby se zlepšil jejich vzhled nebo čitelnost.</span><span class="sxs-lookup"><span data-stu-id="724f6-103">*Antialiasing* refers to the smoothing of jagged edges of drawn graphics and text to improve their appearance or readability.</span></span> <span data-ttu-id="724f6-104">Díky spravovaným třídám GDI+ můžete vykreslit vysoce kvalitní vyhlazovaný text a také text nižší kvality.</span><span class="sxs-lookup"><span data-stu-id="724f6-104">With the managed GDI+ classes, you can render high quality antialiased text, as well as lower quality text.</span></span> <span data-ttu-id="724f6-105">Vykreslování s vyšší kvalitou obvykle trvá déle než vykreslování nižší kvality.</span><span class="sxs-lookup"><span data-stu-id="724f6-105">Typically, higher quality rendering takes more processing time than lower quality rendering.</span></span> <span data-ttu-id="724f6-106">Chcete-li nastavit úroveň kvality <xref:System.Drawing.Graphics.TextRenderingHint%2A> textu, <xref:System.Drawing.Graphics> nastavte vlastnost a <xref:System.Drawing.Text.TextRenderingHint> na jeden z prvků výčtu.</span><span class="sxs-lookup"><span data-stu-id="724f6-106">To set the text quality level, set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property of a <xref:System.Drawing.Graphics> to one of the elements of the <xref:System.Drawing.Text.TextRenderingHint> enumeration</span></span>  
  
## <a name="example"></a><span data-ttu-id="724f6-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="724f6-107">Example</span></span>  
 <span data-ttu-id="724f6-108">Následující příklad kódu nakreslí text se dvěma různými nastaveními kvality.</span><span class="sxs-lookup"><span data-stu-id="724f6-108">The following code example draws text with two different quality settings.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.FontsAndText#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#21)]  

 <span data-ttu-id="724f6-109">Následující obrázek znázorňuje výstup ukázkového kódu:</span><span class="sxs-lookup"><span data-stu-id="724f6-109">The following illustration shows the output of the example code:</span></span>  
  
 ![Snímek obrazovky, který zobrazuje text se dvěma různými nastaveními kvality.](./media/how-to-use-antialiasing-with-text/antialiasing-text-quality-settings.png)  
  
## <a name="compiling-the-code"></a><span data-ttu-id="724f6-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="724f6-111">Compiling the Code</span></span>  
 <span data-ttu-id="724f6-112">Předchozí příklad kódu je určen pro použití s <xref:System.Windows.Forms.PaintEventArgs> `e`windows forms a <xref:System.Windows.Forms.PaintEventHandler>vyžaduje , což je parametr .</span><span class="sxs-lookup"><span data-stu-id="724f6-112">The preceding code example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="724f6-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="724f6-113">See also</span></span>

- [<span data-ttu-id="724f6-114">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="724f6-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
