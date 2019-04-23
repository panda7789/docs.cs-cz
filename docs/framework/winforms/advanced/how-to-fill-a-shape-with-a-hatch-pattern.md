---
title: 'Postupy: Vyplnění obrazce pomocí nesouvislého vzoru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- patterns [Windows Forms], adding to shapes
- shapes [Windows Forms], filling with patterns
- brushes [Windows Forms], using hatch brushes
ms.assetid: 9c8300ff-187b-404f-af1f-ebd499f5b16f
ms.openlocfilehash: f5399c4151b335090f4b93be041375b8c2781afa
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118115"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Postupy: Vyplnění obrazce pomocí nesouvislého vzoru
Nesouvislého vzoru se provádí stínováním dvěma barvami: jeden pro na pozadí a jeden pro řádky, které tvoří vzor přes na pozadí. Chcete-li vyplnění uzavřené obrazce pomocí nesouvislého vzoru, použijte <xref:System.Drawing.Drawing2D.HatchBrush> objektu. Následující příklad ukazuje, jak vyplnit elipsu pomocí nesouvislého vzoru:  
  
## <a name="example"></a>Příklad  
 <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> Konstruktor má tři argumenty: Styl šrafování, barva šrafování čáry a barvu pozadí. Styl šrafování argument může být libovolná hodnota od <xref:System.Drawing.Drawing2D.HatchStyle> výčtu. Existuje více než 50 elementů v <xref:System.Drawing.Drawing2D.HatchStyle> výčet; některé z těchto elementů jsou uvedeny v následujícím seznamu:  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
-   <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Následující obrázek znázorňuje vyplněnou elipsu.  
  
 ![Šrafovaných vzor](./media/hatch1.png "hatch1")  
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Použití štětce k vyplnění obrazců](using-a-brush-to-fill-shapes.md)
