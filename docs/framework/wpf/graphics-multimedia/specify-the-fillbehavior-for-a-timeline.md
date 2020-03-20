---
title: 'Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 1f54f2c1bb49bb7a0301f112a109194ab1a8658e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141170"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období
Tento příklad ukazuje, <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> jak určit <xref:System.Windows.Media.Animation.Timeline> pro neaktivní animované vlastnosti.  
  
## <a name="example"></a>Příklad  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> určuje, co se stane s hodnotou animované vlastnosti, když není animována, to znamená, když <xref:System.Windows.Media.Animation.Timeline> je neaktivní, ale jeho nadřazený <xref:System.Windows.Media.Animation.Timeline> je uvnitř jeho aktivní nebo pozdržet období. Například zůstane animovaná vlastnost na své koncové hodnotě po ukončení animace nebo se vrátí zpět na hodnotu, kterou měla před zahájením animace?  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> k animaci <xref:System.Windows.FrameworkElement.Width%2A> dvou obdélníků. Každý obdélník používá <xref:System.Windows.Media.Animation.Timeline> jiný objekt.  
  
 Jeden <xref:System.Windows.Media.Animation.Timeline> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> má, který <xref:System.Windows.Media.Animation.FillBehavior.Stop>je nastaven na , což způsobí, že šířka obdélníku <xref:System.Windows.Media.Animation.Timeline> vrátit zpět do své neanimované hodnoty po skončení. Druhý <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> a <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, což způsobí, že šířka <xref:System.Windows.Media.Animation.Timeline> zůstane na jeho koncové hodnotě při ukončení.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Kompletní ukázku naleznete v galerii [příkladů animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationExamples).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Přehled animace](animation-overview.md)
- [Postupy: Témata animace a časování](animation-and-timing-how-to-topics.md)
