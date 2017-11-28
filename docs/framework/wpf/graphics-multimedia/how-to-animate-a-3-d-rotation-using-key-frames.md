---
title: "Postupy: Animace trojrozměrného otočení použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations [WPF], with key frames (Rotation3DAnimation)
- key frames [WPF], Rotation3DAnimation
- 3-D translations [WPF], animating [WPF], with key frames (Rotation3DAnimation)
ms.assetid: 6f671b95-7f30-4836-9a4f-aeb7dc30121f
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8dad8934dacd64f31cf65d7517d8c48114522505
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-animate-a-3-d-rotation-using-key-frames"></a><span data-ttu-id="7d197-102">Postupy: Animace trojrozměrného otočení použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="7d197-102">How to: Animate a 3-D Rotation Using Key Frames</span></span>
<span data-ttu-id="7d197-103">V následujícím příkladu <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> se používá k zajištění 3D objektu otočit při jeho osou otáčení animuje, výsledkem je "Němý".</span><span class="sxs-lookup"><span data-stu-id="7d197-103">In the following example, <xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames> is used to make a 3D object rotate while its axis of rotation animates resulting in a "wobble".</span></span> <span data-ttu-id="7d197-104">Tato animace používá následující klíčové snímky:</span><span class="sxs-lookup"><span data-stu-id="7d197-104">This animation uses the following key frames:</span></span>  
  
1.  <span data-ttu-id="7d197-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame>slouží k vytvoření smooth, lineární interpolace mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="7d197-105"><xref:System.Windows.Media.Animation.LinearRotation3DKeyFrame> is used to create a smooth, linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="7d197-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame>slouží k vytvoření nečekané "přechodů" mezi hodnotami (žádné interpolace).</span><span class="sxs-lookup"><span data-stu-id="7d197-106"><xref:System.Windows.Media.Animation.DiscreteRotation3DKeyFrame> is used to create sudden "jumps" between values (no interpolation).</span></span>  
  
3.  <span data-ttu-id="7d197-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame>slouží k vytvoření proměnné přechod mezi hodnotami v závislosti na tom <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7d197-107"><xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame> is used to create a variable transition between values depending on the <xref:System.Windows.Media.Animation.SplineRotation3DKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="7d197-108">Tuto část animace v následujícím příkladu spustí vypnout pomalé, ale na konec časového úseku, urychluje exponenciálně.</span><span class="sxs-lookup"><span data-stu-id="7d197-108">In the example below, this part of the animation starts off slow but toward the end of the time segment, speeds up exponentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d197-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d197-109">Example</span></span>  
 [!code-xaml[Animation3DGallery_snip#Rotation3DAnimationUsingKeyFramesExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Rotation3DAnimationUsingKeyFramesExample.xaml#rotation3danimationusingkeyframesexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="7d197-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d197-110">See Also</span></span>  
 [<span data-ttu-id="7d197-111">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="7d197-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="7d197-112">Přehled animací jednotlivých klíč</span><span class="sxs-lookup"><span data-stu-id="7d197-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="7d197-113">Animace 3D otočení pomocí scénářů</span><span class="sxs-lookup"><span data-stu-id="7d197-113">Animate a 3-D Rotation Using Storyboards</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-storyboards.md)  
 [<span data-ttu-id="7d197-114">Animace 3D otočení pomocí Rotation3DAnimation</span><span class="sxs-lookup"><span data-stu-id="7d197-114">Animate a 3-D Rotation Using Rotation3DAnimation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-rotation3danimation.md)  
 [<span data-ttu-id="7d197-115">Animace 3D otočení pomocí Quaternions</span><span class="sxs-lookup"><span data-stu-id="7d197-115">Animate a 3-D Rotation Using Quaternions</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-3-d-rotation-using-quaternions.md)  
 [<span data-ttu-id="7d197-116">Animace 3D otočení pomocí klíčových snímků (QuaternionAnimationUsingKeyFrames)</span><span class="sxs-lookup"><span data-stu-id="7d197-116">Animate a 3-D Rotation Using Key Frames (QuaternionAnimationUsingKeyFrames)</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animate-a-3-d-rotation-quaternionanimationusingkeyframes.md)
