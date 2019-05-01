---
title: 'Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období'
ms.date: 03/30/2017
helpviewer_keywords:
- FillBehavior property for inactive timelines [WPF]
- Timelines [WPF], FillBehavior property
ms.assetid: db805f59-d513-4dac-af15-47005dae3199
ms.openlocfilehash: 9f03c5b8d4585c32e0a9f119649dd15a23523033
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973664"
---
# <a name="how-to-specify-the-fillbehavior-for-a-timeline-that-has-reached-the-end-of-its-active-period"></a>Postupy: Určení FillBehavior pro časovou osu, která dosáhla konce aktivního období
Tento příklad ukazuje, jak určit <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> pro neaktivní <xref:System.Windows.Media.Animation.Timeline> animované vlastnosti.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, co se stane hodnotou animované vlastnosti, když není právě animovat, to znamená, když <xref:System.Windows.Media.Animation.Timeline> je neaktivní, ale jeho nadřazený objekt <xref:System.Windows.Media.Animation.Timeline> se nachází uvnitř jeho aktivní nebo období uchování. Například nemá animované vlastnosti zůstávají na jeho konci hodnota po ukončení animace nebo to udělá vrátit zpět na hodnotu byl před zahájením animace?  
  
 Následující příklad používá <xref:System.Windows.Media.Animation.DoubleAnimation> pro animaci <xref:System.Windows.FrameworkElement.Width%2A> dvou obdélníků. Každý používá jiný <xref:System.Windows.Media.Animation.Timeline> objektu.  
  
 Jeden <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> , která je nastavena na <xref:System.Windows.Media.Animation.FillBehavior.Stop>, což způsobí, že šířku obdélníku do zpátky na jeho bez animací hodnotu v případě <xref:System.Windows.Media.Animation.Timeline> skončí. Druhý <xref:System.Windows.Media.Animation.Timeline> má <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> z <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>, což způsobí, že šířka zůstat na jeho konci hodnotu v případě <xref:System.Windows.Media.Animation.Timeline> skončí.  
  
 [!code-xaml[timingbehaviors_snip#FillBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/FillBehaviorExample.xaml#fillbehaviorwholepage)]  
  
 Úplnou ukázku najdete v tématu [animace příkladu Galerie](https://go.microsoft.com/fwlink/?LinkID=159969).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.DoubleAnimation>
- <xref:System.Windows.FrameworkElement.Width%2A>
- <xref:System.Windows.Media.Animation.Timeline>
- <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>
- <xref:System.Windows.Media.Animation.FillBehavior.Stop>
- <xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>
- [Přehled animace](animation-overview.md)
- [Animace a časování témata s postupy](animation-and-timing-how-to-topics.md)
