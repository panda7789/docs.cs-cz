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
ms.openlocfilehash: 5df3a201eaae4ddcf2e5d5aac3de6e0d5013947c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353397"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Postupy: Umístění a směrování kamery animace pomocí klíčových snímků
V následujícím příkladu <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> slouží k animace umístění <xref:System.Windows.Media.Media3D.PerspectiveCamera> ve 3D scéně. Kromě toho <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> je použít pro animaci směr odkazuje fotoaparátu/kamery ve 3D scéně. Obě tyto animace budete používat několik klíčových snímků, které vytvářejí řadu efekty animace:  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> a <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> slouží k vytvoření hladkého, lineární interpolaci mezi hodnotami.  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> a <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> slouží k vytvoření i s náhlými "přeskakování" mezi hodnotami (žádné interpolace).  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> a <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> se používají k vytváření proměnných přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> vlastnost. Animace v následujícím příkladu spustí vypnout pomalé, ale na konci časového úseku, zrychluje exponenciálně zvyšuje.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Animace umístění a směrování kamery ve 3D scéně](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
