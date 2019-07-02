---
title: 'Postupy: Použití režimu interpolace pro řízení kvality obrázku během změny měřítka'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interpolation mode [Windows Forms], controlling image quality
- images [Windows Forms], scaling
- images [Windows Forms], controlling quality
ms.assetid: fde9bccf-8aa5-4b0d-ba4b-788740627b02
ms.openlocfilehash: ab0ff93b3ee26467c0de448efd31b698167f95c2
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505710"
---
# <a name="how-to-use-interpolation-mode-to-control-image-quality-during-scaling"></a>Postupy: Použití režimu interpolace pro řízení kvality obrázku během změny měřítka
Režim interpolace <xref:System.Drawing.Graphics> objektu má vliv způsob, jak rozhraní GDI + škálování (úseky a zmenší) bitové kopie. <xref:System.Drawing.Drawing2D.InterpolationMode> Výčet definuje několik režimů interpolace, z nichž některé jsou uvedeny v následujícím seznamu:  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.Bilinear>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBilinear>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.Bicubic>  
  
- <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic>  
  
 Roztáhnout obrázek, každý pixel v původní bitové kopie musí být namapován na skupinu větší obrázku v pixelech. Zmenšení bitovou kopii, skupiny pixelů v původní bitové kopie musí být namapován na jeden pixelů v menším obrázkem. Účinnost algoritmy, které provádějí tato mapování určuje kvalitu obrazu se změněnou velikostí. Algoritmy, které vytvářejí škálován imagí kvalitnější většinou vyžaduje více času na zpracování. V předchozím seznamu <xref:System.Drawing.Drawing2D.InterpolationMode.NearestNeighbor> je režim nejnižší kvality a <xref:System.Drawing.Drawing2D.InterpolationMode.HighQualityBicubic> je režim nejvyšší kvality.  
  
 Nastavení režimu interpolace, přiřadit jeden z členů <xref:System.Drawing.Drawing2D.InterpolationMode> výčet <xref:System.Drawing.Graphics.InterpolationMode%2A> vlastnost <xref:System.Drawing.Graphics> objektu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu nakreslí obrázek a potom zmenšuje bitová kopie se tři interpolace různé režimy.  
  
 Následující obrázek znázorňuje původní bitové kopie a tři menší Image.  
  
 ![Snímek obrazovky zobrazující image s rozdílnými interpolace nastavení.](./media/how-to-use-interpolation-mode-to-control-image-quality-during-scaling/varied-interpolation-settings.png)  
  
 [!code-csharp[System.Drawing.WorkingWithImages#81](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/CS/Class1.cs#81)]
 [!code-vb[System.Drawing.WorkingWithImages#81](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.WorkingWithImages/VB/Class1.vb#81)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
- [Práce s obrázky, rastrovými obrázky, ikonami a metasoubory](working-with-images-bitmaps-icons-and-metafiles.md)
