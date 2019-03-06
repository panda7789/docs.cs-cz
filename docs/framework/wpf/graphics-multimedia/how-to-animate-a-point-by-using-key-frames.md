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
ms.openlocfilehash: 4eeb7aa271883e1c76d5cac77f49accbdff39aea
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357232"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a><span data-ttu-id="33b8c-102">Postupy: Animace bodu použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="33b8c-102">How to: Animate a Point by Using Key Frames</span></span>
<span data-ttu-id="33b8c-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Point>.</span><span class="sxs-lookup"><span data-stu-id="33b8c-103">This example shows how to use the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate a <xref:System.Windows.Point>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33b8c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="33b8c-104">Example</span></span>  
 <span data-ttu-id="33b8c-105">V následujícím příkladu se přesune elipsa trojúhelníkové cestě.</span><span class="sxs-lookup"><span data-stu-id="33b8c-105">The following example moves an ellipse along a triangular path.</span></span> <span data-ttu-id="33b8c-106">V příkladu se používá <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.EllipseGeometry.Center%2A> vlastnost <xref:System.Windows.Media.EllipseGeometry>.</span><span class="sxs-lookup"><span data-stu-id="33b8c-106">The example uses the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.EllipseGeometry.Center%2A> property of an <xref:System.Windows.Media.EllipseGeometry>.</span></span> <span data-ttu-id="33b8c-107">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="33b8c-107">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="33b8c-108">Během prvního půl sekundy, používá instanci <xref:System.Windows.Media.Animation.LinearPointKeyFrame> třídy pro přesun na tři tečky podél cesty stabilní rychlostí z jeho výchozí pozice.</span><span class="sxs-lookup"><span data-stu-id="33b8c-108">During the first half second, uses an instance of the <xref:System.Windows.Media.Animation.LinearPointKeyFrame> class to move the ellipse along a path at a steady rate from its starting position.</span></span> <span data-ttu-id="33b8c-109">Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearPointKeyFrame> Vytvoření hladkého lineární interpolaci mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="33b8c-109">Linear key frames like <xref:System.Windows.Media.Animation.LinearPointKeyFrame> create a smooth linear interpolation between values.</span></span>  
  
2.  <span data-ttu-id="33b8c-110">Při ukončení na další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> třídy náhle přesunout na tři tečky na cestě na další pozici.</span><span class="sxs-lookup"><span data-stu-id="33b8c-110">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> class to suddenly move the ellipse along the path to the next position.</span></span> <span data-ttu-id="33b8c-111">Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> vytvořit i s náhlými rozdíly mezi jednotlivými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="33b8c-111">Discrete key frames like <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> create sudden jumps between values.</span></span>  
  
3.  <span data-ttu-id="33b8c-112">Během poslední dvě sekundy, používá instanci <xref:System.Windows.Media.Animation.SplinePointKeyFrame> třídy pro přechod na tři tečky na počáteční pozici.</span><span class="sxs-lookup"><span data-stu-id="33b8c-112">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame> class to move the ellipse back to its starting position.</span></span> <span data-ttu-id="33b8c-113">Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplinePointKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="33b8c-113">Spline key frames like <xref:System.Windows.Media.Animation.SplinePointKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="33b8c-114">V tomto příkladu animace začne pomalu a zrychluje exponenciálně na konci časového úseku.</span><span class="sxs-lookup"><span data-stu-id="33b8c-114">In this example, the animation begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="33b8c-115">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="33b8c-115">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
 <span data-ttu-id="33b8c-116">Pro zajištění konzistence s další příklady animace, kód verze tohoto příkladu použijte <xref:System.Windows.Media.Animation.Storyboard> objektu, který chcete použít <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="33b8c-116">For consistency with other animation examples, the code versions of this example use a <xref:System.Windows.Media.Animation.Storyboard> object to apply the <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>.</span></span> <span data-ttu-id="33b8c-117">Při použití jedné animace v kódu, je ale jednodušší použít <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda namísto použití <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="33b8c-117">However, when applying a single animation in code, it's simpler to use the <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> method instead of using a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="33b8c-118">Příklad najdete v tématu [animace vlastnosti bez pomoci scénáře](how-to-animate-a-property-without-using-a-storyboard.md).</span><span class="sxs-lookup"><span data-stu-id="33b8c-118">For an example, see [Animate a Property Without Using a Storyboard](how-to-animate-a-property-without-using-a-storyboard.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33b8c-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="33b8c-119">See also</span></span>
- <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>
- <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>
- <xref:System.Windows.Media.EllipseGeometry>
- [<span data-ttu-id="33b8c-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="33b8c-120">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="33b8c-121">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="33b8c-121">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
