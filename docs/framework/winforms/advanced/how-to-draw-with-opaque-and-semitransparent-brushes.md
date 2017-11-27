---
title: "Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- semi-transparent shapes [Windows Forms], drawing
- transparency [Windows Forms], semi-transparent shapes
- alpha blending [Windows Forms], brush
- brushes [Windows Forms], using semi-transparent
ms.assetid: a4f6f6b8-3bc8-440a-84af-d62ef0f8ff40
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4af2664851ed0903a362a4b88edf1db9bb042dfa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-draw-with-opaque-and-semitransparent-brushes"></a>Postupy: Kreslení pomocí neprůhledných a poloprůhledných štětců
Po vyplnění obrazce, je nutné předat <xref:System.Drawing.Brush> objektu na jednu z metod výplně <xref:System.Drawing.Graphics> třídy. Jeden parametr <xref:System.Drawing.SolidBrush.%23ctor%2A> konstruktor je <xref:System.Drawing.Color> objektu. K vyplnění neprůhledného tvaru, nastavte komponentu alfa barvy na 255. K vyplnění obrazce poloprůhledných, nastavte na jakoukoli hodnotu od 1 do 254 komponentu alfa.  
  
 Jakmile zadáte poloprůhledných obrazce, barva obrazce je smíšený s barvy pozadí. Komponentu alfa Určuje, jak jsou kombinované barvy tvar a pozadí; hodnoty alfa téměř 0 umístěte další váhy barvy pozadí a hodnoty alfa téměř 255 umístit další váhy na barvou obrazce.  
  
## <a name="example"></a>Příklad  
 Následující příklad nevykresluje rastrový obrázek a pak vyplní tři výpustky, které se překrývají bitové mapy. První elipsy používá alfa součást 255, takže je plné krytí. Druhý a třetí výpustky použít alfa součást 128, tak, aby byly poloprůhledných; Zobrazí se obrázek pozadí prostřednictvím na symbol tří teček. Volání, které se nastaví <xref:System.Drawing.Graphics.CompositingQuality%2A> vlastnost způsobí, že prolnutí pro třetí elipsy provést ve spojení s korekce gama.  
  
 Následující obrázek znázorňuje výstup následující kód.  
  
 ![Neprůhledných a poloprůhledných](../../../../docs/framework/winforms/advanced/media/compqualellipse.png "compqualellipse")  
  
 [!code-csharp[System.Drawing.AlphaBlending#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.AlphaBlending/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.AlphaBlending#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.AlphaBlending/VB/Class1.vb#31)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 V předchozím příkladu je určen k použití s modelem Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.  
  
## <a name="see-also"></a>Viz také  
 [Grafika a kreslení v systému Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Alfa míchání čar a výplní](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 [Postupy: poskytnout vlastní ovládací prvek průhledné pozadí](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 [Postupy: kreslení neprůhledných a poloprůhledných čar](../../../../docs/framework/winforms/advanced/how-to-draw-opaque-and-semitransparent-lines.md)
