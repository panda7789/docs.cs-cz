---
title: 'Postupy: Kódování vizuálního souboru na obrázek'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- image files [WPF], encoding from visuals
- encoding image formats [WPF]
- visuals [WPF], encoding to an image file
ms.assetid: 2036385b-ea47-4d54-8027-5797f52c8149
ms.openlocfilehash: a9e847a46941c37efb735d5bfd13bde2dd74271c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560160"
---
# <a name="how-to-encode-a-visual-to-an-image-file"></a>Postupy: Kódování vizuálního souboru na obrázek
Tento příklad ukazuje, jak ke kódování <xref:System.Windows.Media.Visual> objektu do souboru bitové kopie pomocí <xref:System.Windows.Media.Imaging.RenderTargetBitmap> a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.DrawingVisual> Je vytvořený pomocí <xref:System.Windows.Media.Imaging.BitmapImage> a <xref:System.Windows.Media.FormattedText> které je vykresleno do <xref:System.Windows.Media.Imaging.RenderTargetBitmap>. Vykreslené rastrového obrázku se pak použije k vytvoření <xref:System.Windows.Media.Imaging.BitmapFrame> která se přidá do <xref:System.Windows.Media.Imaging.PngBitmapEncoder> pro vytvoření nového [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] souboru.  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample_Encode.cs#rtbencodeinline1)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#RTBEncodeInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample_Encode.vb#rtbencodeinline1)]  
  
 A <xref:System.Windows.Media.Imaging.PngBitmapEncoder> byl použit v tomto příkladu, ale některé z odvozené <xref:System.Windows.Media.Imaging.BitmapEncoder> objekty může byl použit pro vytvoření souboru bitové kopie.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.DrawingContext>  
 [Přehled obrázků](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Použití objektů DrawingVisual](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)
