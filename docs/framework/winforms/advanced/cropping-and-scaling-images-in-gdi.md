---
title: "Oříznutí a změna měřítka obrázků v GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0bbe7ac4b8c541ea76392f94f538e41816cf5c3f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="cropping-and-scaling-images-in-gdi"></a>Oříznutí a změna měřítka obrázků v GDI+
Můžete použít <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> třída pro kreslení a umístění bitové kopie vektoru a rastrových obrázků. <xref:System.Drawing.Graphics.DrawImage%2A>je přetížené metody, takže je můžete zadat s argumenty několika způsoby.  
  
## <a name="drawimage-variations"></a>DrawImage – variant  
 Jeden varianta <xref:System.Drawing.Graphics.DrawImage%2A> metoda obdrží <xref:System.Drawing.Bitmap> a <xref:System.Drawing.Rectangle>. Rámeček určuje cíl pro kreslení operaci; To znamená určuje obdélníku, ve kterém k vykreslení bitovou kopii. Pokud velikost cílové rámeček se liší od velikost původní bitové kopie, bitovou kopii přizpůsobí se rámeček cílový. Následující příklad kódu ukazuje, jak k vykreslení stejnou bitovou kopii třikrát: jednou pro žádné škálování, jednou pro rozšíření a jednou pro komprese:  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#31)]  
  
 Následující obrázek znázorňuje tři obrázky.  
  
 ![Škálování](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art06.gif "AboutGdip03_Art06")  
  
 Některé variace <xref:System.Drawing.Graphics.DrawImage%2A> metoda mít parametr zdroj obdélníku, jakož i cílové obdélníku parametr. Parametr zdroj obdélníku určuje část původní bitové kopie k vykreslení. Rámeček cílové určuje obdélníku, ve kterém k vykreslení část bitovou kopii. Pokud velikost cílové rámeček se liší od velikost zdroje obdélníku, na obrázku přizpůsobí se rámeček cílový.  
  
 Následující příklad kódu ukazuje, jak vytvořit <xref:System.Drawing.Bitmap> ze souboru Runner.jpg. Celého obrázku vykreslením s žádné škálování na (0, 0). Pak malá část obrázku se nevykreslí dvakrát: jednou s komprese a jednou rozšíření.  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#32)]  
  
 Následující obrázek znázorňuje bez měřítka bitové kopie a části komprimované a rozšířená bitové kopie.  
  
 ![Oříznutí a změna měřítka](../../../../docs/framework/winforms/advanced/media/aboutgdip03-art07.gif "AboutGdip03_Art07")  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
