---
title: 'Postup: Animace 3D natočení pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D translations [WPF], animating [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
- key frames [WPF], QuaternionAnimationUsingKeyFrames
- animation [WPF], 3D translations [WPF], with key frames (QuaternionAnimationUsingKeyFrames)
ms.assetid: 09e5707b-7523-4a08-9aa7-bb13cbedccdf
ms.openlocfilehash: 5273183aaa49a743cc401dec0b4b16bae09e3129
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112294"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames-quaternionanimationusingkeyframes"></a><span data-ttu-id="11135-102">Postup: Animace 3D natočení pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="11135-102">How to: Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>
<span data-ttu-id="11135-103">V následujícím příkladu <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> se používá k otočení 3D objektu.</span><span class="sxs-lookup"><span data-stu-id="11135-103">In the following example, <xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames> is used to make a 3D object rotate.</span></span> <span data-ttu-id="11135-104">Tato animace používá následující klíčové snímky:</span><span class="sxs-lookup"><span data-stu-id="11135-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="11135-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>se používá k vytvoření hladké, lineární interpolace mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="11135-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="11135-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>se používá k vytvoření náhlých "skoků" mezi hodnotami (bez interpolace).</span><span class="sxs-lookup"><span data-stu-id="11135-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="11135-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>se používá k vytvoření proměnné přechodu <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> mezi hodnotami v závislosti na vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="11135-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="11135-108">V níže uvedeném příkladu začíná tato část animace pomalu, ale ke konci časového segmentu exponenciálně urychluje.</span><span class="sxs-lookup"><span data-stu-id="11135-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="11135-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="11135-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#QuaternionAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/QuaternionAnimationUsingKeyFramesExample.xaml#quaternionanimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="11135-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="11135-110">See also</span></span>

- [<span data-ttu-id="11135-111">Animace 3D natočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="11135-111">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="11135-112">Animace 3D natočení pomocí funkce Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="11135-112">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="11135-113">Animace 3D rotace pomocí quaternions</span><span class="sxs-lookup"><span data-stu-id="11135-113">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="11135-114">Animace 3D natočení pomocí klíčových snímků (Rotation3DAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="11135-114">Animate a 3D Rotation Using Key Frames (Rotation3DAnimationUsingKeyFrames)</span></span>](how-to-animate-a-3-d-rotation-using-key-frames.md)
- [<span data-ttu-id="11135-115">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="11135-115">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="11135-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="11135-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
