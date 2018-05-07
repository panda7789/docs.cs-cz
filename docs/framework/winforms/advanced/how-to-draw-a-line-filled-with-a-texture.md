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
ms.openlocfilehash: 1895c752340d8d764205b5a32b9af0861303841a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-a-line-filled-with-a-texture"></a>Postupy: Kreslení čáry vyplněné texturou
Místo kreslení čáry s plnou barvou, můžete kreslení čáry texturou. Kreslení čar a křivek texturou, vytvoření <xref:System.Drawing.TextureBrush> objektu a který předat <xref:System.Drawing.TextureBrush> do objektu <xref:System.Drawing.Pen.%23ctor%2A> konstruktor. Rastrový obrázek přidružené štětce texture slouží k dlaždici rovině (tedy bez zásahu uživatele), a když pera nevykresluje řádek nebo křivky, tahu pera umožňuje odhalit určité pixelů vedle sebe texture.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří <xref:System.Drawing.Bitmap> objektu ze souboru `Texture1.jpg`. Tento rastrový obrázek se používá pro konstrukci <xref:System.Drawing.TextureBrush> objekt a <xref:System.Drawing.TextureBrush> objekt se používá pro konstrukci <xref:System.Drawing.Pen> objektu. Volání <xref:System.Drawing.Graphics.DrawImage%2A> nevykresluje bitmap s jeho levého horního rohu v (0, 0). Volání <xref:System.Drawing.Graphics.DrawEllipse%2A> používá <xref:System.Drawing.Pen> objektu k vykreslení texturou třemi tečkami.  
  
 Následující obrázek znázorňuje bitovou mapu a texturou třemi tečkami.  
  
 ![Pera](../../../../docs/framework/winforms/advanced/media/pens7.png "pens7")  
  
 [!code-csharp[System.Drawing.UsingAPen#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#61)]
 [!code-vb[System.Drawing.UsingAPen#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#61)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí. Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Nahraďte `Texture.jpg` s bitovou kopií platné ve vašem systému.  
  
## <a name="see-also"></a>Viz také  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
