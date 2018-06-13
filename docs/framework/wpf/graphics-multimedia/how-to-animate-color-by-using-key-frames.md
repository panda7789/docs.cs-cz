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
ms.openlocfilehash: 7d89a1f9c24c93bd6b05265092bde09e8cf6eff5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560329"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="7bf46-102">Postupy: Animace barev použitím klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="7bf46-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="7bf46-103">Tento příklad ukazuje, jak animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> pomocí klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="7bf46-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bf46-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7bf46-104">Example</span></span>  
 <span data-ttu-id="7bf46-105">Následující příklad používá <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> třídy animace <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="7bf46-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="7bf46-106">Tato animace používá tři klíčových snímků následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7bf46-106">This animation uses three key frames in the following manner:</span></span>  
  
1.  <span data-ttu-id="7bf46-107">Při první dvě sekundy používá instanci <xref:System.Windows.Media.Animation.LinearColorKeyFrame> třídy postupně změnit barvu ze zelené na červený.</span><span class="sxs-lookup"><span data-stu-id="7bf46-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="7bf46-108">Lineární klíčových snímků jako <xref:System.Windows.Media.Animation.LinearColorKeyFrame> vytvořit hladký lineární přechod mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="7bf46-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2.  <span data-ttu-id="7bf46-109">Během konec další půl sekundy používá instanci <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> třídy rychle změnit barvu red na žlutě.</span><span class="sxs-lookup"><span data-stu-id="7bf46-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="7bf46-110">Diskrétní klíčových snímků jako <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> vytvořit nečekané změn mezi hodnotami, který je, změna barvy v této části animace probíhá rychle a není jemně.</span><span class="sxs-lookup"><span data-stu-id="7bf46-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3.  <span data-ttu-id="7bf46-111">Během poslední dvou sekund, používá instanci <xref:System.Windows.Media.Animation.SplineColorKeyFrame> třída znovu Změna barvy – tentokrát z žlutý zpět na zelenou.</span><span class="sxs-lookup"><span data-stu-id="7bf46-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="7bf46-112">Křivkový klíčových snímků jako <xref:System.Windows.Media.Animation.SplineColorKeyFrame> vytvoření proměnné přechod mezi hodnotami podle hodnot <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7bf46-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="7bf46-113">V tomto příkladu změnu v hodnotě barva začne pomalu a urychluje exponenciálnímu ke konci čas segmentu.</span><span class="sxs-lookup"><span data-stu-id="7bf46-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="7bf46-114">Kompletní příklad, najdete v části [@keyframe, které určuje animace ukázka](http://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="7bf46-114">For the complete sample, see [KeyFrame Animation Sample](http://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf46-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bf46-115">See Also</span></span>  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [<span data-ttu-id="7bf46-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="7bf46-116">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="7bf46-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="7bf46-117">Key-Frame How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
