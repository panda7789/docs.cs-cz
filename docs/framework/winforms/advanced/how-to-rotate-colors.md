---
title: 'Postupy: Otáčení barev'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], rotating
- examples [Windows Forms], rotating colors
ms.assetid: e2e4c300-159c-4f4a-9b56-103b0f7cbc05
ms.openlocfilehash: 6c4f41504911e94673707d99d804fad5b228599e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54503059"
---
# <a name="how-to-rotate-colors"></a>Postupy: Otáčení barev
Otočení v four-dimensional barevný prostor je obtížné vizualizace. Můžeme provádět to usnadňuje vizualizaci otočení souhlasit a udržovat jeden barevným opraveno. Předpokládejme, že jsme souhlas zachovat alfa pevně nastavena na 1 (úplně neprůhledné). Potom jsme vizualizace trojrozměrného barevný prostor pomocí červené, zelené a modré osy, jak je znázorněno na následujícím obrázku.  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring03.gif "recoloring03")  
  
 Barvu můžete představit jako bod v 3D prostoru. Například bod (1, 0, 0) v prostoru představuje červenou barvu a bod (0, 1, 0) v prostoru představuje zelenou barvu.  
  
 Následující obrázek znázorňuje prostřednictvím úhel 60 stupňů v rovině červenou a zelenou význam otočení barev (1, 0, 0). Otočení paralelně roviny k rovině červenou a zelenou můžete představit jako otočení o modrá osu.  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring04.gif "recoloring04")  
  
 Následující obrázek znázorňuje způsob inicializace matice barev k provedení rotace o každé ze tří OS souřadnic (červená, zelená, modrá).  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring05.gif "recoloring05")  
  
## <a name="example"></a>Příklad  
 Následující příklad používá image, která je všechny jednu barvu (1, 0, 0.6) a platí otočení 60 stupňů o modrá osu. Úhel otočení je, jež navýšení kapacity v rovině, který je paralelní k rovině červenou a zelenou.  
  
 Následující obrázek znázorňuje původní obrázek nalevo a obrázek otočí barvu na pravé straně.  
  
 ![Rotate Colors](../../../../docs/framework/winforms/advanced/media/colortrans5.png "colortrans5")  
  
 Následující obrázek znázorňuje vizualizace otáčení barev provést v následujícím kódu.  
  
 ![Přebarvení](../../../../docs/framework/winforms/advanced/media/recoloring06.gif "recoloring06")  
  
 [!code-csharp[System.Drawing.RotateColors#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `RotationInput.bmp` název a cesta platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Přebarvení obrázků](../../../../docs/framework/winforms/advanced/recoloring-images.md)
