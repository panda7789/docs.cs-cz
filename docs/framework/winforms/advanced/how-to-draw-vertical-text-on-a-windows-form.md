---
title: 'Postupy: Kreslení svislého textu na formuláři Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- StringFormat.FormatFlags
- Graphics.DrawString
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- strings [Windows Forms], drawing vertical
- text [Windows Forms], drawing
- text [Windows Forms], vertical text
ms.assetid: 717a6131-00f6-4373-b574-9894e8317799
ms.openlocfilehash: 660d7abae5463c976e60b7d9caeae8a798d122ca
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626175"
---
# <a name="how-to-draw-vertical-text-on-a-windows-form"></a><span data-ttu-id="62195-102">Postupy: Kreslení svislého textu na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="62195-102">How to: Draw Vertical Text on a Windows Form</span></span>
<span data-ttu-id="62195-103">Následující příklad kódu ukazuje, jak s použitím kreslení svislého textu ve formuláři <xref:System.Drawing.Graphics.DrawString%2A> metoda <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="62195-103">The following code example shows how to draw vertical text on a form by using the <xref:System.Drawing.Graphics.DrawString%2A> method of <xref:System.Drawing.Graphics>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62195-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="62195-104">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#8)]
 [!code-csharp[System.Drawing.ConceptualHowTos#8](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#8)]
 [!code-vb[System.Drawing.ConceptualHowTos#8](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#8)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="62195-105">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="62195-105">Compiling the Code</span></span>  
 <span data-ttu-id="62195-106">Tuto metodu nelze volat <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="62195-106">You cannot call this method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="62195-107">Vykreslený obsah aktivním, pokud je velikost nebo zakryto jiný formulář. formuláře.</span><span class="sxs-lookup"><span data-stu-id="62195-107">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="62195-108">Chcete-li obsah automaticky repaint, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="62195-108">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="62195-109">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="62195-109">Robust Programming</span></span>  
 <span data-ttu-id="62195-110">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="62195-110">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="62195-111">Arial písmo není nainstalováno.</span><span class="sxs-lookup"><span data-stu-id="62195-111">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62195-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62195-112">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="62195-113">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="62195-113">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="62195-114">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="62195-114">Using Fonts and Text</span></span>](using-fonts-and-text.md)
