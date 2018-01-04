---
title: "Postupy: Použití tabulky přemapování barev"
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
- color tables [Windows Forms], remapping colors with
- custom colors [Windows Forms], creating with color remap table
- color remap tables [Windows Forms], using
ms.assetid: 977df1ce-8665-42d4-9fb1-ef7f0ff63419
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e208aa9c98c1ca19baee83760cfd0f75972ecfa
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-color-remap-table"></a>Postupy: Použití tabulky přemapování barev
Přemapování je proces převodu barev v obraze podle tabulky přemapování barev. Tabulky přemapování barev je pole <xref:System.Drawing.Imaging.ColorMap> objekty. Každý <xref:System.Drawing.Imaging.ColorMap> objekt v poli má <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> vlastnost a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> vlastnost.  
  
 Když [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nakreslí na bitovou kopii, každý pixelů bitové kopie se porovnává se pole staré barvy. Pokud jeden bod barva odpovídá původní barvu, jeho barva se změní na barvu odpovídající nové. Barvy došlo ke změně pouze pro vykreslování – hodnoty barev samotné bitové kopie (uložené v <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objektu), nebudou změněny.  
  
 Kreslení změnu mapování bitové kopie, inicializovat pole <xref:System.Drawing.Imaging.ColorMap> objekty. Předat do tohoto pole <xref:System.Drawing.Imaging.ImageAttributes.SetRemapTable%2A> metodu <xref:System.Drawing.Imaging.ImageAttributes> objektu a pak <xref:System.Drawing.Imaging.ImageAttributes> do objektu <xref:System.Drawing.Graphics.DrawImage%2A> metodu <xref:System.Drawing.Graphics> objektu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objektu ze souboru RemapInput.bmp. Kód vytvoří tabulky přemapování barev, která se skládá z jedné <xref:System.Drawing.Imaging.ColorMap> objektu. <xref:System.Drawing.Imaging.ColorMap.OldColor%2A> Vlastnost `ColorRemap` objekt je červená a <xref:System.Drawing.Imaging.ColorMap.NewColor%2A> vlastnost je modrá. Bitová kopie je vykresleného jednou bez přemapování a jednou pro přemapování. Procesu přemapování změní všechny red pixelů na modrou.  
  
 Následující obrázek znázorňuje původní bitové kopie na levé straně a bitovou kopii změnu mapování na pravé straně.  
  
 ![Barva přemapování](../../../../docs/framework/winforms/advanced/media/colortrans7.png "colortrans7")  
  
 [!code-csharp[System.Drawing.RecoloringImages#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.RecoloringImages#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Přebarvení obrázků](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 [Obrázky, rastrové obrázky a metasoubory](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
