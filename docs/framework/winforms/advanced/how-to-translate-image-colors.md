---
title: 'Postupy: Překlad barev obrázků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [Windows Forms], changing colors
- images [Windows Forms], changing colors
- image colors [Windows Forms]
ms.assetid: 2106fb9a-4d60-4dcf-9220-9f189a6c4d19
ms.openlocfilehash: fb9ec30c06740214b8dc6b65d32eba4e2920c89b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592928"
---
# <a name="how-to-translate-image-colors"></a>Postupy: Překlad barev obrázků
Překlad přidá hodnotu na jeden nebo více součástí čtyři barvy. Matice položek barev, které představují překlady jsou uvedeny v následující tabulce.  
  
|Součást, kterou přeložit|Přehled vstupu|  
|--------------------------------|------------------|  
|Červená|[4][0]|  
|Zelená|[4][1]|  
|Modrá|[4][2]|  
|Alpha|[4][3]|  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Image> objekt ze souboru ColorBars.bmp. Potom kód přidá 0,75 červené každý pixel na obrázku. Původní bitové kopie nakreslen spolu s transformovaný bitové kopie.  
  
 Následující obrázek znázorňuje původní obrázek na levé straně a transformovaná image na pravé straně:  
  
 ![Snímek obrazovky s původní a transformovaná image.](./media/how-to-translate-image-colors/original-image-translate-colors.png)  
  
 Následující tabulka uvádí vektory barvu pro čtyři pruhy před a po červenou překladu. Mějte na paměti, protože maximální hodnota složky barvy je 1, červené ve druhém řádku nezmění. (Podobně, minimální hodnota složky barvy je 0.)  
  
|Původní|Přeložit|  
|--------------|----------------|  
|Černé (0, 0, 0, 1)|(0.75, 0, 0, 1)|  
|Červená (1, 0, 0, 1)|(1, 0, 0, 1)|  
|Zelená (0, 1, 0, 1)|(0.75, 1, 0, 1)|  
|Modré (0, 0, 1, 1)|(0.75, 0, 1, 1)|  
  
 [!code-csharp[System.Drawing.RecoloringImages#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.RecoloringImages/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.RecoloringImages#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.RecoloringImages/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `ColorBars.bmp` název souboru bitové kopie a cestu, která jsou platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.Imaging.ColorMatrix>
- <xref:System.Drawing.Imaging.ImageAttributes>
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Přebarvení obrázků](recoloring-images.md)
