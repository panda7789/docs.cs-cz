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
ms.openlocfilehash: e812e441233c1d29a67dac639048e20a659549f0
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753565"
---
# <a name="how-to-apply-gamma-correction-to-a-gradient"></a>Postupy: Použití gama korekce na přechod
Můžete povolit gama korekce na štětec lineárního přechodu nastavením stopy <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `true`. Korekce gama lze zakázat nastavením <xref:System.Drawing.Drawing2D.LinearGradientBrush.GammaCorrection%2A> vlastnost `false`. Korekce gama je ve výchozím nastavení zakázána.  
  
## <a name="example"></a>Příklad  

V následujícím příkladu je metoda, která je volána z ovládacího prvku <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Tento příklad vytvoří štětec lineárního přechodu a používá tento štětce k vyplnění dvou obdélníků. První obdélníku je vyplněný bez gama korekce a druhý obdélníku je vyplněna gama korekce.  
  
 Následující obrázek znázorňuje dvě plného obdélníků. Horní obdélník, který nemá gama korekce, zobrazí se tmavě uprostřed. Zdá se, že dolní části obdélníku, jehož gama korekce mít další míra jednotné.  
  
 ![Dva vyplněný přechodu obdélníky a nemusíte gama korekce.](./media/how-to-apply-gamma-correction-to-a-gradient/two-rectangles-gamma-gradient.png)  
  
 [!code-csharp[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingaGradientBrush#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingaGradientBrush/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Drawing2D.LinearGradientBrush?displayProperty=nameWithType>
- [Použití štětce přechodu k vyplnění obrazců](using-a-gradient-brush-to-fill-shapes.md)
