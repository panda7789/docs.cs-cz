---
title: 'Postupy: Zavedení a zobrazení metasouborů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: 6c17e0b2d023ccf80b0d32301b7ee6765edcae9f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424827"
---
# <a name="how-to-load-and-display-metafiles"></a>Postupy: Zavedení a zobrazení metasouborů
Třída <xref:System.Drawing.Imaging.Metafile>, která dědí z třídy <xref:System.Drawing.Image>, poskytuje metody pro zaznamenávání, zobrazování a zkoumání vektorových imagí.  
  
## <a name="example"></a>Příklad  
 Chcete-li na obrazovce zobrazit vektorový obraz (metasoubor), budete potřebovat objekt <xref:System.Drawing.Imaging.Metafile> a objekt <xref:System.Drawing.Graphics>. Předat název souboru (nebo datového proudu) konstruktoru <xref:System.Drawing.Imaging.Metafile>. Po vytvoření objektu <xref:System.Drawing.Imaging.Metafile> předejte objekt <xref:System.Drawing.Imaging.Metafile> do metody <xref:System.Drawing.Graphics.DrawImage%2A> objektu <xref:System.Drawing.Graphics>.  
  
 V příkladu se vytvoří objekt <xref:System.Drawing.Imaging.Metafile> ze souboru EMF (Enhanced Metafile) a pak se obrázek vykreslí pomocí levého horního rohu v (60, 10).  
  
 Následující ilustrace znázorňuje metasoubor nakreslený v zadaném umístění.  
  
 ![Snímek obrazovky znázorňující umístění obrázku](./media/how-to-load-and-display-metafiles/metafile-drawn-specified-location.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr obslužné rutiny události <xref:System.Windows.Forms.Control.Paint>.  
  
## <a name="see-also"></a>Viz také:

- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
