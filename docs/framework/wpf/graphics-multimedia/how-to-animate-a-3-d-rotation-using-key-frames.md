---
title: 'Postup: Animace 3D natočení pomocí klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
ms.openlocfilehash: 2b9059df079125c34c70237c0f600751020044c6
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112307"
---
# <a name="how-to-animate-a-3d-rotation-using-key-frames"></a><span data-ttu-id="1e671-102">Postup: Animace 3D natočení pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="1e671-102">How to: Animate a 3D Rotation Using Key Frames</span></span>
<span data-ttu-id="1e671-103">V následujícím příkladu se používá k otočení 3D objektu, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> zatímco jeho osa natočení animuje, což vede k "zakolísání".</span><span class="sxs-lookup"><span data-stu-id="1e671-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="1e671-104">Tato animace používá následující klíčové snímky:</span><span class="sxs-lookup"><span data-stu-id="1e671-104">This animation uses the following key frames:</span></span>  
  
1. <span data-ttu-id="1e671-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>se používá k vytvoření hladké, lineární interpolace mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="1e671-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="1e671-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>se používá k vytvoření náhlých "skoků" mezi hodnotami (bez interpolace).</span><span class="sxs-lookup"><span data-stu-id="1e671-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3. <span data-ttu-id="1e671-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>se používá k vytvoření proměnné přechodu <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> mezi hodnotami v závislosti na vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1e671-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="1e671-108">V níže uvedeném příkladu začíná tato část animace pomalu, ale ke konci časového segmentu exponenciálně urychluje.</span><span class="sxs-lookup"><span data-stu-id="1e671-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e671-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e671-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="1e671-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e671-110">See also</span></span>

- [<span data-ttu-id="1e671-111">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="1e671-111">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="1e671-112">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="1e671-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="1e671-113">Animace 3D natočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="1e671-113">Animate a 3D Rotation Using Storyboards</span></span>](how-to-animate-a-3-d-rotation-using-storyboards.md)
- [<span data-ttu-id="1e671-114">Animace 3D natočení pomocí funkce Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="1e671-114">Animate a 3D Rotation Using Rotation3DAnimation</span></span>](how-to-animate-a-3-d-rotation-using-rotation3danimation.md)
- [<span data-ttu-id="1e671-115">Animace 3D rotace pomocí quaternions</span><span class="sxs-lookup"><span data-stu-id="1e671-115">Animate a 3D Rotation Using Quaternions</span></span>](how-to-animate-a-3-d-rotation-using-quaternions.md)
- [<span data-ttu-id="1e671-116">Animace 3D natočení pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="1e671-116">Animate a 3D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
