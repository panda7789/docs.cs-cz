---
title: 'Postup: Animace 3D rotace pomocí scénářů'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 088f1a33cfc73a706ffed55ffff6494adaf8fca4
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112208"
---
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a>Postup: Animace 3D rotace pomocí scénářů
Následující příklad ukazuje, jak provést 3D objekt otočit, zatímco se "zakolísá" animací <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> vlastnosti objektu. <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> Tento <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objekt určuje rotační transformaci 3D objektu, a proto animace jeho vlastností vytvoří efekt otočení touhy. V storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> se používá k <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> animaci vlastnost i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> min. <xref:System.Windows.Media.Animation.Vector3DAnimation>  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Animace 3D natočení pomocí funkce Rotation3DAnimation](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [Animace 3D natočení pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Přehled scénářů](storyboards-overview.md)
