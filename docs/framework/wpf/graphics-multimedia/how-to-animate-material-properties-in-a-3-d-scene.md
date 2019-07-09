---
title: 'Postupy: Animace vlastností materiálu ve 3D scéně'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: 8dfd7f01b87e2becfbcf57544ec4f8340cf8d5cc
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2019
ms.locfileid: "67662554"
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a>Postupy: Animace vlastností materiálu ve 3D scéně
Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost <xref:System.Windows.Media.Media3D.Material> použít na 3D model.  
  
 Následující příklad kódu definuje <xref:System.Windows.Media.LinearGradientBrush> použít jako <xref:System.Windows.Media.Media3D.Material> použít na 3D objekt.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <xref:System.Windows.Media.Brush.Opacity%2A> Vlastnosti tohoto <xref:System.Windows.Media.LinearGradientBrush> je animovaný pomocí následující příklad kódu.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorku.  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
