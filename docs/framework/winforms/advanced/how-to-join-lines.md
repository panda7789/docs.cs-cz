---
title: 'Postupy: Spojení čar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- miter line join style
- bevel line join style
- line join
- drawing [Windows Forms], joining lines
- GraphicsPath object
- round line join style
- lines [Windows Forms], joining
- graphics [Windows Forms], joining lines
ms.assetid: 9fc480c2-3c75-4fd1-8ab5-296a99e820e2
ms.openlocfilehash: cecced7b32af7187cb1ef072921f0ff28f04adad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-join-lines"></a>Postupy: Spojení čar
Spojení čar je běžné oblasti, která je tvořen dvěma řádky, jehož elementy end splňují nebo překrývat. [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje tři styly řádku spojení: ostrý bevelova křivka a zaokrouhleno. Čára – styl propojení je vlastnost <xref:System.Drawing.Pen> třídy. Pokud zadáte styl řádku spojení <xref:System.Drawing.Pen> objektu, že styl spojení se použije na všechny řádky, které jsou připojené v žádném <xref:System.Drawing.Drawing2D.GraphicsPath> objekt vykreslovány pomocí pera.  
  
 Následující obrázek znázorňuje výsledky příklad spojení zkosení řádku.  
  
 ![Pera](../../../../docs/framework/winforms/advanced/media/pens5.gif "pens5")  
  
## <a name="example"></a>Příklad  
 Styl čáry spojení můžete zadat pomocí <xref:System.Drawing.Pen.LineJoin%2A> vlastnost <xref:System.Drawing.Pen> třídy. Příklad ukazuje zkosení řádku spojení mezi na vodorovném řádku a svislá čára. V následujícím kódu, hodnota <xref:System.Drawing.Drawing2D.LineJoin.Bevel> přiřazené <xref:System.Drawing.Pen.LineJoin%2A> vlastnost je členem skupiny <xref:System.Drawing.Drawing2D.LineJoin> výčtu. Ostatní členové <xref:System.Drawing.Drawing2D.LineJoin> jsou výčtu <xref:System.Drawing.Drawing2D.LineJoin.Miter> a <xref:System.Drawing.Drawing2D.LineJoin.Round>.  
  
 [!code-csharp[System.Drawing.UsingAPen#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.UsingAPen#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
