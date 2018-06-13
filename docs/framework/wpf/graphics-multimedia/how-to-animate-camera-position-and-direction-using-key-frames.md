---
title: 'Postupy: Umístění a směrování kamery animace pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 5be14513755c3b5c80c13cbc5cae889cc4663cec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558829"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Postupy: Umístění a směrování kamery animace pomocí klíčových snímků
V následujícím příkladu <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> se používá k animace pozice <xref:System.Windows.Media.Media3D.PerspectiveCamera> v 3D scény. Kromě toho <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> se používá k animace směr fotoaparát odkazuje v 3D scény. Obě tyto animací použít několik klíčových snímků, kterých se bude vytvářet řadu animace důsledky:  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> a <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> slouží k vytváření smooth, lineární interpolace mezi hodnotami.  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> a <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> slouží k vytváření nečekané "přeskočí" mezi hodnotami (žádné interpolace).  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> a <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> se používají k vytvoření proměnné přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> vlastnost. Animace v následujícím příkladu spustí vypnout pomalé, ale na konec časového úseku, urychluje exponenciálně.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Animace umístění a směrování kamery ve 3D scéně](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-in-a-3d-scene.md)  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
