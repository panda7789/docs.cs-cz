---
title: 'Postupy: Animace barev použitím klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 8a444706f7541b52722ab8257a88e76c3e1b0938
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/27/2020
ms.locfileid: "80344753"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="047e9-102">Postupy: Animace barev použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="047e9-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="047e9-103">Tento příklad ukazuje, jak <xref:System.Windows.Media.SolidColorBrush.Color%2A> animovat of a <xref:System.Windows.Media.SolidColorBrush> pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="047e9-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="047e9-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="047e9-104">Example</span></span>  
 <span data-ttu-id="047e9-105">Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> třídu k <xref:System.Windows.Media.SolidColorBrush.Color%2A> animaci vlastnosti <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="047e9-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="047e9-106">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="047e9-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="047e9-107">Během prvních dvou sekund používá instanci <xref:System.Windows.Media.Animation.LinearColorKeyFrame> třídy k postupné změně barvy ze zelené na červenou.</span><span class="sxs-lookup"><span data-stu-id="047e9-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="047e9-108">Lineární klíčové <xref:System.Windows.Media.Animation.LinearColorKeyFrame> snímky, jako je vytvoření hladkého lineárního přechodu mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="047e9-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="047e9-109">Na konci další půlsekundy použije instanci <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> třídy k rychlé změně barvy z červené na žlutou.</span><span class="sxs-lookup"><span data-stu-id="047e9-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="047e9-110">Diskrétní klíčové snímky, <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> jako je vytvoření náhlých změn mezi hodnotami, to znamená, že změna barvy v této části animace nastává rychle a není jemná.</span><span class="sxs-lookup"><span data-stu-id="047e9-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="047e9-111">Během posledních dvou sekund použije instanci <xref:System.Windows.Media.Animation.SplineColorKeyFrame> třídy ke změně barvy znovu – tentokrát ze žluté zpět na zelenou.</span><span class="sxs-lookup"><span data-stu-id="047e9-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="047e9-112">Klíčové snímky spline, jako je <xref:System.Windows.Media.Animation.SplineColorKeyFrame> vytvoření proměnné přechodu mezi hodnotami podle hodnot vlastnosti. <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A></span><span class="sxs-lookup"><span data-stu-id="047e9-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="047e9-113">V tomto příkladu změna barvy začíná pomalu a exponenciálně urychluje ke konci časového segmentu.</span><span class="sxs-lookup"><span data-stu-id="047e9-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="047e9-114">Kompletní ukázku naleznete v tématu [Ukázka animace klíčových snímků](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span><span class="sxs-lookup"><span data-stu-id="047e9-114">For the complete sample, see [KeyFrame Animation Sample](https://github.com/microsoft/WPF-Samples/tree/master/Animation/KeyFrameAnimation).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="047e9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="047e9-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="047e9-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="047e9-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="047e9-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="047e9-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
