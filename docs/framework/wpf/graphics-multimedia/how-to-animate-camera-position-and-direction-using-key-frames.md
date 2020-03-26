---
title: 'Postupy: Umístění a směrování kamery animace pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 28471f9b42140a6c75b043d33939503528b63194
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112164"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="6d976-102">Postupy: Umístění a směrování kamery animace pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="6d976-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="6d976-103">V následujícím příkladu <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> se používá k animaci polohy <xref:System.Windows.Media.Media3D.PerspectiveCamera> ve 3D scéně.</span><span class="sxs-lookup"><span data-stu-id="6d976-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="6d976-104">Kromě toho <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> se používá k animaci směru, kterým kamera ukazuje ve 3D scéně.</span><span class="sxs-lookup"><span data-stu-id="6d976-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="6d976-105">Obě tyto animace používají několik klíčových snímků, které vytvářejí řadu animačních efektů:</span><span class="sxs-lookup"><span data-stu-id="6d976-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1. <span data-ttu-id="6d976-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame>a <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> slouží k vytvoření hladké, lineární interpolace mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="6d976-106"><xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="6d976-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame>a <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> slouží k vytvoření náhlých "skoků" mezi hodnotami (bez interpolace).</span><span class="sxs-lookup"><span data-stu-id="6d976-107"><xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="6d976-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame>a <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> slouží k vytvoření proměnné přechodu <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> mezi hodnotami v závislosti na vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6d976-108"><xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="6d976-109">V níže uvedeném příkladu animace začíná pomalu, ale ke konci časového segmentu exponenciálně urychluje.</span><span class="sxs-lookup"><span data-stu-id="6d976-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d976-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d976-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6d976-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d976-111">See also</span></span>

- [<span data-ttu-id="6d976-112">Animace umístění a směrování kamery ve 3D scéně</span><span class="sxs-lookup"><span data-stu-id="6d976-112">Animate Camera Position and Direction in a 3D Scene</span></span>](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [<span data-ttu-id="6d976-113">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="6d976-113">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
