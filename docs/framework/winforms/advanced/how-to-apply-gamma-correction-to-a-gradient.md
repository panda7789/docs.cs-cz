---
title: 'Postupy: Použití gama korekce na přechod'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gradient brushes [Windows Forms], gamma correction
- gradients [Windows Forms], gamma correction
ms.assetid: da4690e7-5fac-4fd2-b3f0-5cb35c165b92
ms.openlocfilehash: 7290b7901714e9b71bda3f85f930f5331b8fd4ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59077326"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Postupy: Použití gama korekce na přechod
Můžete povolit gama korekce na štětec lineárního přechodu nastavením stopy <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `true`. Korekce gama lze zakázat nastavením <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `false`. Korekce gama je ve výchozím nastavení zakázána.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří štětec lineárního přechodu a používá tento štětce k vyplnění dvou obdélníků. První obdélníku je vyplněný bez gama korekce a druhý obdélníku je vyplněna gama korekce.  
  
 Následující obrázek znázorňuje dvě plného obdélníků. Horní obdélník, který nemá gama korekce, zobrazí se tmavě uprostřed. Zdá se, že dolní části obdélníku, jehož gama korekce mít další míra jednotné.  
  
 ![Gradient](./media/gammagradient1.png "gammagradient1")  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.LinearGradientBrush>
- [Použití štětce přechodu k vyplnění obrazců](using-a-gradient-brush-to-fill-shapes.md)
