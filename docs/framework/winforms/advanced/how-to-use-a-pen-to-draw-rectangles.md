---
title: 'Postupy: Kreslení obdélníků pomocí pera'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- rectangles [Windows Forms], drawing
- pens [Windows Forms], drawing rectangles
ms.assetid: 54a7fa14-3ad8-4d64-b424-2a12005b250c
ms.openlocfilehash: 0e51a1e3a2d14754147dbd36f170127a7e978acd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954480"
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>Postupy: Kreslení obdélníků pomocí pera
Kreslení obdélníků, je nutné <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt, který poskytuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody a <xref:System.Drawing.Pen> ukládá funkce na řádku, jako je barva a šířka.  
  
## <a name="example"></a>Příklad  
 Kreslení obdélníku s jeho levého horního rohu v následujícím příkladu (10, 10). Obdélník má 100 šířku a výšku 50. Druhý argument předaný do <xref:System.Drawing.Pen.%23ctor%2A> konstruktor znamená, že šířka pera je 5 pixelů.  
  
 Při vykreslení obdélníku pera je zarovnaný na střed v obdélníku hranice. Vzhledem k tomu, že šířka pera je 5, strany pravoúhelníku se vykreslený 5 pixelů široký, například je vykreslen této 1 pixelu na dané hranice lze na samotný jsou vykreslovány 2 pixelů uvnitř, a jsou vykreslovány 2 pixelů na povrchu. Podrobné informace o psaní perem zarovnání naleznete v tématu [jak: Nastavení šířky a pera a zarovnání](how-to-set-pen-width-and-alignment.md).  
  
 Výsledný obdélníku na následujícím obrázku. Zobrazit tečkované čáry, kde obdélník by byl nakreslen diagram Pokud šířku pera je jeden pixel. Zvětšeným zobrazením levého horního rohu obdélníku ukazuje, že se na tyto tečkované čáry na silný černý řádky.  
  
 ![Snímek obrazovky zobrazující vykresleného obdélníku s černý a tečkované čáry.](./media/how-to-use-a-pen-to-draw-rectangles/drawn-rectangle-black-lines-dotted-lines.gif)  
  
 [!code-csharp[System.Drawing.UsingAPen#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
