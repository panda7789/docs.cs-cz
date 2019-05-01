---
title: 'Postupy: Nakreslení existujícího rastrového obrázku na obrazovku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], displaying in Windows Forms
- bitmaps [Windows Forms], loading in Windows Forms applications
- images [Windows Forms], displaying on Windows Forms
ms.assetid: 5bc558d7-b326-4050-a834-b8600da0de95
ms.openlocfilehash: 90511adf9caffe7952e270d6fe32dd85162a29d7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004173"
---
# <a name="how-to-draw-an-existing-bitmap-to-the-screen"></a>Postupy: Nakreslení existujícího rastrového obrázku na obrazovku
Snadno můžete nakreslit stávající bitovou kopii na obrazovce. Nejdřív je potřeba vytvořit <xref:System.Drawing.Bitmap> objektu pomocí konstruktoru rastrový obrázek, který vezme název souboru, <xref:System.Drawing.Bitmap.%23ctor%28System.String%29>. Tento konstruktor přijímá imagí v několika různých formátech, včetně BMP, GIF, JPEG, PNG a TIFF. Po vytvoření <xref:System.Drawing.Bitmap> objektu, který předat <xref:System.Drawing.Bitmap> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří <xref:System.Drawing.Bitmap> objekt ze souboru JPEG a pak vykreslí pomocí jeho levého horního rohu na (60, 10).  
  
 Následující obrázek znázorňuje rastrového obrázku vykreslena v zadaném umístění:  
  
 ![Snímek obrazovky zobrazující image na určené pozici.](./media/how-to-draw-an-existing-bitmap-to-the-screen/bitmap-specified-position.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.WorkingWithImages#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
