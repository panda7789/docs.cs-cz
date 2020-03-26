---
title: 'Postup: Animace 3D natočení pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112307"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a>Postup: Animace 3D natočení pomocí klíčových snímků
V následujícím příkladu se používá k otočení 3D objektu, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> zatímco jeho osa natočení animuje, což vede k "zakolísání". Tato animace používá následující klíčové snímky:  
  
1. <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>se používá k vytvoření hladké, lineární interpolace mezi hodnotami.  
  
2. <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>se používá k vytvoření náhlých "skoků" mezi hodnotami (bez interpolace).  
  
3. <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>se používá k vytvoření proměnné přechodu <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> mezi hodnotami v závislosti na vlastnosti. V níže uvedeném příkladu začíná tato část animace pomalu, ale ke konci časového segmentu exponenciálně urychluje.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled animací klíčových snímků](key-frame-animations-overview.md)
- [Animace 3D natočení pomocí scénářů](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animace 3D natočení pomocí funkce Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animace 3D rotace pomocí quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Animace 3D natočení pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
