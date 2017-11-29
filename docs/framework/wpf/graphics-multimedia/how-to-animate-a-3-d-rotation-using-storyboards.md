---
title: "Postupy: Animace trojrozměrného otočení použitím scénářů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 56839dfc5382f5dd56ec0b26d4aabe42536bf04e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="bd72a-102">Postupy: Animace trojrozměrného otočení použitím scénářů</span><span class="sxs-lookup"><span data-stu-id="bd72a-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="bd72a-103">Následující příklad ukazuje, jak vytvořit objekt 3D otočit při jeho "wobbles" podle animace <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> vlastnosti <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objektu.</span><span class="sxs-lookup"><span data-stu-id="bd72a-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="bd72a-104">To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objektu určuje otočení transformace 3D objektu, a proto animace jeho vlastnosti vytvoří desire otočení účinek.</span><span class="sxs-lookup"><span data-stu-id="bd72a-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="bd72a-105">Ve scénáři <xref:System.Windows.Media.Animation.DoubleAnimation> se používá k animace <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> vlastnost při <xref:System.Windows.Media.Animation.Vector3DAnimation> se používá k animace <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="bd72a-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bd72a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bd72a-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bd72a-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="bd72a-107">See Also</span></span>  
 [<span data-ttu-id="bd72a-108">Animace 3D otočení pomocí Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="bd72a-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="bd72a-109">Animace 3D otočení pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="bd72a-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)  
 [<span data-ttu-id="bd72a-110">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="bd72a-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="bd72a-111">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="bd72a-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
