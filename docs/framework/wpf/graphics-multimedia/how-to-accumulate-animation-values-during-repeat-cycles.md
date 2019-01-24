---
title: 'Postupy: Kumulování hodnot animace při opakujících se cyklech'
ms.date: 03/30/2017
helpviewer_keywords:
- accumulating animation values across repeating cycles [WPF]
- animation [WPF], accumulating values across repeating cycles
ms.assetid: 548df369-c7cc-4dab-b569-08b95ced2e7e
ms.openlocfilehash: 6e98b7eefd0c30e728b60926096c0f082bc079ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587278"
---
# <a name="how-to-accumulate-animation-values-during-repeat-cycles"></a><span data-ttu-id="b7b17-102">Postupy: Kumulování hodnot animace při opakujících se cyklech</span><span class="sxs-lookup"><span data-stu-id="b7b17-102">How to: Accumulate Animation Values During Repeat Cycles</span></span>
<span data-ttu-id="b7b17-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost kumulování hodnot animace přes opakující se cykly.</span><span class="sxs-lookup"><span data-stu-id="b7b17-103">This example shows how to use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate animation values across repeating cycles.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b7b17-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="b7b17-104">Example</span></span>  
 <span data-ttu-id="b7b17-105">Použití <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost kumulování základních hodnot animace přes opakující se cykly.</span><span class="sxs-lookup"><span data-stu-id="b7b17-105">Use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to accumulate base values of an animation across repeating cycles.</span></span> <span data-ttu-id="b7b17-106">Například pokud nastavíte animace opakování 9 časy (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9 x") a nastavte vlastnost animovat 10 až 15 (z = 10 k = 15), vlastnost animuje z 10 až 15 během první cyklu z 15 až 20 během druhé cyklu , od 20 do 25 během cyklu třetí a tak dále.</span><span class="sxs-lookup"><span data-stu-id="b7b17-106">For example, if you set an animation to repeat 9 times (<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> = "9x") and you set the property to animate between 10 and 15 (From = 10 To = 15), the property animates from 10 to 15 during the first cycle, from 15 to 20 during the second cycle, from 20 to 25 during the third cycle, and so on.</span></span> <span data-ttu-id="b7b17-107">Každý cyklus animace proto používá koncovou hodnotu animace od předchozího cyklu animace jako jeho základní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="b7b17-107">Hence, each animation cycle uses the ending animation value from the previous animation cycle as its base value.</span></span>  
  
 <span data-ttu-id="b7b17-108">Můžete použít `IsCumulative` vlastnost nejzákladnější animace a většina klíčový snímek animace.</span><span class="sxs-lookup"><span data-stu-id="b7b17-108">You can use the `IsCumulative` property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="b7b17-109">Další informace najdete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="b7b17-109">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="b7b17-110">Následující příklad ukazuje toto chování animace šířka čtyři obdélníků.</span><span class="sxs-lookup"><span data-stu-id="b7b17-110">The following example shows this behavior by animating the width of four rectangles.</span></span> <span data-ttu-id="b7b17-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="b7b17-111">The example:</span></span>  
  
-   <span data-ttu-id="b7b17-112">Animuje první obdélníku s <xref:System.Windows.Media.Animation.DoubleAnimation> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="b7b17-112">Animates the first rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="b7b17-113">Animuje druhý obdélníku s <xref:System.Windows.Media.Animation.DoubleAnimation> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> vlastnost na výchozí hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="b7b17-113">Animates the second rectangle with <xref:System.Windows.Media.Animation.DoubleAnimation> and sets the <xref:System.Windows.Media.Animation.DoubleAnimation.IsCumulative%2A> property to the default value of `false`.</span></span>  
  
-   <span data-ttu-id="b7b17-114">Animuje třetí obdélníku s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="b7b17-114">Animates the third rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `true`.</span></span>  
  
-   <span data-ttu-id="b7b17-115">Animuje poslední obdélníku s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> a nastaví <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="b7b17-115">Animates the last rectangle with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> and sets the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsCumulative%2A> property to `false`.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsCumulativeWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsCumulativeExample.xaml#iscumulativewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="b7b17-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b7b17-116">See also</span></span>
- [<span data-ttu-id="b7b17-117">Přidání výstupní hodnoty animace do počáteční hodnoty animace</span><span class="sxs-lookup"><span data-stu-id="b7b17-117">Add an Animation Output Value to an Animation Starting Value</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-add-an-animation-output-value-to-an-animation-starting-value.md)
- [<span data-ttu-id="b7b17-118">Opakování animace</span><span class="sxs-lookup"><span data-stu-id="b7b17-118">Repeat an Animation</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)
- [<span data-ttu-id="b7b17-119">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="b7b17-119">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="b7b17-120">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="b7b17-120">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="b7b17-121">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="b7b17-121">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
