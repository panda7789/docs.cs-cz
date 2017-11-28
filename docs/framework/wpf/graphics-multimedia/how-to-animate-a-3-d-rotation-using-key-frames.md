---
title: "Postupy: Animace trojrozměrného otočení použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8dad8934dacd64f31cf65d7517d8c48114522505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a>Postupy: Animace trojrozměrného otočení použitím klíčových snímků
V následujícím příkladu <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> se používá k zajištění 3D objektu otočit při jeho osou otáčení animuje, výsledkem je "Němý". Tato animace používá následující klíčové snímky:  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>slouží k vytvoření smooth, lineární interpolace mezi hodnotami.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>slouží k vytvoření nečekané "přechodů" mezi hodnotami (žádné interpolace).  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>slouží k vytvoření proměnné přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> vlastnost. Tuto část animace v následujícím příkladu spustí vypnout pomalé, ale na konec časového úseku, urychluje exponenciálně.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Animace 3D otočení pomocí scénářů](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [Animace 3D otočení pomocí Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Animace 3D otočení pomocí Quaternions](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [Animace 3D otočení pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
