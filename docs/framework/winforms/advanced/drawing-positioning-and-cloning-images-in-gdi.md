---
title: Kreslení, umisťování a klonování obrázků v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- raster images [Windows Forms]
- images [Windows Forms], positioning
- drawing [Windows Forms], images
- drawing [Windows Forms], raster images
- images [Windows Forms], cloning
- images [Windows Forms], drawing
- GDI+, drawing images
- GDI+, cloning images
- GDI+, positioning images
ms.assetid: 09f0c07a-19c0-43b4-90a2-862a10545ce8
ms.openlocfilehash: 5ff502884874e21e8f34acb2f15db4c651a0a273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521648"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>Kreslení, umisťování a klonování obrázků v GDI+
Můžete použít <xref:System.Drawing.Bitmap> třída načtení a zobrazuje rastrových obrázků a vy můžete použít <xref:System.Drawing.Imaging.Metafile> třída načtení a zobrazuje vektoru bitové kopie. <xref:System.Drawing.Bitmap> a <xref:System.Drawing.Imaging.Metafile> třídy dědí <xref:System.Drawing.Image> třídy. Bitovou kopii vektoru zobrazíte potřebujete instanci <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Imaging.Metafile>. Pokud chcete zobrazit rastrového obrázku, je třeba instanci <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Bitmap>. Instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawImage%2A> metoda, která přijímá <xref:System.Drawing.Imaging.Metafile> nebo <xref:System.Drawing.Bitmap> jako argument.  
  
## <a name="file-types-and-cloning"></a>Typy souborů a klonování  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Climber.jpg a zobrazí bitové mapy. Cílového bodu pro levý horní roh bitové kopie, (10, 10), je zadána v parametrech druhý a třetí.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 Následující obrázek znázorňuje obrázek.  
  
 ![Obrázek ukázkové](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Můžete vytvořit <xref:System.Drawing.Bitmap> objekty z různých grafiky formáty souborů: BMP, GIF, JPEG, EXIF, PNG, TIFF a ikona.  
  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> objekty z různých typů souborů a potom zobrazí rastrových obrázků.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap> Třída poskytuje <xref:System.Drawing.Bitmap.Clone%2A> metodu, kterou můžete použít k vytvoření kopie existujícího <xref:System.Drawing.Bitmap>. <xref:System.Drawing.Bitmap.Clone%2A> Metoda má parametr obdélníku zdroj, který můžete použít k určení část původní rastrový obrázek, který chcete kopírovat. Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> klonováním horní polovině existující <xref:System.Drawing.Bitmap>. Pak jsou vykreslovány obě bitové kopie.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 Následující obrázek znázorňuje dvě bitové kopie.  
  
 ![Oříznutí](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Postupy: Vytváření grafických objektů pro kreslení](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
