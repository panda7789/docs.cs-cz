---
title: 'Postupy: Vytvoření svislého textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing vertical
- Windows Forms, drawing vertical text
- strings [Windows Forms], drawing vertical
- vertical text [Windows Forms], drawing
ms.assetid: 50c69046-4188-47d9-b949-cc2610ffd337
ms.openlocfilehash: 86401342625f593945b801f7619ef9ca9681317c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182564"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="8f8da-102">Postupy: Vytvoření svislého textu</span><span class="sxs-lookup"><span data-stu-id="8f8da-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="8f8da-103">Pomocí objektu <xref:System.Drawing.StringFormat> můžete určit, že text bude nakreslen svisle, nikoli vodorovně.</span><span class="sxs-lookup"><span data-stu-id="8f8da-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f8da-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="8f8da-104">Example</span></span>  
 <span data-ttu-id="8f8da-105">Následující příklad přiřadí <xref:System.Drawing.StringFormatFlags.DirectionVertical> hodnotu <xref:System.Drawing.StringFormat.FormatFlags%2A> vlastnosti <xref:System.Drawing.StringFormat> objektu.</span><span class="sxs-lookup"><span data-stu-id="8f8da-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="8f8da-106">Tento <xref:System.Drawing.StringFormat> objekt je <xref:System.Drawing.Graphics.DrawString%2A> předán metodě třídy. <xref:System.Drawing.Graphics></span><span class="sxs-lookup"><span data-stu-id="8f8da-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="8f8da-107">Hodnota <xref:System.Drawing.StringFormatFlags.DirectionVertical> je členem výčtu. <xref:System.Drawing.StringFormatFlags></span><span class="sxs-lookup"><span data-stu-id="8f8da-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="8f8da-108">Následující obrázek znázorňuje svislý text:</span><span class="sxs-lookup"><span data-stu-id="8f8da-108">The following illustration shows the vertical text:</span></span>
  
 ![Grafika znázorněná text svislých písem.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8f8da-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8f8da-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="8f8da-111">Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e` forms a vyžaduje <xref:System.Windows.Forms.PaintEventHandler>, což je parametr .</span><span class="sxs-lookup"><span data-stu-id="8f8da-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f8da-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f8da-112">See also</span></span>

- [<span data-ttu-id="8f8da-113">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="8f8da-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
