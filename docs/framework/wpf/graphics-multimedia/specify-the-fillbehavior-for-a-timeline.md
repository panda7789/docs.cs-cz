---
title: 'Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 6745cf5d57a341068e93784d5487f21e34f8a64a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54530091"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="55382-102">Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období</span><span class="sxs-lookup"><span data-stu-id="55382-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="55382-103">Tento příklad ukazuje, jak určit <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pro neaktivní <xref:System.Windows.Media.Animation.Timeline> animované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="55382-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55382-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="55382-104">Example</span></span>  
 <span data-ttu-id="55382-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, co se stane hodnotou animované vlastnosti, když není právě animovat, to znamená, když <xref:System.Windows.Media.Animation.Timeline> je neaktivní, ale jeho nadřazený objekt <xref:System.Windows.Media.Animation.Timeline> se nachází uvnitř jeho aktivní nebo období uchování.</span><span class="sxs-lookup"><span data-stu-id="55382-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="55382-106">Například nemá animované vlastnosti zůstávají na jeho konci hodnota po ukončení animace nebo to udělá vrátit zpět na hodnotu byl před zahájením animace?</span><span class="sxs-lookup"><span data-stu-id="55382-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="55382-107">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci <xref:System.Windows.FrameworkElement.Width%2A> dvou obdélníků.</span><span class="sxs-lookup"><span data-stu-id="55382-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="55382-108">Každý používá jiný <xref:System.Windows.Media.Animation.Timeline> objektu.</span><span class="sxs-lookup"><span data-stu-id="55382-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="55382-109">Jeden <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , která je nastavena na <xref:System.Windows.Media.Animation.FillBehavior.Stop>, což způsobí, že šířku obdélníku do zpátky na jeho bez animací hodnotu v případě <xref:System.Windows.Media.Animation.Timeline> skončí.</span><span class="sxs-lookup"><span data-stu-id="55382-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="55382-110">Druhý <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, což způsobí, že šířka zůstat na jeho konci hodnotu v případě <xref:System.Windows.Media.Animation.Timeline> skončí.</span><span class="sxs-lookup"><span data-stu-id="55382-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="55382-111">Úplnou ukázku najdete v tématu [animace příkladu Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="55382-111">For the complete sample, see [Animation Example Gallery](https://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55382-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55382-112">See also</span></span>
- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [<span data-ttu-id="55382-113">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="55382-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [<span data-ttu-id="55382-114">Animace a časování</span><span class="sxs-lookup"><span data-stu-id="55382-114">Animation and Timing</span></span>](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)
- [<span data-ttu-id="55382-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="55382-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
