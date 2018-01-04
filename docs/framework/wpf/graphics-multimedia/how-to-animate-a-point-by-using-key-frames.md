---
title: "Postupy: Animace bodu použitím klíčových snímků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c115d31c6ace26f8fd9dd6cff3fdeead89eea33
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="f5adf-102">Postupy: Animace bodu použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="f5adf-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="f5adf-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Point>.</span><span class="sxs-lookup"><span data-stu-id="f5adf-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5adf-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5adf-104">Example</span></span>  
 <span data-ttu-id="f5adf-105">Následující příklad přesune elipsy podél trojúhelníkovou cesty.</span><span class="sxs-lookup"><span data-stu-id="f5adf-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="f5adf-106">V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="f5adf-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="f5adf-107">Tato animace používá tři klíčových snímků následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f5adf-107">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="f5adf-108">Při první půl sekundy používá instanci <xref:System.Windows.Media.Animation.LinearPointKeyFrame> třídy pro přesun se třemi tečkami podél cesty konstantní rychlostí od počáteční pozice.</span><span class="sxs-lookup"><span data-stu-id="f5adf-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="f5adf-109">Lineární klíčových snímků jako <xref:System.Windows.Media.Animation.LinearPointKeyFrame> vytvořit smooth lineární interpolace mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="f5adf-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="f5adf-110">Během konec další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> třídy najednou přesuňte se třemi tečkami v cestě pro další.</span><span class="sxs-lookup"><span data-stu-id="f5adf-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="f5adf-111">Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> vytvoření nečekané přechodů mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="f5adf-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3.  <span data-ttu-id="f5adf-112">Během poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplinePointKeyFrame> třída k přesunutí se třemi tečkami zpátky na jeho počáteční pozice.</span><span class="sxs-lookup"><span data-stu-id="f5adf-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="f5adf-113">Křivkový klíčových snímků jako <xref:System.Windows.Media.Animation.SplinePointKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f5adf-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="f5adf-114">V tomto příkladu animace začne pomalu a urychluje exponenciálnímu ke konci čas segmentu.</span><span class="sxs-lookup"><span data-stu-id="f5adf-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="f5adf-115">Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="f5adf-115">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="f5adf-116">Z důvodu konzistence s další příklady animace verze kódu v tomto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objekt, který chcete použít <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="f5adf-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="f5adf-117">Při použití jedné animace v kódu, je však jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda místo použití <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="f5adf-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="f5adf-118">Příklad, naleznete v části [animace vlastnosti bez použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="f5adf-118">For an example, see [Animate a Property Without Using a Storyboard](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5adf-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5adf-119">See Also</span></span>  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [<span data-ttu-id="f5adf-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="f5adf-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="f5adf-121">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="f5adf-121">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
