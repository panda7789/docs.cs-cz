---
title: 'Postupy: Opakování animace'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141546"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="75079-102">Postupy: Opakování animace</span><span class="sxs-lookup"><span data-stu-id="75079-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="75079-103">Tento příklad ukazuje, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> jak používat <xref:System.Windows.Media.Animation.Timeline> vlastnost a k řízení chování opakování animace.</span><span class="sxs-lookup"><span data-stu-id="75079-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75079-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="75079-104">Example</span></span>  
 <span data-ttu-id="75079-105">Vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> určuje, <xref:System.Windows.Media.Animation.Timeline> kolikrát animace opakuje svou jednoduchou dobu trvání.</span><span class="sxs-lookup"><span data-stu-id="75079-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="75079-106">Pomocí <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>aplikace můžete určit, <xref:System.Windows.Media.Animation.Timeline> že opakování pro určitý počet opakování (počet iterací) nebo pro zadané časové období.</span><span class="sxs-lookup"><span data-stu-id="75079-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="75079-107">V obou případech animace prochází tolik spuštění začátku do konce, které potřebuje k vyplnění požadovaný počet nebo dobu trvání.</span><span class="sxs-lookup"><span data-stu-id="75079-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="75079-108">Ve výchozím nastavení mají časové osy počet opakování 1,0, což znamená, že se přehrávají jednou a neopakují se.</span><span class="sxs-lookup"><span data-stu-id="75079-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="75079-109">Pokud však nastavíte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> vlastnost <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>a , časová osa se opakuje neomezeně dlouho.</span><span class="sxs-lookup"><span data-stu-id="75079-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="75079-110">Následující příklad ukazuje, jak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> použít vlastnost k řízení chování opakování animace.</span><span class="sxs-lookup"><span data-stu-id="75079-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="75079-111">Příklad animuje <xref:System.Windows.FrameworkElement.Width%2A> vlastnost pěti obdélníků s každým obdélníkem pomocí jiného typu chování opakování.</span><span class="sxs-lookup"><span data-stu-id="75079-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="75079-112">Kompletní ukázku naleznete v [tématu Ukázka chování časování animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span><span class="sxs-lookup"><span data-stu-id="75079-112">For the complete sample, see [Animation Timing Behavior Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75079-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="75079-113">See also</span></span>

- [<span data-ttu-id="75079-114">Kumulování hodnot animace při opakujících se cyklech</span><span class="sxs-lookup"><span data-stu-id="75079-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="75079-115">Určení automatického otočení časové osy</span><span class="sxs-lookup"><span data-stu-id="75079-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="75079-116">Postupy: Témata animace a časování</span><span class="sxs-lookup"><span data-stu-id="75079-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="75079-117">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="75079-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="75079-118">Ukázka chování časování animace</span><span class="sxs-lookup"><span data-stu-id="75079-118">Animation Timing Behavior Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
