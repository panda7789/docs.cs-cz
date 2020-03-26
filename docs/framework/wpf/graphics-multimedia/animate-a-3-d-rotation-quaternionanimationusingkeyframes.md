---
title: 'Postup: Animace 3D natočení pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112294"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Postup: Animace 3D natočení pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)
V následujícím příkladu <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> se používá k otočení 3D objektu. Tato animace používá následující klíčové snímky:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>se používá k vytvoření hladké, lineární interpolace mezi hodnotami.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>se používá k vytvoření náhlých "skoků" mezi hodnotami (bez interpolace).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>se používá k vytvoření proměnné přechodu <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> mezi hodnotami v závislosti na vlastnosti. V níže uvedeném příkladu začíná tato část animace pomalu, ale ke konci časového segmentu exponenciálně urychluje.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Animace 3D natočení pomocí scénářů](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animace 3D natočení pomocí funkce Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animace 3D rotace pomocí quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animace 3D natočení pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
