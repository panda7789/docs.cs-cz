---
title: 'Postupy: Načtení obrázku jako miniatury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: f984293a395e925368b20cef6aa0cd902bd6fc15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134040"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a>Postupy: Načtení obrázku jako miniatury
Následující příklady ukazují, jak načíst <xref:System.Windows.Controls.Image> jako miniatury pro konzervaci paměti aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] snížit velikost paměti, které jsou nutné k načtení obrázku.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage> v kód pro omezení paměti potřebných k načtení obrázku.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled obrázků](imaging-overview.md)
