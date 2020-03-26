---
title: 'Postup: Animace 3D rotace pomocí funkce Rotation3DAnimation'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with Rotation3DAnimation
- Rotation3DAnimation [WPF]
- animation [WPF], 3D translations [WPF], with Rotation3DAnimation
ms.assetid: a92223ec-b634-4f5e-8e79-d33bc43ecfb3
ms.openlocfilehash: 4016b2e17d273fc401d00e769ce721e6a381cc23
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112229"
---
# <a name="how-to-animate-a-3d-rotation-using-rotation3danimation"></a>Postup: Animace 3D rotace pomocí funkce Rotation3DAnimation
Následující příklad ukazuje, jak 3D objekt otočit, zatímco se <xref:System.Windows.Media.Animation.Rotation3DAnimation> "zakolísá" pomocí animovat <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost objektu <xref:System.Windows.Media.Media3D.RotateTransform3D> aplikovaného na 3D objekt.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationExample.xaml#rotation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Animace 3D natočení pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [Animace 3D natočení pomocí scénářů](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [Animace 3D rotace pomocí quaternions](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [Přehled animace](animation-overview.md)
