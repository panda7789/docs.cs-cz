---
title: 'Postupy: Animace trojrozměrného otočení použitím scénářů'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 0e5e0b4e2b991b15ff7a49da65bfe96485e66fcc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54589802"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a>Postupy: Animace trojrozměrného otočení použitím scénářů
Následující příklad ukazuje, jak 3D objekt otočit při jeho "wobbles" podle animace <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> vlastnosti <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objektu. To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objekt určuje transformace otočení 3D objektu a tak animace vlastností vytvoří efekt otočení přání. Ve scénáři <xref:System.Windows.Media.Animation.DoubleAnimation> je použít pro animaci <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> vlastnost při <xref:System.Windows.Media.Animation.Vector3DAnimation> je použít pro animaci <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> vlastnost.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Animace trojrozměrného otočení pomocí Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animace trojrozměrné rotace pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
