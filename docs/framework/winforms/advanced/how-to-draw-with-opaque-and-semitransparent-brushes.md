---
title: 'Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
ms.openlocfilehash: 922cf6f9fd506e6095d87c3e0ee9eff85f920eba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54586960"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců
Po vyplnění obrazce, je nutné předat <xref:System.Drawing.Brush> objektu do jedné z metod výplň <xref:System.Drawing.Graphics> třídy. Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> je konstruktor <xref:System.Drawing.Color> objektu. K vyplnění obrazce neprůhledný, nastavte alfa barvy na 255. K vyplnění poloprůhledných tvar, nastavte na libovolnou hodnotu od 1 do 254 alfa složkou.  
  
 Po vyplnění poloprůhledných tvar, barvu tvaru jsou prolnuty barvy pozadí. Hodnota alfa Určuje, jak barvy tvar a pozadí směšování; hodnoty alfa téměř 0 umístěte větší váhu na barvy pozadí a alfa hodnot v 255 ustaví větší váhu barvou obrazce.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu nakreslí rastrový obrázek a potom naplní tři symbol tří teček, které se překrývají rastrového obrázku. První tři tečky používá alfa složkou 255, proto je skrytá. Druhý a třetí symbol tří teček použít alfa složkou 128, tak, aby byly poloprůhledných; Zobrazí se obrázek pozadí prostřednictvím symbol tří teček. Volání, které nastaví <xref:System.Drawing.Graphics.CompositingQuality%2A> vlastnosti způsobí, že míchání třetí elipsy ve spojení s gama korekce udělat.  
  
 Následující obrázek znázorňuje výstup následující kód.  
  
 ![Neprůhledných a poloprůhledných](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také:
- [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [Alfa míchání čar a výplní](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
- [Postupy: Zadejte svůj ovládací prvek průhledné pozadí](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
- [Postupy: Kreslení neprůhledných a poloprůhledných čar](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
