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
ms.openlocfilehash: 9682c7be5956680556defd698cb97e8f4b1a7f50
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724654"
---
# <a name="drawing-positioning-and-cloning-images-in-gdi"></a>Kreslení, umisťování a klonování obrázků v GDI+
Můžete použít <xref:System.Drawing.Bitmap> třída načíst a zobrazit rastrové obrázky kde můžete použít <xref:System.Drawing.Imaging.Metafile> třídy načíst a zobrazit vektorové obrázky. <xref:System.Drawing.Bitmap> a <xref:System.Drawing.Imaging.Metafile> třídy dědí <xref:System.Drawing.Image> třídy. K zobrazení bitovou kopii vektoru, je třeba instance <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Imaging.Metafile>. K zobrazení rastrového obrázku, je třeba instance <xref:System.Drawing.Graphics> třídy a <xref:System.Drawing.Bitmap>. Instance <xref:System.Drawing.Graphics> třída poskytuje <xref:System.Drawing.Graphics.DrawImage%2A> metodu, která přijímá <xref:System.Drawing.Imaging.Metafile> nebo <xref:System.Drawing.Bitmap> jako argument.  
  
## <a name="file-types-and-cloning"></a>Typy souborů a klonování  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Climber.jpg a zobrazí rastrový obrázek. Cílový bod pro levý horní roh obrázku, (10, 10), je zadané v druhý a třetí parametr.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#11)]  
  
 Následující obrázek znázorňuje obrázek.  
  
 ![Image Sample](./media/aboutgdip03-art04.gif "AboutGdip03_Art04")  
  
 Můžete vytvořit <xref:System.Drawing.Bitmap> objekty z různých grafiky formáty souborů: BMP, GIF, JPEG, EXIF, PNG, TIFF a ikonu.  
  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> objekty z různých typů souborů a poté zobrazí rastrové obrázky.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#12)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#12)]  
  
 <xref:System.Drawing.Bitmap> Poskytuje třídy <xref:System.Drawing.Bitmap.Clone%2A> metodu, která vám umožní vytvořit kopii existující <xref:System.Drawing.Bitmap>. <xref:System.Drawing.Bitmap.Clone%2A> Metoda má parametr zdrojového obdélníku, který můžete použít k určení část původní rastrový obrázek, který chcete zkopírovat. Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> klonováním existujícího v horní polovině <xref:System.Drawing.Bitmap>. Poté jsou vykreslovány vedle obě bitové kopie.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#13)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#13](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#13)]  
  
 Následující obrázek znázorňuje dvě bitové kopie.  
  
 ![Cropping](./media/aboutgdip03-art05.gif "AboutGdip03_Art05")  
  
## <a name="see-also"></a>Viz také:
- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Postupy: Vytváření grafických objektů pro kreslení](how-to-create-graphics-objects-for-drawing.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
