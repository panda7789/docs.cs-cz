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
ms.openlocfilehash: 8d2717dd7b819e963126072279b361fda02188bc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111332"
---
# <a name="how-to-rotate-colors"></a>Postupy: Otáčení barev
Rotace ve čtyřrozměrném barevném prostoru je obtížné vizualizovat. Můžeme usnadnit vizualizaci rotace tím, že souhlasís tím, aby jedna z barevných složek pevné. Předpokládejme, že se dohodneme na zachování alfa komponenty pevné na 1 (plně neprůhledné). Pak můžeme vizualizovat trojrozměrný barevný prostor s červenými, zelenými a modrými osami, jak je znázorněno na následujícím obrázku.  
  
 ![Obrázek znázorňovaný otočením s červenými, zelenými a modrými osami.](./media/how-to-rotate-colors/rotation-red-green-blue-axes.gif)  
  
 Barvu lze považovat za bod ve 3D prostoru. Například bod (1, 0, 0) v prostoru představuje červenou barvu a bod (0, 1, 0) v prostoru představuje zelenou barvu.  
  
 Následující obrázek znázorňuje, co znamená otočit barvu (1, 0, 0) pod úhlem 60 stupňů v červenozelené rovině. Otočení v rovině rovnoběžné s červeno-zelenou rovinou lze považovat za rotaci kolem modré osy.  
  
 ![Obrázek znázorňuje otočení kolem modré osy.](./media/how-to-rotate-colors/rotation-about-blue-axis.gif)  
  
 Následující obrázek znázorňuje, jak inicializovat matici barev, aby se provedla rotace kolem každé ze tří os souřadnic (červená, zelená, modrá):  
  
 ![Inicializovat matici barev, abyste provedli otočení asi tři osy.](./media/how-to-rotate-colors/rotation-about-three-axes.gif)  
  
## <a name="example"></a>Příklad  
 Následující příklad přebírá obraz, který je všechny jednu barvu (1, 0, 0,6) a použije otočení o 60 stupňů kolem modré osy. Úhel natočení je vymet v rovině, která je rovnoběžná s červenozelenou rovinou.  
  
 Následující obrázek znázorňuje původní obrázek vlevo a obrázek otočený o barvy vpravo:  
  
 ![Obrázek znázorňuje původní obraz a barevně otočený obraz.](./media/how-to-rotate-colors/original-color-rotated-images.png)  
  
 Následující obrázek znázorňuje vizualizaci otáčení barev provedenou v následujícím kódu:
  
 ![Obrázek znázorňuje vizualizaci otáčení barev.](./media/how-to-rotate-colors/visualization-color-rotation.gif)  
  
 [!code-csharp[System.Drawing.RotateColors#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RotateColors/CS/Form1.cs#1)]
 [!code-vb[System.Drawing.RotateColors#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RotateColors/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e`forms a vyžaduje <xref:System.Windows.Forms.Control.Paint> , což je parametr obslužné rutiny události. Nahraďte `RotationInput.bmp` název souboru obrázku a cestu platnou v systému.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Přebarvení obrázků](recoloring-images.md)
