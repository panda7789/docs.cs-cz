---
title: 'Postupy: Nastavení trvání pro animaci'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
ms.openlocfilehash: 7a2edbd953f648d5555e5dc50469211a6da066de
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497928"
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="a8c4e-102">Postupy: Nastavení trvání pro animaci</span><span class="sxs-lookup"><span data-stu-id="a8c4e-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="a8c4e-103">A <xref:System.Windows.Media.Animation.Timeline> představuje segment čas a délka tohoto segmentu se zakládá na časové ose <xref:System.Windows.Duration>.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="a8c4e-104">Když <xref:System.Windows.Media.Animation.Timeline> dosažení konce jeho trvání, zastaví přehrávání.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="a8c4e-105">Pokud <xref:System.Windows.Media.Animation.Timeline> má podřízených časových os, vyhodnocování se zastaví přehrávání také.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="a8c4e-106">V případě animace <xref:System.Windows.Duration> Určuje, jak dlouho animace trvá přechod z jeho výchozí hodnotu na jeho koncovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="a8c4e-107">Můžete zadat <xref:System.Windows.Duration> s konkrétní, omezené dobu nebo speciálními hodnotami <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="a8c4e-108">Doba trvání pro animaci musí být vždy časové hodnoty, protože animace vždy musí mít délku definovanou, omezené – jinak nebude animace vědět, jak přecházet mezi jeho cílové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="a8c4e-109">Časové osy kontejneru (<xref:System.Windows.Media.Animation.TimelineGroup> objekty), jako například <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.ParallelTimeline>, výchozí doba trvání <xref:System.Windows.Duration.Automatic%2A>, což znamená, že automaticky ukončí po jejich posledního podřízeného zastaví přehrávání.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="a8c4e-110">V následujícím příkladu, šířku, výšku a výplň barvu <xref:System.Windows.Shapes.Rectangle> je animovaný.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="a8c4e-111">Doba trvání jsou nastavené na časové ose animace a kontejner výsledkem efekty animace včetně řízení zjištěné rychlosti animace a přepsáním trvání podřízených časových os s dobou trvání časové osy kontejneru.</span><span class="sxs-lookup"><span data-stu-id="a8c4e-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8c4e-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="a8c4e-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="a8c4e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a8c4e-113">See also</span></span>
- <xref:System.Windows.Duration>
- [<span data-ttu-id="a8c4e-114">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="a8c4e-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
