---
title: 'Postupy: Animace trojrozměrné rotace s použitím klíčových snímků (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3-D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 6cb58c2ed97cad1539f3703c98b9af57b0af22fb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54637713"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="9b507-102">Postupy: Animace trojrozměrné rotace s použitím klíčových snímků (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="9b507-102">How to: Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="9b507-103">V následujícím příkladu <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> se využívá k Prognózování 3D objekt otočit.</span><span class="sxs-lookup"><span data-stu-id="9b507-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="9b507-104">Tato animace používá následující klíčové snímky:</span><span class="sxs-lookup"><span data-stu-id="9b507-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="9b507-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> slouží k vytvoření hladkého, lineární interpolaci mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="9b507-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="9b507-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> slouží k vytvoření i s náhlými "přeskakování" mezi hodnotami (žádné interpolace).</span><span class="sxs-lookup"><span data-stu-id="9b507-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="9b507-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> slouží k vytvoření proměnné přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9b507-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="9b507-108">V následujícím příkladu této části se animace spustila vypnout pomalé, ale na konci časového úseku, zrychluje exponenciálně zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="9b507-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b507-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b507-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9b507-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9b507-110">See also</span></span>
- [<span data-ttu-id="9b507-111">Animace trojrozměrného otočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="9b507-111">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="9b507-112">Animace trojrozměrného otočení pomocí Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="9b507-112">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="9b507-113">Animace 3D otočení pomocí kvaternionů</span><span class="sxs-lookup"><span data-stu-id="9b507-113">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="9b507-114">Animace trojrozměrné rotace pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="9b507-114">Animate a 3-D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="9b507-115">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="9b507-115">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [<span data-ttu-id="9b507-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="9b507-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
