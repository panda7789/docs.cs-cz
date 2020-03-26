---
title: 'Postup: Animace 3D rotace pomocí quaternions'
ms.date: 03/30/2017
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3D translations [WPF], with quaternions
- 3D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
ms.openlocfilehash: 0d229b0a714cc53459943fae751ab4d4f787d7d8
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112242"
---
# <a name="how-to-animate-a-3d-rotation-using-quaternions"></a>Postup: Animace 3D rotace pomocí quaternions
Tento příklad ukazuje, jak animovat otočení 3D objektu pomocí quaternions.  
  
 Níže uvedený kód <xref:System.Windows.Media.Media3D.QuaternionRotation3D> ukazuje použitou <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> jako hodnota <xref:System.Windows.Media.Media3D.RotateTransform3D>vlastnosti .  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 To <xref:System.Windows.Media.Media3D.QuaternionRotation3D> je animovaný <xref:System.Windows.Media.Animation.QuaternionAnimation> s <xref:System.Windows.Media.Animation.Storyboard> v rámci pomocí kódu níže.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorek.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Přehled animace](animation-overview.md)
- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled transformace](transforms-overview.md)
- [Animace 3D natočení pomocí scénářů](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animace 3D natočení pomocí funkce Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
