---
title: 'Postupy: Zarovnání vykresleného textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
ms.openlocfilehash: 1cd6566e5eb5b60128206458c6e82b8eecf5492e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632371"
---
# <a name="how-to-align-drawn-text"></a><span data-ttu-id="d362f-102">Postupy: Zarovnání vykresleného textu</span><span class="sxs-lookup"><span data-stu-id="d362f-102">How to: Align Drawn Text</span></span>
<span data-ttu-id="d362f-103">Při provádění vlastní kreslení, můžete často center vykreslený text na formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="d362f-103">When you perform custom drawing, you may often want to center drawn text on a form or control.</span></span> <span data-ttu-id="d362f-104">Je možné snadno zarovnat text nakreslit <xref:System.Drawing.Graphics.DrawString%2A> nebo <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody vytvořením správný objekt formátování a nastavení příznaků příslušném formátu.</span><span class="sxs-lookup"><span data-stu-id="d362f-104">You can easily align text drawn with the <xref:System.Drawing.Graphics.DrawString%2A> or <xref:System.Windows.Forms.TextRenderer.DrawText%2A> methods by creating the correct formatting object and setting the appropriate format flags.</span></span>  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a><span data-ttu-id="d362f-105">Chcete-li nakreslit na střed textu pomocí GDI + (tkanicí stažení)</span><span class="sxs-lookup"><span data-stu-id="d362f-105">To draw centered text with GDI+ (DrawString)</span></span>  
  
1.  <span data-ttu-id="d362f-106">Použití <xref:System.Drawing.StringFormat> příslušnou <xref:System.Drawing.Graphics.DrawString%2A> metoda zadat text na střed.</span><span class="sxs-lookup"><span data-stu-id="d362f-106">Use a <xref:System.Drawing.StringFormat> with the appropriate <xref:System.Drawing.Graphics.DrawString%2A> method to specify centered text.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a><span data-ttu-id="d362f-107">Chcete-li nakreslit na střed textu pomocí GDI (DrawText)</span><span class="sxs-lookup"><span data-stu-id="d362f-107">To draw centered text with GDI (DrawText)</span></span>  
  
1.  <span data-ttu-id="d362f-108">Použití <xref:System.Windows.Forms.TextFormatFlags> výčtu pro obtékání také vertikální i horizontální zarovnání textu příslušnou <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="d362f-108">Use the <xref:System.Windows.Forms.TextFormatFlags> enumeration for wrapping as well as vertically and horizontally centering text with the appropriate <xref:System.Windows.Forms.TextRenderer.DrawText%2A> method.</span></span>  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d362f-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d362f-109">Compiling the Code</span></span>  
 <span data-ttu-id="d362f-110">V předchozích příkladech kódu jsou určeny k použití pomocí Windows Forms a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="d362f-110">The preceding code examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs>`e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d362f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d362f-111">See also</span></span>
- [<span data-ttu-id="d362f-112">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="d362f-112">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)
- [<span data-ttu-id="d362f-113">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="d362f-113">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)
- [<span data-ttu-id="d362f-114">Postupy: Vytváření rodin písem a písem</span><span class="sxs-lookup"><span data-stu-id="d362f-114">How to: Construct Font Families and Fonts</span></span>](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
