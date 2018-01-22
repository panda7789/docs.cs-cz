---
title: "Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4b890d121cf06dc377a3bbc1dc569d9dac7c011b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období
Tento příklad ukazuje, jak zadat <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pro neaktivní <xref:System.Windows.Media.Animation.Timeline> animovaný vlastnosti.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, co se stane hodnotou animovaný vlastnosti, když není ani animovaný, to znamená, když <xref:System.Windows.Media.Animation.Timeline> je neaktivní, ale jeho nadřazený objekt <xref:System.Windows.Media.Animation.Timeline> je uvnitř jeho aktivní nebo období uchování. Například nemá animovaný vlastnost zůstat na jeho konci hodnotu po ukončení animace nebo dělá vrátit zpět na hodnotu byl před zahájením animace?  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci <xref:System.Windows.FrameworkElement.Width%2A> ze dvou tvaru. Každý rámeček používá jiné <xref:System.Windows.Media.Animation.Timeline> objektu.  
  
 Jeden <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , je nastaven na <xref:System.Windows.Media.Animation.FillBehavior.Stop>, což způsobí, že šířku rámeček se vrátit zpět k jeho bez animací hodnotu v případě <xref:System.Windows.Media.Animation.Timeline> ukončí. Druhý <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, což způsobí, že šířku zůstat v jeho koncem hodnotu v případě <xref:System.Windows.Media.Animation.Timeline> ukončí.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Kompletní příklad, najdete v části [animace příklad Galerie](http://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.DoubleAnimation>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 <xref:System.Windows.Media.Animation.Timeline>  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>  
 <xref:System.Windows.Media.Animation.FillBehavior.Stop>  
 <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animace a časování](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
