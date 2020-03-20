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
ms.openlocfilehash: 1e48bbd563f6377380848949325962b568fa432c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142404"
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců
Při vyplňování tvaru je nutné <xref:System.Drawing.Brush> předat objekt jedné z <xref:System.Drawing.Graphics> metod výplně třídy. Jeden parametr konstruktoru <xref:System.Drawing.SolidBrush.%23ctor%2A> <xref:System.Drawing.Color> je objekt. Chcete-li vyplnit neprůhledný tvar, nastavte alfa složku barvy na 255. Chcete-li vyplnit poloprůhledný tvar, nastavte komponentu alfa na libovolnou hodnotu od 1 do 254.  
  
 Když vyplníte poloprůhledný tvar, barva tvaru se prolne s barvami pozadí. Komponenta alfa určuje, jak se smíchají barvy tvaru a pozadí; Hodnoty alfa v blízkosti 0 kladou větší váhu na barvy pozadí a hodnoty alfa poblíž 255 kladou větší váhu na barvu tvaru.  
  
## <a name="example"></a>Příklad  
 Následující příklad nakreslí bitmapu a pak vyplní tři elipsy, které rastrový obrázek překrývají. První elipsa používá alfa součást 255, takže je neprůhledná. Druhá a třetí elipsy používají alfa součást 128, takže jsou poloprůhledné; můžete vidět obrázek na pozadí přes elipsy. Volání, které <xref:System.Drawing.Graphics.CompositingQuality%2A> nastaví vlastnost způsobí prolnutí pro třetí elipsy, které mají být provedeny ve spojení s korekcí gama.  

 [!code-csharp[System.Drawing.AlphaBlending#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  

 Následující obrázek znázorňuje výstup následujícího kódu:
  
 ![Obrázek znázorňuje neprůhledný a poloprůhledný výstup.](./media/how-to-draw-with-opaque-and-semitransparent-brushes/compositingquality-ellipse-semitransparent.png)  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Předchozí příklad je určen pro použití s windows <xref:System.Windows.Forms.PaintEventArgs> `e`forms a vyžaduje <xref:System.Windows.Forms.PaintEventHandler>, což je parametr .  
  
## <a name="see-also"></a>Viz také

- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Alfa míchání čar a výplní](alpha-blending-lines-and-fills.md)
- [Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek](../controls/how-to-give-your-control-a-transparent-background.md)
- [Postupy: Kreslení neprůhledných a poloprůhledných čar](how-to-draw-opaque-and-semitransparent-lines.md)
