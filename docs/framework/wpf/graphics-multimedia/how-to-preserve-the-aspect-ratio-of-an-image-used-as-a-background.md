---
title: 'Postupy: Zachování poměru stran u obrázku na pozadí'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 4ae6f1242548038bcd54b7218783e5063fa67872
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61921750"
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Postupy: Zachování poměru stran u obrázku na pozadí
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.ImageBrush> aby bylo možné zachovat poměr stran obrázku.  
  
 Ve výchozím nastavení při použití <xref:System.Windows.Media.ImageBrush> k vykreslení oblasti, jeho obsah roztáhne pro úplně naplnění výstupní oblasti. Při různých poměry stran mají výstupní oblasti a bitovou kopii, bitovou kopii je narušeny tento roztažení.  
  
 Chcete-li <xref:System.Windows.Media.ImageBrush> zachování poměru stran jeho bitové kopie, nastavte <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dva <xref:System.Windows.Media.ImageBrush> objekty k vykreslení dvou obdélníků. Každý obdélníku je 300 x 150 pixelů a každý obsahuje bitovou kopii 300 podle 300 pixelů. <xref:System.Windows.Media.TileBrush.Stretch%2A> První štětce je nastavena na <xref:System.Windows.Media.Stretch.Uniform>a <xref:System.Windows.Media.TileBrush.Stretch%2A> druhý štětce je nastavena na <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Následující obrázek znázorňuje výstup první štětec, který má <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![ImageBrush s jednotnou roztažení](./media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Následující obrázek znázorňuje výstup druhý štětec, který má <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![ImageBrush s roztažením UniformToFill](./media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Všimněte si, že <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost chová stejně jako pro ostatní <xref:System.Windows.Media.TileBrush> objekty, to znamená pro <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>. Další informace o <xref:System.Windows.Media.ImageBrush> a druhý <xref:System.Windows.Media.TileBrush> objekty, najdete [Malování pomocí obrázků, kreseb a vizuálních](painting-with-images-drawings-and-visuals.md).  
  
 Všimněte si také, že, i když <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost se zobrazí, zadejte způsob, jak <xref:System.Windows.Media.TileBrush> obsah roztáhne podle jeho výstupní oblasti, ve skutečnosti určuje způsob, jak <xref:System.Windows.Media.TileBrush> obsahu úsecích tak, aby vyplnil svůj základní dlaždice. Další informace naleznete v tématu <xref:System.Windows.Media.TileBrush>.  
  
 Tento příklad kódu je součástí většího příkladu, která je k dispozici pro <xref:System.Windows.Media.ImageBrush> třídy. Úplnou ukázku najdete v tématu [ImageBrush ukázka](https://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.TileBrush>
- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
