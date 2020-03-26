---
title: 'Postup: Animace 3D překladů'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations
- 3D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: 7d4fff9c74663bd220ad5d15a983bcb639621afd
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112255"
---
# <a name="how-to-animate-3d-translations"></a>Postup: Animace 3D překladů
Toto téma ukazuje, jak animovat sadu transformace překladu na 3D modelu.  
  
 Níže uvedený kód ukazuje <xref:System.Windows.Media.Media3D.TranslateTransform3D> použití objektu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> na <xref:System.Windows.Media.Media3D.GeometryModel3D>vlastnost .  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 Vlastnost <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> tohoto <xref:System.Windows.Media.Media3D.TranslateTransform3D> objektu je animována pomocí níže uvedeného kódu.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorek.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled transformace](transforms-overview.md)
