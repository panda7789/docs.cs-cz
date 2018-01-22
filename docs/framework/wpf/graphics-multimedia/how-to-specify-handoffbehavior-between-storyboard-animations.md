---
title: "Postupy: Určení HandoffBehavior mezi animacemi scénáře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d11c559679b67c22eeed87893bf2e362084034c
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Postupy: Určení HandoffBehavior mezi animacemi scénáře
Tento příklad ukazuje, jak určit chování předávaných mezi storyboard animace. <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.BeginStoryboard> Určuje, jak nové animace interakci s všechny existující ty, které jsou již přidruženy k vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě tlačítka, která zvětší při přesunutí kurzoru myši nad nimi a zmenší, když přesunut, kurzor. Je-li na tlačítko myši a potom rychle odeberte kurzor, aplikují se před dokončením první druhý animace. Pokud dva animací překrývat jako to, který se zobrazí rozdíl mezi, je <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> hodnoty <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> a <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. Hodnota <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> kombinuje překrývající se animace způsobuje hladší přechod mezi animací při hodnotu <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> způsobí, že nové animace okamžitě nahradit dříve překrývající se animace.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Animace a časování](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
