---
title: 'Postupy: Opakování animace'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 176fc9c31f85361a243cd9357d79608e0ff6a4cd
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43855293"
---
# <a name="how-to-repeat-an-animation"></a>Postupy: Opakování animace
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Timeline> aby bylo možné řídit chování opakování animace.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, kolikrát opakuje jeho jednoduchý doba trvání animace. S použitím <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, můžete určit, že <xref:System.Windows.Media.Animation.Timeline> opakuje pro určitý počet časy (nepředstavuje počet iterací) nebo za zadané časové období. V obou případech se animace prochází tolik spuštění začátku do konce, které jsou potřebné k vyplnění požadovaný počet nebo dobu trvání.  
  
 Ve výchozím nastavení mají časové osy počet opakování pro 1.0, což znamená, že Přehrát jednou a neopakuje. Ale pokud nastavíte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Timeline> k <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, na časové ose opakuje bez omezení.  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastností pro řízení chování opakování animace. V příkladu animuje <xref:System.Windows.FrameworkElement.Width%2A> vlastnost pět obdélníků s každou obdélníku pomocí jiného typu chování opakování.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Úplnou ukázku najdete v tématu [ukázka chování časování animace](https://go.microsoft.com/fwlink/?LinkID=159970).  
  
## <a name="see-also"></a>Viz také  
 [Kumulování hodnot animace při opakujících se cyklech](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Určení automatického otočení časové osy](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Animace a časování](https://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Ukázka chování časování animace](https://go.microsoft.com/fwlink/?LinkID=159970)
