---
title: 'Postupy: Vytvoření bitmapy z prostředí Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitmaps [WPF], rendering from visuals
- visuals [WPF], rendering to bitmaps
ms.assetid: 103fc7f5-7306-4026-9d61-2005e79959f3
ms.openlocfilehash: 429aacc99d8ead5a18e9be7602b19a74773b419a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57362861"
---
# <a name="how-to-create-a-bitmap-from-a-visual"></a>Postupy: Vytvoření bitmapy z prostředí Visual
Tento příklad ukazuje, jak můžete vytvořit rastrový obrázek z <xref:System.Windows.Media.Visual>. A <xref:System.Windows.Media.DrawingVisual> je vykreslen pomocí <xref:System.Windows.Media.FormattedText>. <xref:System.Windows.Media.Visual> Se pak vykreslí na <xref:System.Windows.Media.Imaging.RenderTargetBitmap> vytvoření bitmapy z daného textu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/RenderTargetBitmapExample.cs#creatertbimage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#CreateRTBImage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/RenderTargetBitmapExample.vb#creatertbimage)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.DrawingContext>
- [Přehled obrázků](imaging-overview.md)
- [Přehled nakreslených objektů](drawing-objects-overview.md)
- [Použití objektů DrawingVisual](using-drawingvisual-objects.md)
