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
ms.openlocfilehash: 349a602a10b89931701e24334bf5ac5536f26400
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33562320"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a>Postupy: Načtení obrázku jako miniatury
Následující příklady ukazují, jak načíst <xref:System.Windows.Controls.Image> jako miniaturu pro konzervaci paměti aplikace.  
  
## <a name="example"></a>Příklad  
 Následující příklad nastavuje <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] snížit velikost paměti vyžadované pro načtení bitovou kopii.  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a>Příklad  
 Následující příklad nastavuje <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage> v kódu snížit velikost paměti vyžadované pro načtení bitovou kopii.  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled obrázků](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
