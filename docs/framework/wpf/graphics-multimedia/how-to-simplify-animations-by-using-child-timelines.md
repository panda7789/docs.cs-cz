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
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>Postupy: Zjednodušení aplikací použitím podřízených časových os
Tento příklad ukazuje, jak můžete zjednodušit animace pomocí podřízené <xref:System.Windows.Media.Animation.ParallelTimeline> objekty. A <xref:System.Windows.Media.Animation.Storyboard> je typ <xref:System.Windows.Media.Animation.Timeline> poskytující cílení informace pro časové osy obsahuje. Použití <xref:System.Windows.Media.Animation.Storyboard> zajistit časovou osu zacílení na informace, včetně informací o objektu a vlastnost.  
  
 Chcete-li začít animace pomocí jednoho nebo více <xref:System.Windows.Media.Animation.ParallelTimeline> objekty jako vnořené podřízených elementů <xref:System.Windows.Media.Animation.Storyboard>. Tyto <xref:System.Windows.Media.Animation.ParallelTimeline> objekty může obsahovat jiné animace a proto může lépe zapouzdřit časování pořadí v komplexní animace. Například, pokud jsou animace <xref:System.Windows.Controls.TextBlock> a několik tvarů ve stejné <xref:System.Windows.Media.Animation.Storyboard>, můžete oddělit animací pro <xref:System.Windows.Controls.TextBlock> a obrazců, každý do samostatné uvedení <xref:System.Windows.Media.Animation.ParallelTimeline>. Protože každý <xref:System.Windows.Media.Animation.ParallelTimeline> má svou vlastní <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> a všech podřízených elementů <xref:System.Windows.Media.Animation.ParallelTimeline> začít relativně k to <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, je lepší zapouzdřený časování.  
  
 Následující příklad animuje dvě části textu (<xref:System.Windows.Controls.TextBlock> objekty) z v téže <xref:System.Windows.Media.Animation.Storyboard>. A <xref:System.Windows.Media.Animation.ParallelTimeline> zapouzdří animací jednoho <xref:System.Windows.Controls.TextBlock> objekty.  
  
 **Výkon Poznámka:** i když lze vnořit <xref:System.Windows.Media.Animation.Storyboard> časové osy v sobě navzájem, <xref:System.Windows.Media.Animation.ParallelTimeline>s jsou nejvhodnější pro vnoření vzhledem k tomu, že se vyžadují menší režii. ( <xref:System.Windows.Media.Animation.Storyboard> Třída dědí z <xref:System.Windows.Media.Animation.ParallelTimeline> třídy.)  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Určení HandoffBehavior mezi animacemi scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-handoffbehavior-between-storyboard-animations.md)
