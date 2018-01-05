---
title: "Postupy: Nastavení trvání pro animaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], duration
- Timelines [WPF], description
- duration of animations [WPF]
ms.assetid: 155034ef-7d00-4416-a73c-b1713992d2eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e8d15a1b8432b3dae5bee73396bdec9fc9d50f0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-a-duration-for-an-animation"></a><span data-ttu-id="4ac7c-102">Postupy: Nastavení trvání pro animaci</span><span class="sxs-lookup"><span data-stu-id="4ac7c-102">How to: Set a Duration for an Animation</span></span>
<span data-ttu-id="4ac7c-103">A <xref:System.Windows.Media.Animation.Timeline> představuje segment čas a že segmentu je dáno časové ose <xref:System.Windows.Duration>.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-103">A <xref:System.Windows.Media.Animation.Timeline> represents a segment of time and the length of that segment is determined by the timeline's <xref:System.Windows.Duration>.</span></span> <span data-ttu-id="4ac7c-104">Když <xref:System.Windows.Media.Animation.Timeline> dosáhne konce z jeho trvání, zastaví se přehrávání.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-104">When a <xref:System.Windows.Media.Animation.Timeline> reaches the end of its duration, it stops playing.</span></span> <span data-ttu-id="4ac7c-105">Pokud <xref:System.Windows.Media.Animation.Timeline> má podřízené časových os, přestane také přehrávání.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-105">If the <xref:System.Windows.Media.Animation.Timeline> has child timelines, they stop playing as well.</span></span> <span data-ttu-id="4ac7c-106">V případě animace <xref:System.Windows.Duration> Určuje, jak dlouho animace trvá přechod z jeho výchozí hodnotu na jeho koncovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-106">In the case of an animation, the <xref:System.Windows.Duration> specifies how long the animation takes to transition from its starting value to its ending value.</span></span>  
  
 <span data-ttu-id="4ac7c-107">Můžete zadat <xref:System.Windows.Duration> s konkrétní, konečný čas nebo speciální hodnoty <xref:System.Windows.Duration.Automatic%2A> nebo <xref:System.Windows.Duration.Forever%2A>.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-107">You can specify a <xref:System.Windows.Duration> with a specific, finite time or the special values <xref:System.Windows.Duration.Automatic%2A> or <xref:System.Windows.Duration.Forever%2A>.</span></span> <span data-ttu-id="4ac7c-108">Doba trvání animace na musí být vždy hodnotu času, protože animace musí mít vždy definované, konečné délku –, jinak nebude animace vědět, jak přecházet mezi jeho cílové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-108">An animation's duration must always be a time value, because an animation must always have a defined, finite length—otherwise, the animation would not know how to transition between its target values.</span></span> <span data-ttu-id="4ac7c-109">Kontejner časové osy (<xref:System.Windows.Media.Animation.TimelineGroup> objekty), jako například <xref:System.Windows.Media.Animation.Storyboard> a <xref:System.Windows.Media.Animation.ParallelTimeline>, výchozí doba trvání <xref:System.Windows.Duration.Automatic%2A>, což znamená, že automaticky ukončí při jejich posledního podřízeného zastavení přehrávání.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-109">Container timelines (<xref:System.Windows.Media.Animation.TimelineGroup> objects), such as <xref:System.Windows.Media.Animation.Storyboard> and <xref:System.Windows.Media.Animation.ParallelTimeline>, have a default duration of <xref:System.Windows.Duration.Automatic%2A>, which means they automatically end when their last child stops playing.</span></span>  
  
 <span data-ttu-id="4ac7c-110">V následujícím příkladu, šířky, výšky a výplně barva <xref:System.Windows.Shapes.Rectangle> je animace.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-110">In the following example, the width, height and fill color of a <xref:System.Windows.Shapes.Rectangle> is animated.</span></span> <span data-ttu-id="4ac7c-111">Doby jsou nastavené na animace a kontejner časové osy které animace účinky, včetně řízení dosahovaný rychlost animace a přepsáním trvání časové osy podřízeného s trvání časová osa kontejneru.</span><span class="sxs-lookup"><span data-stu-id="4ac7c-111">Durations are set on animation and container timelines resulting in animation effects including controlling the perceived speed of an animation and overriding the duration of child timelines with the duration of a container timeline.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ac7c-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4ac7c-112">Example</span></span>  
 [!code-xaml[timingbehaviors_snip#DurationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/DurationExample.xaml#durationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="4ac7c-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ac7c-113">See Also</span></span>  
 <xref:System.Windows.Duration>  
 [<span data-ttu-id="4ac7c-114">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="4ac7c-114">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
