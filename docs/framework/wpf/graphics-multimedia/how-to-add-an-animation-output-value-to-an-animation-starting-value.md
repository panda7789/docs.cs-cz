---
title: 'Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF]
ms.assetid: b89a82be-b03d-481e-a8d3-cc513d09ca00
ms.openlocfilehash: 945675d03a280e2394fdb0eab27c0978dc7cc320
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59102606"
---
# <a name="how-to-add-an-animation-output-value-to-an-animation-starting-value"></a><span data-ttu-id="87f3e-102">Postupy: Přidání výstupní hodnoty animace do počáteční hodnoty animace</span><span class="sxs-lookup"><span data-stu-id="87f3e-102">How to: Add an Animation Output Value to an Animation Starting Value</span></span>
<span data-ttu-id="87f3e-103">Tento příklad ukazuje, jak přidat výstupní hodnoty animace do počáteční hodnoty animace.</span><span class="sxs-lookup"><span data-stu-id="87f3e-103">This example shows how to add an animation output value to an animation starting value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87f3e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="87f3e-104">Example</span></span>  
 <span data-ttu-id="87f3e-105"><xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> Vlastnost určuje, jestli se chcete o výstupní hodnoty animace do počáteční hodnoty (základní hodnoty) animované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="87f3e-105">The <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property specifies whether you want the output value of an animation added to the starting value (base value) of an animated property.</span></span> <span data-ttu-id="87f3e-106">Můžete použít <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> vlastnost nejzákladnější animace a většina klíčový snímek animace.</span><span class="sxs-lookup"><span data-stu-id="87f3e-106">You can use the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A> property with most basic animations and most key frame animations.</span></span> <span data-ttu-id="87f3e-107">Další informace najdete v tématu [přehled animace](animation-overview.md) a [přehled animací klíčových snímků](key-frame-animations-overview.md).</span><span class="sxs-lookup"><span data-stu-id="87f3e-107">For more information, see [Animation Overview](animation-overview.md) and [Key-Frame Animations Overview](key-frame-animations-overview.md).</span></span>  
  
 <span data-ttu-id="87f3e-108">Následující příklad ukazuje účinek pomocí <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimation> a použití <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> vlastnost s <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span><span class="sxs-lookup"><span data-stu-id="87f3e-108">The following example shows the effect of using the <xref:System.Windows.Media.Animation.DoubleAnimation.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimation> and using the <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.IsAdditive%2A?displayProperty=nameWithType> property with <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#IsAdditiveWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/IsAdditiveExample.xaml#isadditivewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="87f3e-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="87f3e-109">See also</span></span>

- [<span data-ttu-id="87f3e-110">Kumulování hodnot animace při opakujících se cyklech</span><span class="sxs-lookup"><span data-stu-id="87f3e-110">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="87f3e-111">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="87f3e-111">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="87f3e-112">Přehled animací klíčových snímků</span><span class="sxs-lookup"><span data-stu-id="87f3e-112">Key-Frame Animations Overview</span></span>](key-frame-animations-overview.md)
- [<span data-ttu-id="87f3e-113">Postupy: Témata animace a časování</span><span class="sxs-lookup"><span data-stu-id="87f3e-113">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
