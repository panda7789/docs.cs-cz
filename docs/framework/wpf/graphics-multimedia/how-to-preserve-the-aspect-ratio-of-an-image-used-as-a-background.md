---
title: 'Postupy: Zachování poměru stran u obrázku na pozadí'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: b467fcd353994faef19b5a997e03d6582789eac1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186035"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Postupy: Zachování poměru stran u obrázku na pozadí
Tento příklad ukazuje, <xref:System.Windows.Media.TileBrush.Stretch%2A> jak používat <xref:System.Windows.Media.ImageBrush> vlastnost k zachování poměru stran obrazu.  
  
 Ve výchozím nastavení se <xref:System.Windows.Media.ImageBrush> její obsah při malování oblasti použije k malování oblasti a zcela vyplní výstupní oblast. Pokud má výstupní oblast a obraz různé poměry stran, obraz je tímto roztažením zkreslen.  
  
 Chcete-li <xref:System.Windows.Media.ImageBrush> zachovat poměr stran jeho obrazu, <xref:System.Windows.Media.Stretch.Uniform> nastavte <xref:System.Windows.Media.Stretch.UniformToFill> <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost na nebo .  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.ImageBrush> dva objekty k malování dvou obdélníků. Každý obdélník je 300 x 150 pixelů a každý obsahuje obraz 300 x 300 pixelů. Vlastnost <xref:System.Windows.Media.TileBrush.Stretch%2A> první stopy je <xref:System.Windows.Media.Stretch.Uniform>nastavena <xref:System.Windows.Media.TileBrush.Stretch%2A> na a vlastnost druhé <xref:System.Windows.Media.Stretch.UniformToFill>stopy je nastavena na .  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Následující obrázek znázorňuje výstup první <xref:System.Windows.Media.TileBrush.Stretch%2A> stopy, <xref:System.Windows.Media.Stretch.Uniform>která má nastavení .  
  
 ![ImageBrush s rovnoměrným roztažením](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Další obrázek znázorňuje výstup druhého <xref:System.Windows.Media.TileBrush.Stretch%2A> stopy, <xref:System.Windows.Media.Stretch.UniformToFill>který má nastavení .  
  
 ![ImageBrush s uniformyToFill strečink](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Všimněte <xref:System.Windows.Media.TileBrush.Stretch%2A> si, že vlastnost se <xref:System.Windows.Media.TileBrush> chová stejně pro <xref:System.Windows.Media.DrawingBrush> <xref:System.Windows.Media.VisualBrush>ostatní objekty, to znamená pro a . Další informace <xref:System.Windows.Media.ImageBrush> o ostatních <xref:System.Windows.Media.TileBrush> objektech naleznete v [tématu Malování obrázky, kresbami a vizuály](painting-with-images-drawings-and-visuals.md).  
  
 Všimněte si také, že i když se zdá, že <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost určuje, jak se <xref:System.Windows.Media.TileBrush> obsah roztáhne tak, aby odpovídal výstupní oblasti, ve skutečnosti určuje, jak se <xref:System.Windows.Media.TileBrush> obsah roztáhne, aby vyplnil svou základní dlaždici. Další informace naleznete v tématu <xref:System.Windows.Media.TileBrush>.  
  
 Tento příklad kódu je součástí většípříklad, který <xref:System.Windows.Media.ImageBrush> je k dispozici pro třídu. Kompletní ukázku naleznete v tématu [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.TileBrush>
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
