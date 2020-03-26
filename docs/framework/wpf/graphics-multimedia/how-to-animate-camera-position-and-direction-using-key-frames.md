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
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112164"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a>Postupy: Umístění a směrování kamery animace pomocí klíčových snímků
V následujícím příkladu <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> se používá k animaci polohy <xref:System.Windows.Media.Media3D.PerspectiveCamera> ve 3D scéně. Kromě toho <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> se používá k animaci směru, kterým kamera ukazuje ve 3D scéně. Obě tyto animace používají několik klíčových snímků, které vytvářejí řadu animačních efektů:  
  
1. <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>a <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> slouží k vytvoření hladké, lineární interpolace mezi hodnotami.  
  
2. <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>a <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> slouží k vytvoření náhlých "skoků" mezi hodnotami (bez interpolace).  
  
3. <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>a <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> slouží k vytvoření proměnné přechodu <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> mezi hodnotami v závislosti na vlastnosti. V níže uvedeném příkladu animace začíná pomalu, ale ke konci časového segmentu exponenciálně urychluje.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Animace umístění a směrování kamery ve 3D scéně](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
