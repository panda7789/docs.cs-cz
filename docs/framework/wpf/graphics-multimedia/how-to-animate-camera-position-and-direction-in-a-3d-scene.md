---
title: 'Postupy: Umístění kamery animace a směrování ve 3D scéně'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
ms.openlocfilehash: 429139da809a78474f4f6a082fb6e3c08c72d431
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558875"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a>Postupy: Umístění kamery animace a směrování ve 3D scéně
Následující příklad ukazuje, jak animace pozici fotoaparátu a použije animaci směr, který bude ukazovat v 3D scény. To se provádí pomocí <xref:System.Windows.Media.Animation.Point3DAnimation> a <xref:System.Windows.Media.Animation.Vector3DAnimation> pro animaci <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> a <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> vlastnosti v uvedeném pořadí <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Chcete-li změnit zobrazení onlooker scény v reakci na událost můžete použít animace takto.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.Vector3DAnimation>  
 <xref:System.Windows.Media.Animation.Point3DAnimation>  
 [Animace umístění a směrování kamery pomocí klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-camera-position-and-direction-using-key-frames.md)  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
