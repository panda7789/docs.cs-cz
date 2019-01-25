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
ms.openlocfilehash: 6076ebf6cb75aa4fdb5cf5798b642597d8f84c80
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559044"
---
# <a name="how-to-draw-opaque-and-semitransparent-lines"></a>Postupy: Kreslení neprůhledných a poloprůhledných čar
Když nakreslíte čáru, je nutné předat <xref:System.Drawing.Pen> objektu <xref:System.Drawing.Graphics.DrawLine%2A> metodu <xref:System.Drawing.Graphics> třídy. Jeden z parametrů <xref:System.Drawing.Pen.%23ctor%2A> je konstruktor <xref:System.Drawing.Color> objektu. Kreslení neprůhledných čáry, nastavte hodnota alfa barvy do 255. Nakreslení poloprůhledných čáry, nastavte na libovolnou hodnotu od 1 do 254 alfa složkou.  
  
 Když nakreslíte čáru poloprůhledných na pozadí, Barva čáry jsou prolnuty barvy pozadí. Hodnota alfa Určuje, jak barvy čáry a pozadí směšování; hodnoty alfa téměř 0 umístěte větší váhu na barvy pozadí a alfa hodnot v 255 umístit větší váhu na barvu čáry.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu nakreslí rastrový obrázek a pak vykreslí tři řádky, které používají rastrového obrázku na pozadí. První řádek používá alfa složkou 255, proto je skrytá. Druhý a třetí řádky použít alfa složkou 128, tak, aby byly poloprůhledných; Zobrazí se obrázek pozadí přes řádky. Příkaz, který nastaví <xref:System.Drawing.Graphics.CompositingQuality%2A> vlastnosti způsobí, že míchání pro udělat ve spojení s gama korekce na třetím řádku.  
  
 Následující obrázek znázorňuje výstup následující kód.  
  
 ![Neprůhledných a poloprůhledných](../../../../docs/framework/winforms/advanced/media/compqualline.png "compqualline")  
  
 [!code-csharp[System.Drawing.AlphaBlending#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#11)]
 [!code-vb[System.Drawing.AlphaBlending#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#11)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- [Alfa míchání čar a výplní](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)
- [Postupy: Zadejte svůj ovládací prvek průhledné pozadí](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
- [Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců](../../../../docs/framework/winforms/advanced/how-to-draw-with-opaque-and-semitransparent-brushes.md)
