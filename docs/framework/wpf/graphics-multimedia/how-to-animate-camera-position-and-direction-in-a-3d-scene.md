---
title: 'Postupy: Umístění kamery animace a směrování ve 3D scéně'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3D scenes
- camera direction [WPF], animating in 3D scenes
- 3D scenes [WPF], animating camera position
- 3D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3D scenes
- animation [WPF], camera direction in 3D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 5ce94e154cd5aa29b59260f893ec2b63a08db0fc
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112205"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Postupy: Umístění kamery animace a směrování ve 3D scéně
Následující příklad ukazuje, jak animovat polohu kamery a animovat směr, kterým ukazuje ve 3D scéně. To se provádí <xref:System.Windows.Media.Animation.Point3DAnimation> <xref:System.Windows.Media.Animation.Vector3DAnimation> pomocí a <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> animovat a <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> <xref:System.Windows.Media.Media3D.PerspectiveCamera>vlastnosti v uvedeném pořadí . Takovou animaci můžete použít ke změně pohledu diváka na scénu v reakci na událost.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [Animace umístění a směrování kamery pomocí klíčových snímků](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
