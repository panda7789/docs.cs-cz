---
title: 'Postupy: Animace 3D otočení použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: e72ec94f830f0f5001a77e7492aa1326a47b309d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61762147"
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="29d89-102">Postupy: Animace 3D otočení použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="29d89-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="29d89-103">V následujícím příkladu <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> se využívá k Prognózování 3D objekt otočit při jeho osa otáčení animuje, což vede k "Němý".</span><span class="sxs-lookup"><span data-stu-id="29d89-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="29d89-104">Tato animace používá následující klíčové snímky:</span><span class="sxs-lookup"><span data-stu-id="29d89-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="29d89-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> slouží k vytvoření hladkého, lineární interpolaci mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="29d89-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="29d89-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> slouží k vytvoření i s náhlými "přeskakování" mezi hodnotami (žádné interpolace).</span><span class="sxs-lookup"><span data-stu-id="29d89-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="29d89-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> slouží k vytvoření proměnné přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="29d89-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="29d89-108">V následujícím příkladu této části se animace spustila vypnout pomalé, ale na konci časového úseku, zrychluje exponenciálně zvyšuje.</span><span class="sxs-lookup"><span data-stu-id="29d89-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29d89-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="29d89-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="29d89-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29d89-110">See also</span></span>

- [<span data-ttu-id="29d89-111">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="29d89-111">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="29d89-112">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="29d89-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="29d89-113">Animace trojrozměrného otočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="29d89-113">Animate a 3-D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="29d89-114">Animace trojrozměrného otočení pomocí Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="29d89-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="29d89-115">Animace 3D otočení pomocí kvaternionů</span><span class="sxs-lookup"><span data-stu-id="29d89-115">Animate a 3-D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="29d89-116">Animace trojrozměrné rotace pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="29d89-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
