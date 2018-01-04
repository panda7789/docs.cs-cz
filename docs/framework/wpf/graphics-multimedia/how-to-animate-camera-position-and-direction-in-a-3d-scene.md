---
title: "Postupy: Umístění kamery animace a směrování ve 3D scéně"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], camera position in 3-D scenes
- camera direction [WPF], animating in 3-D scenes
- 3-D scenes [WPF], animating camera position
- 3-D scenes [WPF], animating camera direction
- camera position [WPF], animating in 3-D scenes
- animation [WPF], camera direction in 3-D scenes
ms.assetid: 480224b7-a5e5-4165-ba7f-ef760ddff94a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8e80f1032e886d59240b74281c2ed87ad5743a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
