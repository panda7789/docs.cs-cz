---
title: 'Postupy: Kumulování hodnot animace při opakujících se cyklech'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 7b954a388549f1bc6f3fa6ec1bcb2df61cc4e045
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557664"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="a86ec-102">Postupy: Kumulování hodnot animace při opakujících se cyklech</span><span class="sxs-lookup"><span data-stu-id="a86ec-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="a86ec-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost hromadit hodnoty animace napříč opakovaných cyklů.</span><span class="sxs-lookup"><span data-stu-id="a86ec-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a86ec-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a86ec-104">Example</span></span>  
 <span data-ttu-id="a86ec-105">Použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost hromadit základní hodnoty animace napříč opakovaných cyklů.</span><span class="sxs-lookup"><span data-stu-id="a86ec-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="a86ec-106">Například pokud nastavíte animace opakování 9 časy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") a nastavte vlastnosti, která má animace 10 až 15 (z = 10 k = 15), vlastnost animuje od 10 do 15 první cyklu od 15 do 20 druhý cyklu , z 20 až 25 během třetí cyklu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="a86ec-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="a86ec-107">Proto každý cyklus animace používá koncovou hodnotu animace z předchozího cyklu animace jako svou základní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a86ec-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="a86ec-108">Můžete použít `IsCumulative` vlastnost nejzákladnější animace a většina klíčových snímků animace.</span><span class="sxs-lookup"><span data-stu-id="a86ec-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="a86ec-109">Další informace najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [klíč rámce animací přehled](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="a86ec-109">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="a86ec-110">Následující příklad ukazuje toto chování animace šířku čtyři obdélníky.</span><span class="sxs-lookup"><span data-stu-id="a86ec-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="a86ec-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="a86ec-111">The example:</span></span>  
  
-   <span data-ttu-id="a86ec-112">Animuje první rámeček s <xref:System.Windows.Media.Animation.DoubleAnimation> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="a86ec-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="a86ec-113">Animuje druhý rámeček s <xref:System.Windows.Media.Animation.DoubleAnimation> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost, která má výchozí hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="a86ec-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="a86ec-114">Animuje třetí rámeček s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="a86ec-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="a86ec-115">Animuje poslední rámeček s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="a86ec-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a86ec-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="a86ec-116">See Also</span></span>  
 [<span data-ttu-id="a86ec-117">Přidání výstupní hodnoty animace do počáteční hodnoty animace</span><span class="sxs-lookup"><span data-stu-id="a86ec-117">Add an Animation Output Value to an Animation Starting Value</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)  
 [<span data-ttu-id="a86ec-118">Opakování animace</span><span class="sxs-lookup"><span data-stu-id="a86ec-118">Repeat an Animation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)  
 [<span data-ttu-id="a86ec-119">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="a86ec-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="a86ec-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="a86ec-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [<span data-ttu-id="a86ec-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="a86ec-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
