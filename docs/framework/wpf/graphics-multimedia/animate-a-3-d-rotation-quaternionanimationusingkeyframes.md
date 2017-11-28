---
title: "Postupy: Animace trojrozměrného otočení použitím klíčových snímků (QuaternionAnimationUsingKeyFrames)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 61968c13d395187d1190c7a2eaaa2bfe3f6072e4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a>Postupy: Animace trojrozměrného otočení použitím klíčových snímků (QuaternionAnimationUsingKeyFrames)
V následujícím příkladu <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> se používá k zajištění otočit 3D objektu. Tato animace používá následující klíčové snímky:  
  
1.  <xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>slouží k vytvoření smooth, lineární interpolace mezi hodnotami.  
  
2.  <xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>slouží k vytvoření nečekané "přechodů" mezi hodnotami (žádné interpolace).  
  
3.  <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>slouží k vytvoření proměnné přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> vlastnost. Tuto část animace v následujícím příkladu spustí vypnout pomalé, ale na konec časového úseku, urychluje exponenciálně.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Animace 3D otočení pomocí scénářů](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [Animace 3D otočení pomocí Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [Animace 3D otočení pomocí Quaternions](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [Animace 3D otočení pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Přehled animací jednotlivých klíč](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
