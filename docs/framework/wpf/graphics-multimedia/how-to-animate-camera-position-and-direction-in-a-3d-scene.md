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
ms.openlocfilehash: 459b668c134e31afe295dd311094ac9cf84d884a
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374021"
---
# <a name="how-to-animate-camera-position-and-direction-in-a-3d-scene"></a><span data-ttu-id="5d9a2-102">Postupy: Umístění kamery animace a směrování ve 3D scéně</span><span class="sxs-lookup"><span data-stu-id="5d9a2-102">How to: Animate Camera Position and Direction in a 3D Scene</span></span>
<span data-ttu-id="5d9a2-103">Následující příklad ukazuje, jak umístění kamery animace a animovat směr, který se odkazuje ve 3D scéně.</span><span class="sxs-lookup"><span data-stu-id="5d9a2-103">The following example shows how to animate the position of a camera and animate the direction it is pointing in a 3D scene.</span></span> <span data-ttu-id="5d9a2-104">To se provádí pomocí <xref:System.Windows.Media.Animation.Point3DAnimation> a <xref:System.Windows.Media.Animation.Vector3DAnimation> pro animaci <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> a <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> vlastnosti v uvedeném pořadí <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span><span class="sxs-lookup"><span data-stu-id="5d9a2-104">This is done by using <xref:System.Windows.Media.Animation.Point3DAnimation> and <xref:System.Windows.Media.Animation.Vector3DAnimation> to animate the <xref:System.Windows.Media.Media3D.ProjectionCamera.Position%2A> and <xref:System.Windows.Media.Media3D.ProjectionCamera.LookDirection%2A> properties respectively of the <xref:System.Windows.Media.Media3D.PerspectiveCamera>.</span></span> <span data-ttu-id="5d9a2-105">Chcete-li změnit zobrazení onlooker scény v reakci na událost můžete použít animace následujícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="5d9a2-105">You might use an animation like this to change the onlooker's view of a scene in response to an event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d9a2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d9a2-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationExample.xaml#pointvector3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5d9a2-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d9a2-107">See also</span></span>
- <xref:System.Windows.Media.Animation.Vector3DAnimation>
- <xref:System.Windows.Media.Animation.Point3DAnimation>
- [<span data-ttu-id="5d9a2-108">Animace umístění a směrování kamery pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="5d9a2-108">Animate Camera Position and Direction Using Key Frames</span></span>](how-to-animate-camera-position-and-direction-using-key-frames.md)
- [<span data-ttu-id="5d9a2-109">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="5d9a2-109">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
