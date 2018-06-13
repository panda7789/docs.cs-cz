---
title: 'Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 947be09140dc2d1d5e130ccb74472d8dce3408cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563477"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a><span data-ttu-id="51374-102">Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období</span><span class="sxs-lookup"><span data-stu-id="51374-102">How to: Specify the FillBehavior for a Timeline that has Reached the End of Its Active Period</span></span>
<span data-ttu-id="51374-103">Tento příklad ukazuje, jak zadat <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pro neaktivní <xref:System.Windows.Media.Animation.Timeline> animovaný vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="51374-103">This example shows how to specify the <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> for the inactive <xref:System.Windows.Media.Animation.Timeline> of an animated property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51374-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="51374-104">Example</span></span>  
 <span data-ttu-id="51374-105"><xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, co se stane hodnotou animovaný vlastnosti, když není ani animovaný, to znamená, když <xref:System.Windows.Media.Animation.Timeline> je neaktivní, ale jeho nadřazený objekt <xref:System.Windows.Media.Animation.Timeline> je uvnitř jeho aktivní nebo období uchování.</span><span class="sxs-lookup"><span data-stu-id="51374-105">The <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> determines what happens to the value of an animated property when it is not being animated, that is, when the <xref:System.Windows.Media.Animation.Timeline> is inactive but its parent <xref:System.Windows.Media.Animation.Timeline> is inside its active or hold period.</span></span> <span data-ttu-id="51374-106">Například nemá animovaný vlastnost zůstat na jeho konci hodnotu po ukončení animace nebo dělá vrátit zpět na hodnotu byl před zahájením animace?</span><span class="sxs-lookup"><span data-stu-id="51374-106">For example, does an animated property remain at its end value after the animation ends or does it revert back to the value it had before the animation started?</span></span>  
  
 <span data-ttu-id="51374-107">Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci <xref:System.Windows.FrameworkElement.Width%2A> ze dvou tvaru.</span><span class="sxs-lookup"><span data-stu-id="51374-107">The following example uses a <xref:System.Windows.Media.Animation.DoubleAnimation> to animate the <xref:System.Windows.FrameworkElement.Width%2A> of two rectangles.</span></span> <span data-ttu-id="51374-108">Každý rámeček používá jiné <xref:System.Windows.Media.Animation.Timeline> objektu.</span><span class="sxs-lookup"><span data-stu-id="51374-108">Each rectangle uses a different <xref:System.Windows.Media.Animation.Timeline> object.</span></span>  
  
 <span data-ttu-id="51374-109">Jeden <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , je nastaven na <xref:System.Windows.Media.Animation.FillBehavior.Stop>, což způsobí, že šířku rámeček se vrátit zpět k jeho bez animací hodnotu v případě <xref:System.Windows.Media.Animation.Timeline> ukončí.</span><span class="sxs-lookup"><span data-stu-id="51374-109">One <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> that is set to <xref:System.Windows.Media.Animation.FillBehavior.Stop>, which causes the width of the rectangle to revert back to its non-animated value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span> <span data-ttu-id="51374-110">Druhý <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, což způsobí, že šířku zůstat v jeho koncem hodnotu v případě <xref:System.Windows.Media.Animation.Timeline> ukončí.</span><span class="sxs-lookup"><span data-stu-id="51374-110">The other <xref:System.Windows.Media.Animation.Timeline> has a <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> of <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, which causes the width to remain at its end value when the <xref:System.Windows.Media.Animation.Timeline> ends.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 <span data-ttu-id="51374-111">Kompletní příklad, najdete v části [animace příklad Galerie](http://go.microsoft.com/fwlink/?LinkID=159969).</span><span class="sxs-lookup"><span data-stu-id="51374-111">For the complete sample, see [Animation Example Gallery](http://go.microsoft.com/fwlink/?LinkID=159969).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51374-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="51374-112">See Also</span></span>  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [<span data-ttu-id="51374-113">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="51374-113">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="51374-114">Animace a časování</span><span class="sxs-lookup"><span data-stu-id="51374-114">Animation and Timing</span></span>](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [<span data-ttu-id="51374-115">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="51374-115">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
