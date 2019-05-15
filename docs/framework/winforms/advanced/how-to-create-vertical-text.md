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
ms.openlocfilehash: 009e8e392841ac6b846007a88efc33ef79f56967
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582679"
---
# <a name="how-to-create-vertical-text"></a><span data-ttu-id="96194-102">Postupy: Vytvoření svislého textu</span><span class="sxs-lookup"><span data-stu-id="96194-102">How to: Create Vertical Text</span></span>
<span data-ttu-id="96194-103">Můžete použít <xref:System.Drawing.StringFormat> objektu k určení, že text být vykreslován svisle spíše než vodorovně.</span><span class="sxs-lookup"><span data-stu-id="96194-103">You can use a <xref:System.Drawing.StringFormat> object to specify that text be drawn vertically rather than horizontally.</span></span>  
  
## <a name="example"></a><span data-ttu-id="96194-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="96194-104">Example</span></span>  
 <span data-ttu-id="96194-105">Následující příklad přiřadí hodnotu <xref:System.Drawing.StringFormatFlags.DirectionVertical> k <xref:System.Drawing.StringFormat.FormatFlags%2A> vlastnost <xref:System.Drawing.StringFormat> objektu.</span><span class="sxs-lookup"><span data-stu-id="96194-105">The following example assigns the value <xref:System.Drawing.StringFormatFlags.DirectionVertical> to the <xref:System.Drawing.StringFormat.FormatFlags%2A> property of a <xref:System.Drawing.StringFormat> object.</span></span> <span data-ttu-id="96194-106">Že <xref:System.Drawing.StringFormat> objekt je předán do <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="96194-106">That <xref:System.Drawing.StringFormat> object is passed to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="96194-107">Hodnota <xref:System.Drawing.StringFormatFlags.DirectionVertical> je členem skupiny <xref:System.Drawing.StringFormatFlags> výčtu.</span><span class="sxs-lookup"><span data-stu-id="96194-107">The value <xref:System.Drawing.StringFormatFlags.DirectionVertical> is a member of the <xref:System.Drawing.StringFormatFlags> enumeration.</span></span>  
  
 <span data-ttu-id="96194-108">Následující obrázek znázorňuje svislého textu:</span><span class="sxs-lookup"><span data-stu-id="96194-108">The following illustration shows the vertical text:</span></span> 
  
 ![Obrázek, který zobrazuje svislá písma textu.](./media/how-to-create-vertical-text/vertical-font-text-graphic.png)  
  
 [!code-csharp[System.Drawing.FontsAndText#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.FontsAndText#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="96194-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="96194-110">Compiling the Code</span></span>  
  
- <span data-ttu-id="96194-111">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e` , což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="96194-111">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e` , which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96194-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="96194-112">See also</span></span>

- [<span data-ttu-id="96194-113">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="96194-113">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
