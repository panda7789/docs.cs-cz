---
title: 'Postupy: Zachování poměru stran u obrázku na pozadí'
ms.date: 03/30/2017
helpviewer_keywords:
- aspect ratios of background images [WPF], preserving
- brushes [WPF], preserving aspect ratios of background images
- background images [WPF], preserving aspect ratios
ms.assetid: 28c39478-13d7-4011-80a3-8b9cc3e54478
ms.openlocfilehash: 906033b43ba657acc873f12a00000189db6796ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-preserve-the-aspect-ratio-of-an-image-used-as-a-background"></a>Postupy: Zachování poměru stran u obrázku na pozadí
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.ImageBrush> Chcete-li zachovat poměr stran obrázku.  
  
 Ve výchozím nastavení se při použití <xref:System.Windows.Media.ImageBrush> k vyplnění oblast, její obsah roztahovány úplně zaplnění výstupní oblasti. Pokud mají různé poměrům stran oblasti výstup a bitovou kopii, bitovou kopii je poškozený, podle této roztažení.  
  
 Chcete-li <xref:System.Windows.Media.ImageBrush> zachová poměr stran jeho bitové kopie, nastavte <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost <xref:System.Windows.Media.Stretch.Uniform> nebo <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá dva <xref:System.Windows.Media.ImageBrush> objekty k vyplnění dvou tvaru. Každý rámeček je 300 o 150 pixelů a každý obsahuje bitovou kopii 300 podle 300 pixelů. <xref:System.Windows.Media.TileBrush.Stretch%2A> První stopy je nastavena na <xref:System.Windows.Media.Stretch.Uniform>a <xref:System.Windows.Media.TileBrush.Stretch%2A> druhý štětce je nastavena na <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushStretchModesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/StretchModes.cs#imagebrushstretchmodesexamplewholepage)]  
  
 Následující obrázek ukazuje výstup první štětce, který má <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení <xref:System.Windows.Media.Stretch.Uniform>.  
  
 ![Objekt ImageBrush s Uniform roztažení](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformstretch.jpg "graphicsmm_ImageBrushUniformStretch")  
  
 Následující obrázek znázorňuje, výstup druhý štětce, který má <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavení <xref:System.Windows.Media.Stretch.UniformToFill>.  
  
 ![Objekt ImageBrush s roztažením UniformToFill](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-imagebrushuniformtofillstretch.jpg "graphicsmm_ImageBrushUniformToFillStretch")  
  
 Všimněte si, že <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnost se chová stejně pro druhý <xref:System.Windows.Media.TileBrush> objekty, který je pro <xref:System.Windows.Media.DrawingBrush> a <xref:System.Windows.Media.VisualBrush>. Další informace o <xref:System.Windows.Media.ImageBrush> a dalších <xref:System.Windows.Media.TileBrush> objekty, najdete v části [vykreslování s obrázky, kresby a vizuální prvky](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md).  
  
 Všimněte si také, že i když <xref:System.Windows.Media.TileBrush.Stretch%2A> vlastnosti se zobrazí, zadejte jak <xref:System.Windows.Media.TileBrush> obsah roztahovány podle jeho výstup oblasti, ve skutečnosti určuje, jak <xref:System.Windows.Media.TileBrush> obsahu úsecích k vyplnění jeho základní dlaždice. Další informace naleznete v tématu <xref:System.Windows.Media.TileBrush>.  
  
 Tento příklad kódu je součástí většího příkladu vztahujícího se k <xref:System.Windows.Media.ImageBrush> třídy. Kompletní příklad, najdete v části [Objekt ImageBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160005).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.TileBrush>  
 [Malování pomocí obrázků, kreseb a vizuálních objektů](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
