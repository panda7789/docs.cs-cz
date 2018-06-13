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
ms.openlocfilehash: 46c559356447688e52508b823cc260c13128208f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553803"
---
# <a name="how-to-crop-an-image"></a>Postupy: Oříznutí obrázku
Tento příklad ukazuje, jak oříznout k bitovou kopii pomocí <xref:System.Windows.Media.Imaging.CroppedBitmap>.  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> slouží především při kódování oříznutý verze bitové kopie na Uložit si do souboru. Ořízne obrázek zobrazení účely najdete v tématu [vytvořit oblasti oříznutí](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376) tématu.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definuje prostředky používané v rámci ukázky níže.  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 Následující příklad vytvoří k pomocí bitové kopie <xref:System.Windows.Media.Imaging.CroppedBitmap> jako svůj zdroj.  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <xref:System.Windows.Media.Imaging.CroppedBitmap> Lze také použít jako zdroj jiný <xref:System.Windows.Media.Imaging.CroppedBitmap>, řetězení oříznutí. Všimněte si, že <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> používá hodnoty, které jsou relativní vzhledem k zdroji oříznout rastrového obrázku a není počáteční bitové kopie.  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření klip oblasti](http://msdn.microsoft.com/library/56e4bed6-78d7-4292-b917-d72d0b3e4376)
