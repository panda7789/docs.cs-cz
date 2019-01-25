---
title: 'Postupy: Animace 3D otočení použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 129b672411edf03dc5b98d1568c49704e66bea25
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54663632"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a>Postupy: Animace 3D otočení použitím klíčových snímků
V následujícím příkladu <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> se využívá k Prognózování 3D objekt otočit při jeho osa otáčení animuje, což vede k "Němý". Tato animace používá následující klíčové snímky:  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> slouží k vytvoření hladkého, lineární interpolaci mezi hodnotami.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> slouží k vytvoření i s náhlými "přeskakování" mezi hodnotami (žádné interpolace).  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> slouží k vytvoření proměnné přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> vlastnost. V následujícím příkladu této části se animace spustila vypnout pomalé, ale na konci časového úseku, zrychluje exponenciálně zvyšuje.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [Přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [Animace trojrozměrného otočení pomocí scénářů](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animace trojrozměrného otočení pomocí Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animace 3D otočení pomocí kvaternionů](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animace trojrozměrné rotace pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
