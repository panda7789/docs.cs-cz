---
title: 'Postupy: Animace trojrozměrného otočení pomocí scénářů'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF]
- 3-D translations [WPF], animating [WPF], with Storyboards
- animation [WPF], 3-D translations [WPF], with Storyboards
ms.assetid: 1020e44e-e21e-49a8-be53-53cbc1910e83
ms.openlocfilehash: 03b01205f1a31426a01b09533b350682c384df4b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024752"
---
# <a name="how-to-animate-a-3-d-rotation-using-storyboards"></a><span data-ttu-id="b3b68-102">Postupy: Animace trojrozměrného otočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="b3b68-102">How to: Animate a 3-D Rotation Using Storyboards</span></span>
<span data-ttu-id="b3b68-103">Následující příklad ukazuje, jak 3D objekt otočit při jeho "wobbles" podle animace <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> vlastnosti <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objektu.</span><span class="sxs-lookup"><span data-stu-id="b3b68-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="b3b68-104">To <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objekt určuje transformace otočení 3D objektu a tak animace vlastností vytvoří efekt otočení přání.</span><span class="sxs-lookup"><span data-stu-id="b3b68-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="b3b68-105">Ve scénáři <xref:System.Windows.Media.Animation.DoubleAnimation> je použít pro animaci <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> vlastnost při <xref:System.Windows.Media.Animation.Vector3DAnimation> je použít pro animaci <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b3b68-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3b68-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3b68-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b3b68-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b3b68-107">See also</span></span>

- [<span data-ttu-id="b3b68-108">Animace trojrozměrného otočení pomocí Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="b3b68-108">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="b3b68-109">Animace trojrozměrné rotace pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="b3b68-109">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="b3b68-110">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="b3b68-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="b3b68-111">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="b3b68-111">Storyboards Overview</span></span>](storyboards-overview.md)
