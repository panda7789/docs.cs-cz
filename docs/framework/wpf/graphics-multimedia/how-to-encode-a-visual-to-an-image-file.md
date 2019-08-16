---
title: 'Postupy: Kódování vizuálního objektu na soubor obrázku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: 193b6a14e404d32bb49d6e0ef3cbd513166bcce2
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545289"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Postupy: Kódování vizuálního objektu na soubor obrázku
Tento příklad ukazuje, jak kódovat <xref:System.Windows.Media.Visual> objekt do souboru obrázku <xref:System.Windows.Media.Imaging.RenderTargetBitmap> pomocí a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
## <a name="example"></a>Příklad  
 Je vytvořen <xref:System.Windows.Media.FormattedText> pomocí a, který je vykreslen do <xref:System.Windows.Media.Imaging.RenderTargetBitmap>. <xref:System.Windows.Media.Imaging.BitmapImage> <xref:System.Windows.Media.DrawingVisual> Vykreslený rastrový obrázek se pak použije k <xref:System.Windows.Media.Imaging.BitmapFrame> vytvoření nového souboru PNG ( <xref:System.Windows.Media.Imaging.PngBitmapEncoder> Portable Network Graphics), který se přidá do.  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 V tomto příkladu se použil nějaký odvozený <xref:System.Windows.Media.Imaging.BitmapEncoder> objekt, který by se mohl použít k vytvoření souboru obrázku. <xref:System.Windows.Media.Imaging.PngBitmapEncoder>  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.DrawingContext>
- [Přehled obrázků](imaging-overview.md)
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Použití objektů DrawingVisual](using-drawingvisual-objects.md)
