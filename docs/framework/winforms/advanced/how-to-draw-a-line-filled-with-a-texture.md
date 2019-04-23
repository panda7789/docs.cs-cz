---
title: 'Postupy: Kreslení čáry vyplněné texturou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- lines [Windows Forms], texture
- drawing lines [Windows Forms], texture
ms.assetid: dc9118cc-f3c2-42e5-8173-f46d41d18fd5
ms.openlocfilehash: c0f90c298f48aeb96893bb09241faddc08d8a49d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59186899"
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Postupy: Kreslení čáry vyplněné texturou
Místo kreslení čáry s plnou barvu, můžete kreslení čáry s textury. Kreslení čar a křivek texturou, vytvořit <xref:System.Drawing.TextureBrush> objektu a předat ho <xref:System.Drawing.TextureBrush> do objektu <xref:System.Drawing.Pen.%23ctor%2A> konstruktoru. Rastrový obrázek přidružený k štětce textury se používá k dlaždici rovině (transparentně) a při pera nakreslí čáru nebo křivku, tahů perem získává některé pixely vedle sebe textury.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Bitmap> objektu ze souboru `Texture1.jpg`. Tento rastrový obrázek se používá ke konstrukci <xref:System.Drawing.TextureBrush> objektu a <xref:System.Drawing.TextureBrush> objektu se používá ke konstrukci <xref:System.Drawing.Pen> objektu. Volání <xref:System.Drawing.Graphics.DrawImage%2A> nakreslí rastrového obrázku pomocí jeho levého horního rohu v (0, 0). Volání <xref:System.Drawing.Graphics.DrawEllipse%2A> používá <xref:System.Drawing.Pen> objekt s texturou elipsa nakreslit.  
  
 Následující obrázek znázorňuje rastrového obrázku a texturou elipsa:  
  
 ![Snímek obrazovky zobrazující rastrového obrázku a texturou elipsy.](./media/how-to-draw-a-line-filled-with-a-texture/bitmap-textured-ellipse.png)  
  
 [!code-csharp[System.Drawing.UsingAPen#61](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí. Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `Texture.jpg` s bitovou kopii platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také:

- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
