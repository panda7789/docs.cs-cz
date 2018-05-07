---
title: 'Postupy: Kreslení neprůhledných a poloprůhledných čar'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- drawing [Windows Forms], lines
- transparency [Windows Forms], lines
- lines [Windows Forms], drawing alpha blended
- alpha blending [Windows Forms], drawing lines
ms.assetid: 8f2508af-f495-4223-b5cc-646cbbb520eb
ms.openlocfilehash: f6667b3ac5bbe5dd82198f7bf23047f01cd7350a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>Postupy: Kreslení neprůhledných a poloprůhledných čar
Při nakreslení čáry, je nutné předat <xref:System.Drawing.Pen> do objektu <xref:System.Drawing.Graphics.DrawLine%2A> metodu <xref:System.Drawing.Graphics> třídy. Jeden z parametrů <xref:System.Drawing.Pen.%23ctor%2A> konstruktor je <xref:System.Drawing.Color> objektu. Kreslení neprůhledných řádku, nastavte komponentu alfa barvy na 255. Kreslení poloprůhledných čáry, nastavte na jakoukoli hodnotu od 1 do 254 komponentu alfa.  
  
 Při kreslení poloprůhledných řádku na pozadí, barvu čáry je smíšený s barvy pozadí. Komponentu alfa Určuje, jak jsou kombinované barvy řádku a pozadí; hodnoty alfa téměř 0 umístěte další váhy barvy pozadí a hodnoty alfa téměř 255 umístit další váhy na barvu čáry.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu nevykresluje rastrový obrázek a poté nakreslí tři řádky, které používají bitovou mapu jako pozadí. První řádek používá alfa součást 255, takže je plné krytí. Druhý a třetí řádky použít alfa součást 128, tak, aby byly poloprůhledných; Zobrazí se obrázek pozadí prostřednictvím řádky. Příkaz, který nastaví <xref:System.Drawing.Graphics.CompositingQuality%2A> vlastnost způsobí, že prolnutí pro ve třetím řádku provést ve spojení s korekce gama.  
  
 Následující obrázek znázorňuje výstup následující kód.  
  
 ![Neprůhledných a poloprůhledných](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Alfa míchání čar a výplní](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Postupy: Zajištění průhledného pozadí pro vlastní ovládací prvek](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
