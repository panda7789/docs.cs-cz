---
title: "Postupy: Zjednodušení aplikací použitím podřízených časových os"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0d3b8f1ca1dbf7ba5452acffc62fdf0b655c9c12
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a><span data-ttu-id="9be3c-102">Postupy: Zjednodušení aplikací použitím podřízených časových os</span><span class="sxs-lookup"><span data-stu-id="9be3c-102">How to: Simplify Animations by Using Child Timelines</span></span>
<span data-ttu-id="9be3c-103">Tento příklad ukazuje, jak můžete zjednodušit animace pomocí podřízené <xref:System.Windows.Media.Animation.ParallelTimeline> objekty.</span><span class="sxs-lookup"><span data-stu-id="9be3c-103">This example shows how to simplify animations by using child <xref:System.Windows.Media.Animation.ParallelTimeline> objects.</span></span> <span data-ttu-id="9be3c-104">A <xref:System.Windows.Media.Animation.Storyboard> je typ <xref:System.Windows.Media.Animation.Timeline> poskytující cílení informace pro časové osy obsahuje.</span><span class="sxs-lookup"><span data-stu-id="9be3c-104">A <xref:System.Windows.Media.Animation.Storyboard> is a type of <xref:System.Windows.Media.Animation.Timeline> that provides targeting information for the timelines it contains.</span></span> <span data-ttu-id="9be3c-105">Použití <xref:System.Windows.Media.Animation.Storyboard> zajistit časovou osu zacílení na informace, včetně informací o objektu a vlastnost.</span><span class="sxs-lookup"><span data-stu-id="9be3c-105">Use a <xref:System.Windows.Media.Animation.Storyboard> to provide timeline targeting information, including object and property information.</span></span>  
  
 <span data-ttu-id="9be3c-106">Chcete-li začít animace pomocí jednoho nebo více <xref:System.Windows.Media.Animation.ParallelTimeline> objekty jako vnořené podřízených elementů <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="9be3c-106">To begin an animation, use one or more <xref:System.Windows.Media.Animation.ParallelTimeline> objects as nested child elements of a <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="9be3c-107">Tyto <xref:System.Windows.Media.Animation.ParallelTimeline> objekty může obsahovat jiné animace a proto může lépe zapouzdřit časování pořadí v komplexní animace.</span><span class="sxs-lookup"><span data-stu-id="9be3c-107">These <xref:System.Windows.Media.Animation.ParallelTimeline> objects can contain other animations and therefore, can better encapsulate the timing sequences in complex animations.</span></span> <span data-ttu-id="9be3c-108">Například, pokud jsou animace <xref:System.Windows.Controls.TextBlock> a několik tvarů ve stejné <xref:System.Windows.Media.Animation.Storyboard>, můžete oddělit animací pro <xref:System.Windows.Controls.TextBlock> a obrazců, každý do samostatné uvedení <xref:System.Windows.Media.Animation.ParallelTimeline>.</span><span class="sxs-lookup"><span data-stu-id="9be3c-108">For example, if you are animating a <xref:System.Windows.Controls.TextBlock> and several shapes in the same <xref:System.Windows.Media.Animation.Storyboard>, you can separate the animations for the <xref:System.Windows.Controls.TextBlock> and the shapes, putting each into a separate <xref:System.Windows.Media.Animation.ParallelTimeline>.</span></span> <span data-ttu-id="9be3c-109">Protože každý <xref:System.Windows.Media.Animation.ParallelTimeline> má svou vlastní <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> a všech podřízených elementů <xref:System.Windows.Media.Animation.ParallelTimeline> začít relativně k to <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, je lepší zapouzdřený časování.</span><span class="sxs-lookup"><span data-stu-id="9be3c-109">Because each <xref:System.Windows.Media.Animation.ParallelTimeline> has its own <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> and all child elements of the <xref:System.Windows.Media.Animation.ParallelTimeline> begin relative to this <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, timing is better encapsulated.</span></span>  
  
 <span data-ttu-id="9be3c-110">Následující příklad animuje dvě části textu (<xref:System.Windows.Controls.TextBlock> objekty) z v téže <xref:System.Windows.Media.Animation.Storyboard>.</span><span class="sxs-lookup"><span data-stu-id="9be3c-110">The following example animates two pieces of text (<xref:System.Windows.Controls.TextBlock> objects) from within the same <xref:System.Windows.Media.Animation.Storyboard>.</span></span> <span data-ttu-id="9be3c-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> zapouzdří animací jednoho <xref:System.Windows.Controls.TextBlock> objekty.</span><span class="sxs-lookup"><span data-stu-id="9be3c-111">A <xref:System.Windows.Media.Animation.ParallelTimeline> encapsulates the animations of one of the <xref:System.Windows.Controls.TextBlock> objects.</span></span>  
  
 <span data-ttu-id="9be3c-112">**Výkon Poznámka:** i když lze vnořit <xref:System.Windows.Media.Animation.Storyboard> časové osy v sobě navzájem, <xref:System.Windows.Media.Animation.ParallelTimeline>s jsou nejvhodnější pro vnoření vzhledem k tomu, že se vyžadují menší režii.</span><span class="sxs-lookup"><span data-stu-id="9be3c-112">**Performance Note:** Although you can nest <xref:System.Windows.Media.Animation.Storyboard> timelines inside each other, <xref:System.Windows.Media.Animation.ParallelTimeline>s are more suitable for nesting because they require less overhead.</span></span> <span data-ttu-id="9be3c-113">( <xref:System.Windows.Media.Animation.Storyboard> Třída dědí z <xref:System.Windows.Media.Animation.ParallelTimeline> třídy.)</span><span class="sxs-lookup"><span data-stu-id="9be3c-113">(The <xref:System.Windows.Media.Animation.Storyboard> class inherits from the <xref:System.Windows.Media.Animation.ParallelTimeline> class.)</span></span>  
  
## <a name="example"></a><span data-ttu-id="9be3c-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="9be3c-114">Example</span></span>  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="9be3c-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="9be3c-115">See Also</span></span>  
 [<span data-ttu-id="9be3c-116">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="9be3c-116">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="9be3c-117">Určení HandoffBehavior mezi animacemi scénáře</span><span class="sxs-lookup"><span data-stu-id="9be3c-117">Specify HandoffBehavior Between Storyboard Animations</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
