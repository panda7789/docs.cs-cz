---
title: 'Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 820e03064d331e852a224e1f989685d7a77983db
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54603024"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="6c2e7-102">Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace</span><span class="sxs-lookup"><span data-stu-id="6c2e7-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="6c2e7-103">Tento příklad ukazuje, jak přidat výstupní hodnoty animace do počáteční hodnoty animace.</span><span class="sxs-lookup"><span data-stu-id="6c2e7-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c2e7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c2e7-104">Example</span></span>  
 <span data-ttu-id="6c2e7-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Vlastnost určuje, jestli se chcete o výstupní hodnoty animace do počáteční hodnoty (základní hodnoty) animované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6c2e7-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="6c2e7-106">Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> vlastnost nejzákladnější animace a většina klíčový snímek animace.</span><span class="sxs-lookup"><span data-stu-id="6c2e7-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="6c2e7-107">Další informace najdete v tématu [přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) a [přehled animací klíčových snímků](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6c2e7-107">For more information, see [Animation Overview](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md) and [Key-Frame Animations Overview](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="6c2e7-108">Následující příklad ukazuje účinek pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimation> a použití <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="6c2e7-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="6c2e7-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6c2e7-109">See also</span></span>
- [<span data-ttu-id="6c2e7-110">Kumulování hodnot animace při opakujících se cyklech</span><span class="sxs-lookup"><span data-stu-id="6c2e7-110">Accumulate Animation Values During Repeat Cycles</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="6c2e7-111">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="6c2e7-111">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="6c2e7-112">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="6c2e7-112">Key-Frame Animations Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)
- [<span data-ttu-id="6c2e7-113">Animace a časování</span><span class="sxs-lookup"><span data-stu-id="6c2e7-113">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="6c2e7-114">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="6c2e7-114">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
