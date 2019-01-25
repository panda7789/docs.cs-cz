---
title: Oříznutí a změna měřítka obrázků v GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- GDI+, scaling images
- GDI+, cropping images
- images [Windows Forms], cropping
- compressing data [Windows Forms], images
- images [Windows Forms], expansion
- images [Windows Forms], scaling
- rectangles [Windows Forms], source
- rectangles [Windows Forms], destination
- images [Windows Forms], compression
ms.assetid: ad5daf26-005f-45bc-a2af-e0e97777a21a
ms.openlocfilehash: 6c3ad0892ea0892b7c4c0e21e14bdb75fe22b447
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554215"
---
# <a name="cropping-and-scaling-images-in-gdi"></a>Oříznutí a změna měřítka obrázků v GDI+
Můžete použít <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> třídu pro vykreslení a umístění vektorové obrázky a rastrové obrázky. <xref:System.Drawing.Graphics.DrawImage%2A> je přetěžované metody, takže je můžete zadat s argumenty několika způsoby.  
  
## <a name="drawimage-variations"></a>DrawImage odchylky  
 Jeden varianta <xref:System.Drawing.Graphics.DrawImage%2A> metoda přijímá <xref:System.Drawing.Bitmap> a <xref:System.Drawing.Rectangle>. Obdélník Určuje cíl pro kreslení operaci. To znamená určuje obdélník, ve kterém chcete-li nakreslit obrázek. Pokud se velikost cílového obdélníku liší od velikosti původní bitové kopie, image se škálovat podle cílového obdélníku. Následující příklad kódu ukazuje, jak nakreslit stejnou bitovou kopii třikrát: jednou pro žádné škálování, jednou pro rozšíření a jednou pro kompresi:  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 Následující obrázek znázorňuje tři obrázky.  
  
 ![Scaling](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 Některé varianty <xref:System.Drawing.Graphics.DrawImage%2A> metoda mít parametr zdrojového obdélníku, stejně jako parametr cílového obdélníku. Parametr zdrojového obdélníku určuje část původní bitové kopie k vykreslení. Cílového obdélníku určuje obdélník, ve kterém chcete-li nakreslit část obrázku. Pokud se velikost cílového obdélníku liší od velikosti zdrojového obdélníku, obrázek se škálovat podle cílového obdélníku.  
  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Runner.jpg. Je nakreslit bez škálování na celého obrázku (0, 0). Vykreslován tak malou část obrázku dvakrát: jednou pro kompresi a posléze s rozšíření.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 Následující obrázek znázorňuje bez měřítka image a image komprimované a rozšířené části.  
  
 ![Oříznutí a změna měřítka](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>Viz také:
- [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
