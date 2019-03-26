---
title: 'Postupy: Použití tabulky přemapování barev'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
ms.openlocfilehash: 73f4f19229a31266b406214e93e2b59acd343ca2
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463888"
---
# <a name="how-to-use-a-color-remap-table"></a>Postupy: Použití tabulky přemapování barev
Přemapování je proces převodu barvy v bitovou kopii podle tabulky přemapování barev. Tabulky přemapování barev je pole <xref:System.Drawing.Imaging.ColorMap> objekty. Každý <xref:System.Drawing.Imaging.ColorMap> objekt pole má <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> vlastnost a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> vlastnost.  
  
 Když [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nakreslí obrázek, každý pixel na obrázku je ve srovnání s poli staré barvy. Pokud jeden bod barva odpovídá stará barva, jeho barva se změní na odpovídající novou barvu. Barvy se změní pouze pro vykreslování – hodnoty barev samotné (uložené v <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objektu) se nezmění.  
  
 Chcete-li nakreslit změnu mapování bitové kopie, inicializovat pole <xref:System.Drawing.Imaging.ColorMap> objekty. Předejte toto pole na <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu a pak předejte <xref:System.Drawing.Imaging.ImageAttributes> objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru RemapInput.bmp. Vytvoří kód, který se skládá z jedné tabulky přemapování barev <xref:System.Drawing.Imaging.ColorMap> objektu. <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Vlastnost `ColorRemap` červená, je objekt a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> vlastnost je modrá. Na obrázku je bez přemapování vykresleného jednou a jednou pro přemapování. Přemapování proces pouze změní všechny red pixelů na modrou.  
  
 Následující obrázek znázorňuje původní obrázek na levé straně a změnu mapování image na pravé straně.  
  
 ![Snímek obrazovky zobrazující původní bitové kopie a změnu mapování bitové kopie.](./media/how-to-use-a-color-remap-table/original-image-remap-colors.png)  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- [Přebarvení obrázků](recoloring-images.md)
- [Obrázky, rastrové obrázky a metasoubory](images-bitmaps-and-metafiles.md)
