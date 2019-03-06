---
title: 'Postupy: Opakování animace'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: a098c912289f59f8be48edeec0f066b7f94b9fda
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57353997"
---
# <a name="how-to-repeat-an-animation"></a><span data-ttu-id="0cc79-102">Postupy: Opakování animace</span><span class="sxs-lookup"><span data-stu-id="0cc79-102">How to: Repeat an Animation</span></span>
<span data-ttu-id="0cc79-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Timeline> aby bylo možné řídit chování opakování animace.</span><span class="sxs-lookup"><span data-stu-id="0cc79-103">This example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> in order to control the repeat behavior of an animation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cc79-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cc79-104">Example</span></span>  
 <span data-ttu-id="0cc79-105"><xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, kolikrát opakuje jeho jednoduchý doba trvání animace.</span><span class="sxs-lookup"><span data-stu-id="0cc79-105">The <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> controls how many times an animation repeats its simple duration.</span></span> <span data-ttu-id="0cc79-106">S použitím <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, můžete určit, že <xref:System.Windows.Media.Animation.Timeline> opakuje pro určitý počet časy (nepředstavuje počet iterací) nebo za zadané časové období.</span><span class="sxs-lookup"><span data-stu-id="0cc79-106">By using <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, you can specify that a <xref:System.Windows.Media.Animation.Timeline> repeats for a certain number of times (an iteration count) or for a specified time period.</span></span> <span data-ttu-id="0cc79-107">V obou případech se animace prochází tolik spuštění začátku do konce, které jsou potřebné k vyplnění požadovaný počet nebo dobu trvání.</span><span class="sxs-lookup"><span data-stu-id="0cc79-107">In either case, the animation goes through as many beginning-to-end runs that it needs in order to fill the requested count or duration.</span></span>  
  
 <span data-ttu-id="0cc79-108">Ve výchozím nastavení mají časové osy počet opakování pro 1.0, což znamená, že Přehrát jednou a neopakuje.</span><span class="sxs-lookup"><span data-stu-id="0cc79-108">By default, timelines have a repeat count of 1.0, which means they play one time and do not repeat.</span></span> <span data-ttu-id="0cc79-109">Ale pokud nastavíte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Timeline> k <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, na časové ose opakuje bez omezení.</span><span class="sxs-lookup"><span data-stu-id="0cc79-109">However, if you set the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property of a <xref:System.Windows.Media.Animation.Timeline> to <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, the timeline repeats indefinitely.</span></span>  
  
 <span data-ttu-id="0cc79-110">Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastností pro řízení chování opakování animace.</span><span class="sxs-lookup"><span data-stu-id="0cc79-110">The following example shows how to use the <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> property to control the repeat behavior of an animation.</span></span> <span data-ttu-id="0cc79-111">V příkladu animuje <xref:System.Windows.FrameworkElement.Width%2A> vlastnost pět obdélníků s každou obdélníku pomocí jiného typu chování opakování.</span><span class="sxs-lookup"><span data-stu-id="0cc79-111">The example animates the <xref:System.Windows.FrameworkElement.Width%2A> property of five rectangles with each rectangle using a different type of repeat behavior.</span></span>  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 <span data-ttu-id="0cc79-112">Úplnou ukázku najdete v tématu [ukázka chování časování animace](https://go.microsoft.com/fwlink/?LinkID=159970).</span><span class="sxs-lookup"><span data-stu-id="0cc79-112">For the complete sample, see [Animation Timing Behavior Sample](https://go.microsoft.com/fwlink/?LinkID=159970).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cc79-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cc79-113">See also</span></span>
- [<span data-ttu-id="0cc79-114">Kumulování hodnot animace při opakujících se cyklech</span><span class="sxs-lookup"><span data-stu-id="0cc79-114">Accumulate Animation Values During Repeat Cycles</span></span>](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [<span data-ttu-id="0cc79-115">Určení automatického otočení časové osy</span><span class="sxs-lookup"><span data-stu-id="0cc79-115">Specify Whether a Timeline Automatically Reverses</span></span>](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [<span data-ttu-id="0cc79-116">Animace a časování témata s postupy</span><span class="sxs-lookup"><span data-stu-id="0cc79-116">Animation and Timing How-to Topics</span></span>](animation-and-timing-how-to-topics.md)
- [<span data-ttu-id="0cc79-117">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="0cc79-117">Animation Overview</span></span>](animation-overview.md)
- [<span data-ttu-id="0cc79-118">Ukázka chování časování animace</span><span class="sxs-lookup"><span data-stu-id="0cc79-118">Animation Timing Behavior Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159970)
