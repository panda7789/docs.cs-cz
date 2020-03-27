---
title: 'Postupy: Animace tloušťky ohraničení použitím klíčových snímků'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], border thickness with key frames
- key frames [WPF], animating border thickness with
- border thickness [WPF], animating with key frames
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
ms.openlocfilehash: 884b62e88c347449ae39caa9c028d09db39b9f4b
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344696"
---
# <a name="how-to-animate-the-thickness-of-a-border-by-using-key-frames"></a><span data-ttu-id="07822-102">Postupy: Animace tloušťky ohraničení použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="07822-102">How to: Animate the Thickness of a Border by Using Key Frames</span></span>
<span data-ttu-id="07822-103">Tento příklad ukazuje, jak <xref:System.Windows.Controls.Control.BorderThickness%2A> animovat vlastnost <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="07822-103">This example shows how to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="07822-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="07822-104">Example</span></span>  
 <span data-ttu-id="07822-105">Následující příklad používá <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> třídu k <xref:System.Windows.Controls.Control.BorderThickness%2A> animaci vlastnosti <xref:System.Windows.Controls.Border>.</span><span class="sxs-lookup"><span data-stu-id="07822-105">The following example uses the <xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Controls.Control.BorderThickness%2A> property of a <xref:System.Windows.Controls.Border>.</span></span> <span data-ttu-id="07822-106">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="07822-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="07822-107">Během první poloviny sekundy používá <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> instanci třídy postupně zvyšovat tloušťku ohraničení.</span><span class="sxs-lookup"><span data-stu-id="07822-107">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> class to gradually increase the thickness of the border.</span></span> <span data-ttu-id="07822-108">Příklad používá <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> k vytvoření hladkého lineárního zvýšení mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="07822-108">The example uses <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> to create a smooth linear increase between values.</span></span>  
  
2. <span data-ttu-id="07822-109">Na konci další poloviny sekundy, používá <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> instance třídy náhle zvýšit tloušťku ohraničení.</span><span class="sxs-lookup"><span data-stu-id="07822-109">At the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> class to suddenly increase the thickness of the border.</span></span> <span data-ttu-id="07822-110">Diskrétní klíčové snímky, jako jsou <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> ty, které jsou odvozeny z vytvoření náhlé skoky mezi hodnotami, to znamená, že pohyb animace je trhané.</span><span class="sxs-lookup"><span data-stu-id="07822-110">Discrete key frames like those derived from <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> create sudden jumps between values, that is, the movement of the animation is jerky.</span></span>  
  
3. <span data-ttu-id="07822-111">Během posledních dvou sekund, používá <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> instance třídy ke snížení tloušťky ohraničení.</span><span class="sxs-lookup"><span data-stu-id="07822-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> class to decrease the thickness of the border.</span></span> <span data-ttu-id="07822-112">Klíčové snímky spline, jako <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> jsou ty, které jsou odvozeny <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> z vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="07822-112">Spline key frames like those derived from <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="07822-113">V tomto klíčovém snímku animace začíná pomalu a exponenciálně urychluje ke konci časového segmentu.</span><span class="sxs-lookup"><span data-stu-id="07822-113">In this key frame, the animation starts off slow and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-xaml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="07822-114">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="07822-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07822-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="07822-115">See also</span></span>

- <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>
- <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>
- [<span data-ttu-id="07822-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="07822-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="07822-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="07822-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
- [<span data-ttu-id="07822-118">Animace hodnoty BorderThickness</span><span class="sxs-lookup"><span data-stu-id="07822-118">Animate a BorderThickness Value</span></span>](../controls/how-to-animate-a-borderthickness-value.md)
