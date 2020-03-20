---
title: 'Postupy: Vykreslení obrázku v oblasti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], painting with
- painting [WPF], with images
- brushes [WPF], painting with images
ms.assetid: 3432c533-1fc7-492d-94ee-0b13d60125ae
ms.openlocfilehash: 92969778c04c6ac634a2964c402d6c3439b96b49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186056"
---
# <a name="how-to-paint-an-area-with-an-image"></a>Postupy: Vykreslení obrázku v oblasti
Tento příklad ukazuje, <xref:System.Windows.Media.ImageBrush> jak použít třídu k malování oblasti s obrazem. Zobrazí <xref:System.Windows.Media.ImageBrush> jeden obrázek, který je <xref:System.Windows.Media.ImageBrush.ImageSource%2A> určen jeho vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad maluje <xref:System.Windows.Controls.Control.Background%2A> tlačítko pomocí <xref:System.Windows.Media.ImageBrush>.  
  
 [!code-csharp[UsingImageBrush_snip#ImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/PaintingWithImagesExample.cs#imagebrushexamplewholepage)]  
  
 Ve výchozím <xref:System.Windows.Media.ImageBrush> nastavení roztáhne obraz tak, aby zcela vyplnil oblast, kterou malujete. V předchozím příkladu je obraz roztažen tak, aby vyplnil tlačítko, což může obrázek zkreslit. Toto chování můžete řídit <xref:System.Windows.Media.TileBrush.Stretch%2A> nastavením <xref:System.Windows.Media.Stretch.Uniform> <xref:System.Windows.Media.Stretch.UniformToFill>vlastnosti <xref:System.Windows.Media.TileBrush> nebo , která způsobí, že stopa zachová poměr stran obrazu.  
  
 Pokud nastavíte <xref:System.Windows.Media.TileBrush.TileMode%2A> vlastnosti <xref:System.Windows.Media.ImageBrush> <xref:System.Windows.Media.TileBrush.Viewport%2A> a , můžete vytvořit opakující se vzorek. Následující příklad maluje tlačítko pomocí vzoru, který je vytvořen z obrazu.  
  
 [!code-csharp[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TiledImageBrushExample.cs#tiledimagebrushexamplewholepage)]
 [!code-vb[UsingImageBrush_snip#TiledImageBrushExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/UsingImageBrush_snip/VisualBasic/TiledImageBrushExample.vb#tiledimagebrushexamplewholepage)]  
  
 Další informace o <xref:System.Windows.Media.ImageBrush> třídě naleznete v tématu [Malování obrázky, kresby a vizuály](painting-with-images-drawings-and-visuals.md).  
  
 Tento příklad kódu je součástí většípříklad, který <xref:System.Windows.Media.ImageBrush> je k dispozici pro třídu. Kompletní ukázku naleznete v tématu [ImageBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/ImageBrush).  
  
## <a name="see-also"></a>Viz také

- [Malování pomocí obrázků, kreseb a vizuálních objektů](painting-with-images-drawings-and-visuals.md)
