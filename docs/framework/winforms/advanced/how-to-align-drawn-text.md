---
title: "Postupy: Zarovnání vykresleného textu"
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
- text [Windows Forms], aligning
- Windows Forms, aligning drawn text
ms.assetid: 83c10a81-1a90-4b5c-98aa-2c6c4b280079
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6be28641073bf430b1dc51c428228d0fb114d4cc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-align-drawn-text"></a>Postupy: Zarovnání vykresleného textu
Při provádění vlastní kreslení, můžete často center vykresleného textu ve formuláři nebo ovládací prvek. Můžete snadno zarovnat text vykreslené s <xref:System.Drawing.Graphics.DrawString%2A> nebo <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metody vytváření správné formátování objektu a nastavením příznaků příslušný formát.  
  
### <a name="to-draw-centered-text-with-gdi-drawstring"></a>Kreslení zarovnaný na střed textu pomocí GDI + (tkanicí stažení)  
  
1.  Použití <xref:System.Drawing.StringFormat> s příslušnou <xref:System.Drawing.Graphics.DrawString%2A> metoda zadat text zarovnaný na střed.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#10)]
     [!code-vb[System.Drawing.AlignDrawnText#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#10)]  
  
### <a name="to-draw-centered-text-with-gdi-drawtext"></a>Kreslení zarovnaný na střed textu pomocí GDI (DrawText)  
  
1.  Použití <xref:System.Windows.Forms.TextFormatFlags> výčtu pro zabalení a také vodorovně a svisle zarovnání textu pomocí odpovídající <xref:System.Windows.Forms.TextRenderer.DrawText%2A> metoda.  
  
     [!code-csharp[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/CS/Form1.cs#20)]
     [!code-vb[System.Drawing.AlignDrawnText#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlignDrawnText/VB/Form1.vb#20)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozích příkladech kódu jsou navrženy pro používání s formuláři Windows a vyžadují <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Kreslení textu pomocí GDI](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)  
 [Použití písem a textu](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [Postupy: Vytváření rodin písem a písem](../../../../docs/framework/winforms/advanced/how-to-construct-font-families-and-fonts.md)
