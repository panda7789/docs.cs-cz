---
title: 'Postupy: Kreslení textu na formuláři Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- forms [Windows Forms], drawing text
- text [Windows Forms], drawing
ms.assetid: 5d2447a9-21a1-4adc-b954-5516f2bb9b2c
ms.openlocfilehash: ae7749deedba03f0a63bb74099d071d5da4fe27e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59172975"
---
# <a name="how-to-draw-text-on-a-windows-form"></a><span data-ttu-id="92306-102">Postupy: Kreslení textu na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="92306-102">How to: Draw Text on a Windows Form</span></span>
<span data-ttu-id="92306-103">Následující příklad kódu ukazuje, jak používat <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> k vykreslení textu ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="92306-103">The following code example shows how to use the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> to draw text on a form.</span></span> <span data-ttu-id="92306-104">Alternativně můžete použít <xref:System.Windows.Forms.TextRenderer> pro kreslení textu ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="92306-104">Alternatively, you can use <xref:System.Windows.Forms.TextRenderer> for drawing text on a form.</span></span> <span data-ttu-id="92306-105">Další informace najdete v tématu [jak: Kreslení textu pomocí GDI](how-to-draw-text-with-gdi.md).</span><span class="sxs-lookup"><span data-stu-id="92306-105">For more information, see [How to: Draw Text with GDI](how-to-draw-text-with-gdi.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92306-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="92306-106">Example</span></span>  
 [!code-cpp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/cpp/form1.cpp#7)]
 [!code-csharp[System.Drawing.ConceptualHowTos#7](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/CS/form1.cs#7)]
 [!code-vb[System.Drawing.ConceptualHowTos#7](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConceptualHowTos/VB/form1.vb#7)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="92306-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="92306-107">Compiling the Code</span></span>  
 <span data-ttu-id="92306-108">Nelze volat <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Windows.Forms.Form.Load> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="92306-108">You cannot call the <xref:System.Drawing.Graphics.DrawString%2A> method in the <xref:System.Windows.Forms.Form.Load> event handler.</span></span> <span data-ttu-id="92306-109">Vykreslený obsah aktivním, pokud je velikost nebo zakryto jiný formulář. formuláře.</span><span class="sxs-lookup"><span data-stu-id="92306-109">The drawn content will not be redrawn if the form is resized or obscured by another form.</span></span> <span data-ttu-id="92306-110">Chcete-li obsah automaticky repaint, by měly přepsat <xref:System.Windows.Forms.Control.OnPaint%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="92306-110">To make your content automatically repaint, you should override the <xref:System.Windows.Forms.Control.OnPaint%2A> method.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="92306-111">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="92306-111">Robust Programming</span></span>  
 <span data-ttu-id="92306-112">Následující podmínky mohou způsobit výjimku:</span><span class="sxs-lookup"><span data-stu-id="92306-112">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="92306-113">Arial písmo není nainstalováno.</span><span class="sxs-lookup"><span data-stu-id="92306-113">The Arial font is not installed.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92306-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92306-114">See also</span></span>

- <xref:System.Drawing.Graphics.DrawString%2A>
- <xref:System.Windows.Forms.TextRenderer.DrawText%2A>
- <xref:System.Drawing.StringFormat.FormatFlags%2A>
- <xref:System.Drawing.StringFormatFlags>
- <xref:System.Windows.Forms.TextFormatFlags>
- <xref:System.Windows.Forms.Control.OnPaint%2A>
- [<span data-ttu-id="92306-115">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="92306-115">Getting Started with Graphics Programming</span></span>](getting-started-with-graphics-programming.md)
- [<span data-ttu-id="92306-116">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="92306-116">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
