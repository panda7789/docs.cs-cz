---
title: 'Postupy: Oříznutí obrázku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: 189cb92d581ccc9209ebdb4de18487951d17818a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406301"
---
# <a name="how-to-crop-an-image"></a>Postupy: Oříznutí obrázku
Tento příklad ukazuje, jak chcete provést oříznutí image pomocí <xref:System.Windows.Media.Imaging.CroppedBitmap>.  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> se používá především při kódování oříznutý verzi image uložit si do souboru. Pokud chcete provést oříznutí obrázku pro zobrazení účely najdete v tématu [vytvořit oblast Ústřižku](https://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) tématu.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definuje prostředky používané v rámci níže.  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 Následující příklad vytvoří objekt pomocí bitové kopie <xref:System.Windows.Media.Imaging.CroppedBitmap> jako zdroj.  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> Může také sloužit jako zdroj jiný <xref:System.Windows.Media.Imaging.CroppedBitmap>, řetězení oříznutí. Všimněte si, že <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> používá hodnoty, které jsou relativní vzhledem k zdroji oříznuté rastrového obrázku a ne počáteční bitové kopie.  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a>Viz také  
 [Vytvořit oblast Ústřižku](https://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376)
