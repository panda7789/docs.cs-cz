---
title: 'Postupy: Animace dvojice použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Doubles [WPF], animating with key frames
- animation [WPF], Doubles with key frames
- key frames [WPF], animating Doubles with
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
ms.openlocfilehash: 9eab794cc8411230226cddc97beaa13c1bdd9405
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344942"
---
# <a name="how-to-animate-a-double-by-using-key-frames"></a><span data-ttu-id="ea7fe-102">Postupy: Animace dvojice použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="ea7fe-102">How to: Animate a Double by Using Key Frames</span></span>
<span data-ttu-id="ea7fe-103">Tento příklad ukazuje, jak animovat hodnotu <xref:System.Double> vlastnosti, která trvá pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-103">This example shows how to animate the value of a property that takes a <xref:System.Double> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea7fe-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea7fe-104">Example</span></span>  
 <span data-ttu-id="ea7fe-105">Následující příklad přesune obdélník přes obrazovku.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-105">The following example moves a rectangle across a screen.</span></span> <span data-ttu-id="ea7fe-106">Příklad používá <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.TranslateTransform.X%2A> animaci <xref:System.Windows.Media.TranslateTransform> vlastnosti <xref:System.Windows.Shapes.Rectangle>aplikované na .</span><span class="sxs-lookup"><span data-stu-id="ea7fe-106">The example uses the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.TranslateTransform.X%2A> property of a <xref:System.Windows.Media.TranslateTransform> applied to a <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="ea7fe-107">Tato animace, která se opakuje neomezeně dlouho, používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="ea7fe-107">This animation, which repeats indefinitely, uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="ea7fe-108">Během prvních tří sekund používá instanci <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> třídy k přesunutí obdélníku podél cesty stabilní rychlostí od počáteční polohy do polohy 500.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-108">During the first three seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> class to move the rectangle along a path at a steady rate from its starting position to the 500 position.</span></span> <span data-ttu-id="ea7fe-109">Lineární klíčové <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> snímky, jako je vytvoření hladkého lineárního přechodu mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="ea7fe-110">Na konci čtvrté sekundy, používá instance <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> třídy náhle přesunout obdélník na další pozici.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-110">At the end of the fourth second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> class to suddenly move the rectangle to the next position.</span></span> <span data-ttu-id="ea7fe-111">Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> create sudden jumps between values.</span></span> <span data-ttu-id="ea7fe-112">V tomto příkladu obdélník je na výchozí pozici a pak se náhle objeví na pozici 500.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-112">In this example, the rectangle is at the starting position and then suddenly appears at the 500 position.</span></span>  
  
3. <span data-ttu-id="ea7fe-113">V posledních dvou sekundách používá <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> instanci třídy k přesunutí obdélníku zpět do výchozí polohy.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-113">In the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> class to move the rectangle back to its starting position.</span></span> <span data-ttu-id="ea7fe-114">Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnoty vlastnosti. <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A></span><span class="sxs-lookup"><span data-stu-id="ea7fe-114">Spline key frames like <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> create a variable transition between values according to the value of the <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="ea7fe-115">V tomto příkladu obdélník začíná pohybem pomalu a pak urychluje exponenciálně ke konci časového segmentu.</span><span class="sxs-lookup"><span data-stu-id="ea7fe-115">In this example, the rectangle begins by moving slowly and then speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="ea7fe-116">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="ea7fe-116">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="ea7fe-117">Pro konzistenci s jinými příklady animace, verze <xref:System.Windows.Media.Animation.Storyboard> kódu v <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>tomto příkladu použít objekt použít .</span><span class="sxs-lookup"><span data-stu-id="ea7fe-117">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="ea7fe-118">Alternativně při použití jedné animace v kódu, je <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> jednodušší použít <xref:System.Windows.Media.Animation.Storyboard>metodu namísto použití .</span><span class="sxs-lookup"><span data-stu-id="ea7fe-118">Alternatively, when applying a single animation in code, it is simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="ea7fe-119">Například viz [Animate vlastnost bez použití storyboardu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="ea7fe-119">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea7fe-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="ea7fe-120">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>
- <xref:System.Windows.Shapes.Rectangle>
- <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>
- <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>
- [<span data-ttu-id="ea7fe-121">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="ea7fe-121">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="ea7fe-122">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="ea7fe-122">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
