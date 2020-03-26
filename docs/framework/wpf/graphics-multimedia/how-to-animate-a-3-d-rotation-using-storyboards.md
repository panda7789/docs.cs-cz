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
# <a name="how-to-animate-a-3d-rotation-using-storyboards"></a><span data-ttu-id="d220c-102">Postup: Animace 3D rotace pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="d220c-102">How to: Animate a 3D Rotation Using Storyboards</span></span>
<span data-ttu-id="d220c-103">Následující příklad ukazuje, jak provést 3D objekt otočit, zatímco se "zakolísá" animací <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> a <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> vlastnosti objektu. <xref:System.Windows.Media.Media3D.AxisAngleRotation3D></span><span class="sxs-lookup"><span data-stu-id="d220c-103">The following example shows how to make a 3D object rotate while it "wobbles" by animating the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> and <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> properties of an <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object.</span></span> <span data-ttu-id="d220c-104">Tento <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> objekt určuje rotační transformaci 3D objektu, a proto animace jeho vlastností vytvoří efekt otočení touhy.</span><span class="sxs-lookup"><span data-stu-id="d220c-104">This <xref:System.Windows.Media.Media3D.AxisAngleRotation3D> object specifies the rotation transform of the 3D object and so animating its properties creates the desire rotation effect.</span></span> <span data-ttu-id="d220c-105">V storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> se používá k <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> animaci vlastnost i <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> min. <xref:System.Windows.Media.Animation.Vector3DAnimation></span><span class="sxs-lookup"><span data-stu-id="d220c-105">Within the Storyboard, <xref:System.Windows.Media.Animation.DoubleAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Angle%2A> property while <xref:System.Windows.Media.Animation.Vector3DAnimation> is used to animate the <xref:System.Windows.Media.Media3D.AxisAngleRotation3D.Axis%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d220c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d220c-106">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotate3DUsingAxisAngleRotation3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotat3DUsingAxisAngleRotation3DExample.xaml#rotate3dusingaxisanglerotation3dexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="d220c-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="d220c-107">See also</span></span>

- [<span data-ttu-id="d220c-108">Animace 3D natočení pomocí funkce Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="d220c-108">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="d220c-109">Animace 3D natočení pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="d220c-109">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="d220c-110">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="d220c-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="d220c-111">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="d220c-111">Storyboards Overview</span></span>](storyboards-overview.md)
