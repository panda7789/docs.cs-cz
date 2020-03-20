---
title: 'Postupy: Opakování animace'
ms.date: 03/30/2017
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
ms.openlocfilehash: 1512c49a658c80f3ab6af652839c3562af3dd205
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79141546"
---
# <a name="how-to-repeat-an-animation"></a>Postupy: Opakování animace
Tento příklad ukazuje, <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> jak používat <xref:System.Windows.Media.Animation.Timeline> vlastnost a k řízení chování opakování animace.  
  
## <a name="example"></a>Příklad  
 Vlastnost <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> určuje, <xref:System.Windows.Media.Animation.Timeline> kolikrát animace opakuje svou jednoduchou dobu trvání. Pomocí <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>aplikace můžete určit, <xref:System.Windows.Media.Animation.Timeline> že opakování pro určitý počet opakování (počet iterací) nebo pro zadané časové období. V obou případech animace prochází tolik spuštění začátku do konce, které potřebuje k vyplnění požadovaný počet nebo dobu trvání.  
  
 Ve výchozím nastavení mají časové osy počet opakování 1,0, což znamená, že se přehrávají jednou a neopakují se. Pokud však nastavíte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> <xref:System.Windows.Media.Animation.Timeline> vlastnost <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>a , časová osa se opakuje neomezeně dlouho.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> použít vlastnost k řízení chování opakování animace. Příklad animuje <xref:System.Windows.FrameworkElement.Width%2A> vlastnost pěti obdélníků s každým obdélníkem pomocí jiného typu chování opakování.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Kompletní ukázku naleznete v [tématu Ukázka chování časování animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming).  
  
## <a name="see-also"></a>Viz také

- [Kumulování hodnot animace při opakujících se cyklech](how-to-accumulate-animation-values-during-repeat-cycles.md)
- [Určení automatického otočení časové osy](how-to-specify-whether-a-timeline-automatically-reverses.md)
- [Postupy: Témata animace a časování](animation-and-timing-how-to-topics.md)
- [Přehled animace](animation-overview.md)
- [Ukázka chování časování animace](https://github.com/Microsoft/WPF-Samples/tree/master/Animation/AnimationTiming)
