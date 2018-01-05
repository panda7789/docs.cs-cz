---
title: "Postupy: Opakování animace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- RepeatBehavior property of timelines [WPF]
- repeating animating [WPF]
- Timelines RepeatBehavior property [WPF]
- animation [WPF], repeating
ms.assetid: e6f3b068-eeeb-47fd-8d40-8848c31f1e1e
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 591053d479b7d26757eb071f08ed4216fc0d57fd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-repeat-an-animation"></a>Postupy: Opakování animace
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Timeline> aby bylo možné řídit chování opakování animace.  
  
## <a name="example"></a>Příklad  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.Timeline> Určuje, kolikrát opakuje jeho jednoduché trvání animace. Pomocí <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>, můžete určit, že <xref:System.Windows.Media.Animation.Timeline> opakuje pro stanovený počet (počet iterací) nebo pro zadané časové období. V obou případech animace projde tolik spustí začátku do konce, které je nutné, aby vyplnil celou dobu trvání na požadovaný počet.  
  
 Ve výchozím nastavení mají časové osy počet opakování 1.0, což znamená, že přehrání jednou a neopakuje. Ale pokud nastavíte <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost <xref:System.Windows.Media.Animation.Timeline> k <xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>, časovou osu opakuje bez omezení.  
  
 Následující příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> vlastnost pro řízení chování opakování animace. V příkladu animuje <xref:System.Windows.FrameworkElement.Width%2A> vlastnost pět obdélníků se každý rámeček pomocí jiného typu opakování chování.  
  
 [!code-xaml[timingbehaviors_snip#RepeatBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/RepeatBehaviorExample.xaml#repeatbehaviorwholepage)]  
  
 Kompletní příklad, najdete v části [ukázka chování časování animace](http://go.microsoft.com/fwlink/?LinkID=159970).  
  
## <a name="see-also"></a>Viz také  
 [Kumulování hodnot animace při opakujících se cyklech](../../../../docs/framework/wpf/graphics-multimedia/how-to-accumulate-animation-values-during-repeat-cycles.md)  
 [Určení automatického otočení časové osy](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [Animace a časování](http://msdn.microsoft.com/en-us/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Ukázka chování časování animace](http://go.microsoft.com/fwlink/?LinkID=159970)
