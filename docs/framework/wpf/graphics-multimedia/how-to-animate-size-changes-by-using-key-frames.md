---
title: 'Postupy: Animace změn velikosti použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- key frames [WPF], animating size changes with
- animation [WPF], size changes with key frames
- size changes [WPF], animating with key frames
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
ms.openlocfilehash: 42cecfc9df4304be4033ea39edc0517016de4a92
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344637"
---
# <a name="how-to-animate-size-changes-by-using-key-frames"></a><span data-ttu-id="0091b-102">Postupy: Animace změn velikosti použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="0091b-102">How to: Animate Size Changes by Using Key Frames</span></span>
<span data-ttu-id="0091b-103">Tento příklad ukazuje, jak animovat změny velikosti pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="0091b-103">This example shows how to animate size changes by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0091b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0091b-104">Example</span></span>  
 <span data-ttu-id="0091b-105">Následující příklad používá <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.ArcSegment.Size%2A> animaci vlastnosti <xref:System.Windows.Media.ArcSegment>.</span><span class="sxs-lookup"><span data-stu-id="0091b-105">The following example uses the <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.ArcSegment.Size%2A> property of an <xref:System.Windows.Media.ArcSegment>.</span></span> <span data-ttu-id="0091b-106">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="0091b-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="0091b-107">Během první poloviny druhé animace používá instance <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> třídy postupně zvětšit velikost oblouku. Lineární klíčové <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> snímky, jako je vytvoření hladkého lineárního přechodu mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="0091b-107">During the first half second of the animation, uses an instance of the <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> class to gradually increase the size of the arc. Linear key frames like <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="0091b-108">Na konci další poloviny sekundy, používá <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> instance třídy náhle zvětšit velikost oblouku. Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami, to znamená, že změny velikosti nastávají náhle a nejsou jemné.</span><span class="sxs-lookup"><span data-stu-id="0091b-108">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> class to suddenly increase the size of the arc. Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> create sudden jumps between values, that is, the size changes occur suddenly and are not subtle.</span></span>  
  
3. <span data-ttu-id="0091b-109">Během posledních dvou sekund používá instanci třídy <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> ke zvětšení velikosti oblouku. Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A></span><span class="sxs-lookup"><span data-stu-id="0091b-109">Over the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> class to increase the size of the arc. Spline key frames like <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="0091b-110">V tomto příkladu se velikost oblouku nejprve zvětšuje pomalu a poté exponenciálně zvyšuje ke konci časového segmentu.</span><span class="sxs-lookup"><span data-stu-id="0091b-110">In this example, the size of the arc increases slowly at first and then increases exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="0091b-111">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="0091b-111">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0091b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="0091b-112">See also</span></span>

- <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>
- <xref:System.Windows.Media.ArcSegment.Size%2A>
- <xref:System.Windows.Media.ArcSegment>
- <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>
- <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>
- [<span data-ttu-id="0091b-113">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="0091b-113">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="0091b-114">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="0091b-114">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
