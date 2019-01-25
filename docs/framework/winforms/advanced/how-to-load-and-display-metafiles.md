---
title: 'Postupy: Načtení a zobrazení metasouborů'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], metafiles
- metafiles [Windows Forms], displaying
ms.assetid: 60af1714-f148-4d85-a739-0557965ffa73
ms.openlocfilehash: d0835d7f2c5ffea44f22661a765ab16b1d0130c5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54619555"
---
# <a name="how-to-load-and-display-metafiles"></a>Postupy: Načtení a zobrazení metasouborů
<xref:System.Drawing.Imaging.Metafile> Třída, která dědí z <xref:System.Drawing.Image> třídy, poskytuje metody pro nahrávání, zobrazování a zkoumání vektorové obrázky.  
  
## <a name="example"></a>Příklad  
 K zobrazení bitovou kopii vektoru (metafile) na obrazovce, je nutné <xref:System.Drawing.Imaging.Metafile> objektu a <xref:System.Drawing.Graphics> objektu. Předat název souboru (nebo datový proud) <xref:System.Drawing.Imaging.Metafile> konstruktoru. Po vytvoření <xref:System.Drawing.Imaging.Metafile> objektu, který předat <xref:System.Drawing.Imaging.Metafile> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
 V příkladu se vytvoří <xref:System.Drawing.Imaging.Metafile> objekt ze souboru EMF (rozšířený metasoubor) a potom nakreslí obrázek s jeho levého horního rohu na (60, 10).  
  
 Následující obrázek znázorňuje tento metasoubor vykreslen v zadaném umístění.  
  
 ![Obrázek pozice](../../../../docs/framework/winforms/advanced/media/imageposition2.png "imageposition2")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.WorkingWithImages#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
