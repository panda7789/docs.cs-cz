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
ms.openlocfilehash: b80708f0ce722b1809fe49190639231e7e4c8329
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320057"
---
# <a name="how-to-fill-a-shape-with-a-hatch-pattern"></a>Postupy: Vyplnění obrazce pomocí nesouvislého vzoru
Vzor šrafování se skládá ze dvou barev: jednoho pro pozadí a jeden pro čáry, které tvoří vzorek na pozadí. Chcete-li vyplnit uzavřený tvar pomocí vzoru šrafování, použijte objekt <xref:System.Drawing.Drawing2D.HatchBrush>. Následující příklad ukazuje, jak vyplnit elipsu vzorem šrafování:  
  
## <a name="example"></a>Příklad  
 Konstruktor <xref:System.Drawing.Drawing2D.HatchBrush.%23ctor%2A> přijímá tři argumenty: styl šrafování, barva šrafované čáry a barvu pozadí. Argument stylu šrafování může být libovolná hodnota z výčtu <xref:System.Drawing.Drawing2D.HatchStyle>. Výčet <xref:System.Drawing.Drawing2D.HatchStyle> obsahuje více než 50 prvků; v následujícím seznamu jsou uvedeny některé z těchto prvků:  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Horizontal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Vertical>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.ForwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.BackwardDiagonal>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.Cross>  
  
- <xref:System.Drawing.Drawing2D.HatchStyle.DiagonalCross>  
  
 Následující ilustrace znázorňuje Vyplněnou elipsu.  
  
  ![Snímek obrazovky toho, jak elipsa vyplněná vzorem šrafování vypadá jako.](./media/how-to-fill-a-shape-with-a-hatch-pattern/ellipse-filled-hatch.png "hatch1")
  
 [!code-csharp[System.Drawing.UsingABrush#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.UsingABrush#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je určený pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> @ no__t-1, což je parametr obslužné rutiny události <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Viz také:

- [Použití štětce k vyplnění obrazců](using-a-brush-to-fill-shapes.md)
