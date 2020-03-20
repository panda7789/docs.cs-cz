---
title: 'Postupy: Zkosení barev'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [Windows Forms], transforming with color matrices
- colors [Windows Forms], shearing
ms.assetid: 0a424171-5b8b-45c4-afef-e9720a6c3e22
ms.openlocfilehash: 825e5a90ebb0d9df3b894ce7bd353e917b676939
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142391"
---
# <a name="how-to-shear-colors"></a>Postupy: Zkosení barev
Zkosení zvětšuje nebo zmenšuje barevnou složku o částku úměrnou jiné barevné složce. Zvažte například transformaci, kde je červená komponenta zvýšena o polovinu hodnoty modré součásti. Při takové transformaci by se barva (0,2, 0,5, 1) stala (0,7, 0,5, 1). Nová červená složka je 0,2 + (1/2)(1) = 0,7.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars4.bmp. Pak kód použije zkosení transformace popsané v předchozím odstavci na každý obrazový bod v obraze.  
  
 Následující obrázek znázorňuje původní obrázek vlevo a střižený obrázek vpravo:
  
 ![Dva čtverce s barevnými pruhy vedle sebe ilustrující původní obraz a stočený obraz.](./media/how-to-shear-colors/original-image-sheared-image.png)  
  
 V následující tabulce jsou uvedeny vektory barev pro čtyři pruhy před a po transformaci zkosení.  
  
|Původní|Sazený|  
|--------------|-------------|  
|(0, 0, 1, 1)|(0.5, 0, 1, 1)|  
|(0.5, 1, 0.5, 1)|(0.75, 1, 0.5, 1)|  
|(1, 1, 0, 1)|(1, 1, 0, 1)|  
|(0.4, 0.4, 0.4, 1)|(0.6, 0.4, 0.4, 1)|  
  
 [!code-csharp[System.Drawing.Misc3#9](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.Misc3/CS/Form1.cs#9)]
 [!code-vb[System.Drawing.Misc3#9](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.Misc3/VB/Form1.vb#9)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e`forms a vyžaduje <xref:System.Windows.Forms.Control.Paint> , což je parametr obslužné rutiny události. Nahraďte `ColorBars.bmp` název obrázku a cestu platnou v systému.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Přebarvení obrázků](recoloring-images.md)
