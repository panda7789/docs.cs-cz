---
title: 'Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141170"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="e61b7-102">Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období</span><span class="sxs-lookup"><span data-stu-id="e61b7-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="e61b7-103">Tento příklad ukazuje, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> jak určit <xref:System.Windows.Media.Animation.Timeline> pro neaktivní animované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e61b7-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e61b7-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e61b7-104">Example</span></span>  
 <span data-ttu-id="e61b7-105">Vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> určuje, co se stane s hodnotou animované vlastnosti, když není animována, to znamená, když <xref:System.Windows.Media.Animation.Timeline> je neaktivní, ale jeho nadřazený <xref:System.Windows.Media.Animation.Timeline> je uvnitř jeho aktivní nebo pozdržet období.</span><span class="sxs-lookup"><span data-stu-id="e61b7-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="e61b7-106">Například zůstane animovaná vlastnost na své koncové hodnotě po ukončení animace nebo se vrátí zpět na hodnotu, kterou měla před zahájením animace?</span><span class="sxs-lookup"><span data-stu-id="e61b7-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="e61b7-107">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> k animaci <xref:System.Windows.FrameworkElement.Width%2A> dvou obdélníků.</span><span class="sxs-lookup"><span data-stu-id="e61b7-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="e61b7-108">Každý obdélník používá <xref:System.Windows.Media.Animation.Timeline> jiný objekt.</span><span class="sxs-lookup"><span data-stu-id="e61b7-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="e61b7-109">Jeden <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> má, který <xref:System.Windows.Media.Animation.FillBehavior.Stop>je nastaven na , což způsobí, že šířka obdélníku <xref:System.Windows.Media.Animation.Timeline> vrátit zpět do své neanimované hodnoty po skončení.</span><span class="sxs-lookup"><span data-stu-id="e61b7-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="e61b7-110">Druhý <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> a <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, což způsobí, že šířka <xref:System.Windows.Media.Animation.Timeline> zůstane na jeho koncové hodnotě při ukončení.</span><span class="sxs-lookup"><span data-stu-id="e61b7-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="e61b7-111">Kompletní ukázku naleznete v galerii [příkladů animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span><span class="sxs-lookup"><span data-stu-id="e61b7-111">For the complete sample, see [Animation Example Gallery](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e61b7-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e61b7-112">See also</span></span>

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="e61b7-113">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="e61b7-113">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="e61b7-114">Postupy: Témata animace a časování</span><span class="sxs-lookup"><span data-stu-id="e61b7-114">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
