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
ms.openlocfilehash: ad5b436f7162c282198c7a9d3cce4d3ce3fd3c6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-pen-to-draw-rectangles"></a>Postupy: Kreslení obdélníků pomocí pera
Kreslení obdélníků, musíte <xref:System.Drawing.Graphics> objektu a <xref:System.Drawing.Pen> objektu. <xref:System.Drawing.Graphics> Objekt poskytuje <xref:System.Drawing.Graphics.DrawRectangle%2A> metody a <xref:System.Drawing.Pen> objekt ukládá funkce na řádku, jako je například barva a šířka.  
  
## <a name="example"></a>Příklad  
 Následující příklad nevykresluje obdélníku s jeho levého horního rohu v (10, 10). Rámeček má šířky 100 a výška 50. Druhý argument předaný <xref:System.Drawing.Pen.%23ctor%2A> konstruktor značí, že šířku pera 5 pixelů.  
  
 Při sestavování rámeček pera se jedná o obdélníku hranic. Vzhledem k šířce pera je 5, jsou stran obdélníku vykresleného 5 pixelů široké, například tento 1 pixel vykreslením na samotná hranice jsou vykreslovány 2 pixelů uvnitř a 2 pixelů jsou vykreslovány na povrchu. Další informace o pera zarovnání v [postupy: nastavení šířky a pera a zarovnání](../../../../docs/framework/winforms/advanced/how-to-set-pen-width-and-alignment.md).  
  
 Následující obrázek znázorňuje výsledné rámeček. Zobrazit čáry s koncovými body, kde rámeček by byly pokud šířku pera je jeden pixel. Práce se zvětšeným zobrazením levého horního rohu obdélníku ukazuje, že se na tyto řádky tečkovaná na silné černé čáry.  
  
 ![Pera](../../../../docs/framework/winforms/advanced/media/pens1.gif "pens1")  
  
 [!code-csharp[System.Drawing.UsingAPen#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingAPen#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
