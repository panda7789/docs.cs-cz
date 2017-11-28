---
title: "Postupy: Animace 3D otočení použitím kvaternionů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- quaternions [WPF]
- animation [WPF], 3-D translations [WPF], with quaternions
- 3-D translations [WPF], animating [WPF], with quaternions
ms.assetid: adca9cb1-066b-4de8-abbb-6b4007579ee7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4485e7dfc6a72f559f6df69f77e7afd98ab8aaf5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-quaternions"></a>Postupy: Animace 3D otočení použitím kvaternionů
Tento příklad ukazuje postup animace natočení 3D objektu pomocí quaternions.  
  
 Kód uvedený níže ukazuje <xref:System.Windows.Media.Media3D.QuaternionRotation3D> použít jako hodnotu <xref:System.Windows.Media.Media3D.RotateTransform3D.Rotation%2A> vlastnost <xref:System.Windows.Media.Media3D.RotateTransform3D>.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline1)]  
  
 To <xref:System.Windows.Media.Media3D.QuaternionRotation3D> je animovaný s <xref:System.Windows.Media.Animation.QuaternionAnimation> v rámci <xref:System.Windows.Media.Animation.Storyboard> pomocí kódu níže.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexampleinline2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celé ukázce.  
  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationExample.xaml#quaternionanimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Animace – přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vytvoření 3D scény](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Transformuje – přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Animace 3D otočení pomocí scénářů](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [Animace 3D otočení pomocí Rotation3DAnimation](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
