---
title: 'Postupy: Zjednodušení aplikací použitím podřízených časových os'
ms.date: 03/30/2017
helpviewer_keywords:
- simplifying animations by child timelines [WPF]
- animation [WPF], simplifying by child timelines
- child timelines [WPF]
ms.assetid: 8335d770-d13d-42bd-8dfa-63f92c0327e2
ms.openlocfilehash: 933ba2dff86b99bddd8d8f75bafcd94833b2e066
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57370355"
---
# <a name="how-to-simplify-animations-by-using-child-timelines"></a>Postupy: Zjednodušení aplikací použitím podřízených časových os
Tento příklad ukazuje, jak zjednodušení aplikací použitím podřízených <xref:System.Windows.Media.Animation.ParallelTimeline> objekty. A <xref:System.Windows.Media.Animation.Storyboard> je typ <xref:System.Windows.Media.Animation.Timeline> , který obsahuje cílení informace o časových os obsahuje. Použití <xref:System.Windows.Media.Animation.Storyboard> stanovit časovou osu zacílení na informace, včetně informací o objektu a vlastnosti.  
  
 Pokud chcete začít animace, použijte jednu nebo více <xref:System.Windows.Media.Animation.ParallelTimeline> objekty jako vnořené podřízené prvky <xref:System.Windows.Media.Animation.Storyboard>. Tyto <xref:System.Windows.Media.Animation.ParallelTimeline> objekty mohou obsahovat jiné animace a proto můžete lépe zapouzdřit pořadí časování v komplexních animace. Například, pokud jsou animace <xref:System.Windows.Controls.TextBlock> a několik obrazců ve stejném <xref:System.Windows.Media.Animation.Storyboard>, můžete oddělit animace pro <xref:System.Windows.Controls.TextBlock> a tvary, vložení, každého do samostatné <xref:System.Windows.Media.Animation.ParallelTimeline>. Protože každý <xref:System.Windows.Media.Animation.ParallelTimeline> má vlastní <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> a všechny podřízené prvky prvku <xref:System.Windows.Media.Animation.ParallelTimeline> začít vzhledem k to <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>, lépe zapouzdřená časování.  
  
 Následující příklad animuje dva druhy textu (<xref:System.Windows.Controls.TextBlock> objekty) z v rámci stejného <xref:System.Windows.Media.Animation.Storyboard>. A <xref:System.Windows.Media.Animation.ParallelTimeline> zapouzdřuje animace některého <xref:System.Windows.Controls.TextBlock> objekty.  
  
 **Poznámka: výkonu:** I když můžete vnořit <xref:System.Windows.Media.Animation.Storyboard> časové osy uvnitř sebe navzájem <xref:System.Windows.Media.Animation.ParallelTimeline>s jsou vhodnější pro vnoření vzhledem k tomu, že jsou menší nákladovou režii. ( <xref:System.Windows.Media.Animation.Storyboard> Třída dědí z <xref:System.Windows.Media.Animation.ParallelTimeline> třídy.)  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Timelines_snip#ParallelTimelineWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Timelines_snip/CS/ParallelTimelineExample.xaml#paralleltimelinewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled animace](animation-overview.md)
- [Určení HandoffBehavior mezi animacemi scénáře](how-to-specify-handoffbehavior-between-storyboard-animations.md)
