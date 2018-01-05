---
title: "Postupy: Použití režimu interpolace pro řízení kvality obrázku během změny měřítka"
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
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e8bbc17b8344fca496dcf8f4077a69b6db1453c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>Postupy: Použití režimu interpolace pro řízení kvality obrázku během změny měřítka
Režim interpolace <xref:System.Drawing.Graphics> objekt ovlivňuje způsob [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] Image měřítka (úsecích a zmenší). <xref:System.Drawing.Drawing2D.InterpolationMode> Výčet definuje několik režimy interpolace, z nichž některé jsou uvedeny v následujícím seznamu:  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
-   <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 K roztažení obrázku, každý pixelů v původní bitové kopie musí být namapovaný na skupinu pixelů na větší obrázku. Zmenšení bitovou kopii, skupiny pixelů v původní bitové kopie musí být mapován na jednom pixelů na menší obrázku. Efektivita algoritmů, které provádějí tato mapování určuje kvalitu škálovat bitové kopie. Algoritmy, které produkují Kvalitnější škálovat obrazy většinou vyžaduje více času na zpracování. V předchozím seznamu <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> je režim nejnižší kvality a <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> je režim nejvyšší kvality.  
  
 Nastavení režimu interpolace, přiřadit jeden ze členů <xref:System.Drawing.Drawing2D.InterpolationMode> výčet <xref:System.Drawing.Graphics.InterpolationMode%2A> vlastnost <xref:System.Drawing.Graphics> objektu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu nakreslí obrázek a pak zmenšuje bitové kopie s tři interpolace různé režimy.  
  
 Následující obrázek znázorňuje původní bitové kopie a tři menší bitové kopie.  
  
 ![Bitové kopie s různým interpolace nastavení](../../../../docs/framework/winforms/advanced/media/csgrapes1.png "csgrapes1")  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)
