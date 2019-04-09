---
title: 'Postupy: Animace umístění a směrování kamery pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], camera direction with key frames
- key frames [WPF], animating camera direction
- animation [WPF], camera position with key frames
- camera position [WPF], animating with key frames
- key frames [WPF], animating camera position
- camera direction [WPF], animating with key frames
ms.assetid: 5753024e-0057-454d-947f-43ea686879c7
ms.openlocfilehash: 3be3fc8d82d9c3061891bd67605548c49230ef87
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59143231"
---
# <a name="how-to-animate-camera-position-and-direction-using-key-frames"></a><span data-ttu-id="6b808-102">Postupy: Animace umístění a směrování kamery pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="6b808-102">How to: Animate Camera Position and Direction Using Key Frames</span></span>
<span data-ttu-id="6b808-103">V následujícím příkladu <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> slouží k animace umístění <xref:System.Windows.Media.Media3D.PerspectiveCamera> ve 3D scéně.</span><span class="sxs-lookup"><span data-stu-id="6b808-103">In the following example, <xref:System.Windows.Media.Animation.Point3DAnimationUsingKeyFrames> is used to animate the position of a <xref:System.Windows.Media.Media3D.PerspectiveCamera> in a 3D scene.</span></span> <span data-ttu-id="6b808-104">Kromě toho <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> je použít pro animaci směr odkazuje fotoaparátu/kamery ve 3D scéně.</span><span class="sxs-lookup"><span data-stu-id="6b808-104">In addition, <xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames> is used to animate the direction the camera is pointing in the 3D scene.</span></span> <span data-ttu-id="6b808-105">Obě tyto animace budete používat několik klíčových snímků, které vytvářejí řadu efekty animace:</span><span class="sxs-lookup"><span data-stu-id="6b808-105">Both of these animations use several key frames which create a series of animation effects:</span></span>  
  
1.  <xref:System.Windows.Media.Animation.LinearPoint3DKeyFrame> <span data-ttu-id="6b808-106">a <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> slouží k vytvoření hladkého, lineární interpolaci mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="6b808-106">and <xref:System.Windows.Media.Animation.LinearVector3DKeyFrame> are used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <xref:System.Windows.Media.Animation.DiscretePoint3DKeyFrame> <span data-ttu-id="6b808-107">a <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> slouží k vytvoření i s náhlými "přeskakování" mezi hodnotami (žádné interpolace).</span><span class="sxs-lookup"><span data-stu-id="6b808-107">and <xref:System.Windows.Media.Animation.DiscreteVector3DKeyFrame> are used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame> <span data-ttu-id="6b808-108">a <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> se používají k vytváření proměnných přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6b808-108">and <xref:System.Windows.Media.Animation.SplineVector3DKeyFrame> are used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplinePoint3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="6b808-109">Animace v následujícím příkladu spustí vypnout pomalé, ale na konci časového úseku, zrychluje exponenciálně zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="6b808-109">In the example below, the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b808-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b808-110">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#PointVector3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/PointVector3DAnimationUsingKeyFramesExample.xaml#pointvector3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6b808-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b808-111">See also</span></span>

- [<span data-ttu-id="6b808-112">Animace umístění a směrování kamery ve 3D scéně</span><span class="sxs-lookup"><span data-stu-id="6b808-112">Animate Camera Position and Direction in a 3D Scene</span></span>](how-to-animate-camera-position-and-direction-in-a-3d-scene.md)
- [<span data-ttu-id="6b808-113">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="6b808-113">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
