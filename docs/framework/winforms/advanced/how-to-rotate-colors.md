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
ms.openlocfilehash: 241d2824fc2d87a0505eb6e790c865bfa7d8ef90
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61967325"
---
# <a name="how-to-rotate-colors"></a>Postupy: Otáčení barev
Otočení v four-dimensional barevný prostor je obtížné vizualizace. Můžeme provádět to usnadňuje vizualizaci otočení souhlasit a udržovat jeden barevným opraveno. Předpokládejme, že jsme souhlas zachovat alfa pevně nastavena na 1 (úplně neprůhledné). Potom jsme vizualizace trojrozměrného barevný prostor pomocí červené, zelené a modré osy, jak je znázorněno na následujícím obrázku.  
  
 ![Obrázek, na kterém otočení pomocí červené, zelené a modré osy.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 Barvu můžete představit jako bod v 3D prostoru. Například bod (1, 0, 0) v prostoru představuje červenou barvu a bod (0, 1, 0) v prostoru představuje zelenou barvu.  
  
 Následující obrázek znázorňuje prostřednictvím úhel 60 stupňů v rovině červenou a zelenou význam otočení barev (1, 0, 0). Otočení paralelně roviny k rovině červenou a zelenou můžete představit jako otočení o modrá osu.  
  
 ![Obrázek, na kterém otočení o modrá osu.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 Následující obrázek znázorňuje způsob inicializace matice barev k provedení rotace o každé ze tří OS souřadnic (červená, zelená, modrá):  
  
 ![Inicializujte matice barev k provedení rotace o tři osy.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>Příklad  
 Následující příklad používá image, která je všechny jednu barvu (1, 0, 0.6) a platí otočení 60 stupňů o modrá osu. Úhel otočení je, jež navýšení kapacity v rovině, který je paralelní k rovině červenou a zelenou.  
  
 Následující obrázek znázorňuje původní obrázek nalevo a obrázek otočí barvu na pravé straně:  
  
 ![Obrázek, který ukazuje původní image a image barva otočen.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 Následující obrázek znázorňuje vizualizace otáčení barev provést v následujícím kódu:
  
 ![Obrázek, který zobrazuje vizualizaci otočení barev.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `RotationInput.bmp` název a cesta platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Přebarvení obrázků](recoloring-images.md)
