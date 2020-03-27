---
title: 'Postupy: Animace bodu použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: edcba36644cf78d6e98f934d9bd8b593af38b328
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344884"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="57240-102">Postupy: Animace bodu použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="57240-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="57240-103">Tento příklad ukazuje, <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> jak použít třídu k animaci <xref:System.Windows.Point>.</span><span class="sxs-lookup"><span data-stu-id="57240-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="57240-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="57240-104">Example</span></span>  
 <span data-ttu-id="57240-105">Následující příklad přesune elipsu podél trojúhelníkové cesty.</span><span class="sxs-lookup"><span data-stu-id="57240-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="57240-106">Příklad používá <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.EllipseGeometry.Center%2A> animaci <xref:System.Windows.Media.EllipseGeometry>vlastnosti .</span><span class="sxs-lookup"><span data-stu-id="57240-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="57240-107">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="57240-107">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="57240-108">Během první poloviny sekundy používá <xref:System.Windows.Media.Animation.LinearPointKeyFrame> instanci třídy k přesunutí elipsy podél cesty stabilní rychlostí z počáteční pozice.</span><span class="sxs-lookup"><span data-stu-id="57240-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="57240-109">Lineární klíčové <xref:System.Windows.Media.Animation.LinearPointKeyFrame> snímky, jako je vytvoření hladké lineární interpolace mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="57240-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2. <span data-ttu-id="57240-110">Na konci další půlsekundy použije instanci <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> třídy k náhlému přesunutí elipsy podél cesty na další pozici.</span><span class="sxs-lookup"><span data-stu-id="57240-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="57240-111">Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> jako je vytvoření náhlých skoků mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="57240-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3. <span data-ttu-id="57240-112">Během posledních dvou sekund, používá <xref:System.Windows.Media.Animation.SplinePointKeyFrame> instance třídy přesunout elipsu zpět do výchozí polohy.</span><span class="sxs-lookup"><span data-stu-id="57240-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="57240-113">Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplinePointKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A></span><span class="sxs-lookup"><span data-stu-id="57240-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="57240-114">V tomto příkladu animace začíná pomalu a zrychluje exponenciálně ke konci časového segmentu.</span><span class="sxs-lookup"><span data-stu-id="57240-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="57240-115">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="57240-115">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
 <span data-ttu-id="57240-116">Pro konzistenci s jinými příklady animace, verze <xref:System.Windows.Media.Animation.Storyboard> kódu v <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>tomto příkladu použít objekt použít .</span><span class="sxs-lookup"><span data-stu-id="57240-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="57240-117">Však při použití jedné animace v kódu, je <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> jednodušší použít <xref:System.Windows.Media.Animation.Storyboard>metodu namísto použití .</span><span class="sxs-lookup"><span data-stu-id="57240-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="57240-118">Například viz [Animate vlastnost bez použití storyboardu](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="57240-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57240-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="57240-119">See also</span></span>

- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="57240-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="57240-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="57240-121">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="57240-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
