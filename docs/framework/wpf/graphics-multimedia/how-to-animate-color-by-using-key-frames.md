---
title: 'Postupy: Animace barev pomocí klíčových snímků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: e579c4beb757ccf58eb1b9ca1f3852a5b96cac1a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59326083"
---
# <a name="how-to-animate-color-by-using-key-frames"></a><span data-ttu-id="c342a-102">Postupy: Animace barev pomocí klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="c342a-102">How to: Animate Color by Using Key Frames</span></span>
<span data-ttu-id="c342a-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> použitím klíčových snímků.</span><span class="sxs-lookup"><span data-stu-id="c342a-103">This example shows how to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a <xref:System.Windows.Media.SolidColorBrush> by using key frames.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c342a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c342a-104">Example</span></span>  
 <span data-ttu-id="c342a-105">V následujícím příkladu <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> třídy pro animaci <xref:System.Windows.Media.SolidColorBrush.Color%2A> vlastnost <xref:System.Windows.Media.SolidColorBrush>.</span><span class="sxs-lookup"><span data-stu-id="c342a-105">The following example uses the <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> class to animate the <xref:System.Windows.Media.SolidColorBrush.Color%2A> property of a <xref:System.Windows.Media.SolidColorBrush>.</span></span> <span data-ttu-id="c342a-106">Tato animace používá tři klíčové snímky následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="c342a-106">This animation uses three key frames in the following manner:</span></span>  
  
1. <span data-ttu-id="c342a-107">Během prvních dvou sekund používá instanci <xref:System.Windows.Media.Animation.LinearColorKeyFrame> třídy postupně od zelené Změna barvy na červenou.</span><span class="sxs-lookup"><span data-stu-id="c342a-107">During the first two seconds, uses an instance of the <xref:System.Windows.Media.Animation.LinearColorKeyFrame> class to gradually change the color from green to red.</span></span> <span data-ttu-id="c342a-108">Lineární klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.LinearColorKeyFrame> Vytvoření hladkého lineárního přechodu mezi hodnotami.</span><span class="sxs-lookup"><span data-stu-id="c342a-108">Linear key frames like <xref:System.Windows.Media.Animation.LinearColorKeyFrame> create a smooth linear transition between values.</span></span>  
  
2. <span data-ttu-id="c342a-109">Při ukončení na další půl sekundy, používá instanci <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> třídy rychle změnit barvu z červené na žlutou.</span><span class="sxs-lookup"><span data-stu-id="c342a-109">During the end of the next half second, uses an instance of the <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> class to quickly change the color from red to yellow.</span></span> <span data-ttu-id="c342a-110">Diskrétní klíčových snímků, jako jsou <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> vytvořit náhlých změn mezi hodnotami, to znamená, změna barvy v této části animace dojde k rychlému a není jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="c342a-110">Discrete key frames like <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> create sudden changes between values, that is, the color change in this part of the animation occurs quickly and is not subtle.</span></span>  
  
3. <span data-ttu-id="c342a-111">Během poslední dvě sekundy, používá instanci <xref:System.Windows.Media.Animation.SplineColorKeyFrame> třídy a změňte barvu znovu, tentokrát z žlutý zpět na zelenou.</span><span class="sxs-lookup"><span data-stu-id="c342a-111">During the final two seconds, uses an instance of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame> class to change the color again—this time from yellow back to green.</span></span> <span data-ttu-id="c342a-112">Klíčové snímky SpLine, jako jsou <xref:System.Windows.Media.Animation.SplineColorKeyFrame> vytvoříte proměnné přechod mezi hodnotami podle hodnoty <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c342a-112">Spline key frames like <xref:System.Windows.Media.Animation.SplineColorKeyFrame> create a variable transition between values according to the values of the <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> property.</span></span> <span data-ttu-id="c342a-113">V tomto příkladu změní barva začne pomalu a zrychluje exponenciálně na konci časového úseku.</span><span class="sxs-lookup"><span data-stu-id="c342a-113">In this example, the change in color begins slowly and speeds up exponentially toward the end of the time segment.</span></span>  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 <span data-ttu-id="c342a-114">Úplnou ukázku najdete v tématu [klíčový snímek animace ukázka](https://go.microsoft.com/fwlink/?LinkID=160012).</span><span class="sxs-lookup"><span data-stu-id="c342a-114">For the complete sample, see [KeyFrame Animation Sample](https://go.microsoft.com/fwlink/?LinkID=160012).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c342a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c342a-115">See also</span></span>

- <xref:System.Windows.Media.SolidColorBrush.Color%2A>
- <xref:System.Windows.Media.SolidColorBrush>
- <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>
- [<span data-ttu-id="c342a-116">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="c342a-116">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="c342a-117">Témata s postupy ke klíčovým snímkům</span><span class="sxs-lookup"><span data-stu-id="c342a-117">Key-Frame How-to Topics</span></span>](key-frame-animation-how-to-topics.md)
