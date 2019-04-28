---
title: 'Postupy: Určení HandoffBehavior mezi animacemi scénáře'
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: d7129d6a48bdf31dc4953bb450267ad3b38fdd17
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651035"
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>Postupy: Určení HandoffBehavior mezi animacemi scénáře
Tento příklad ukazuje, jak určit chování při předání mezi animacemi scénáře. <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> Vlastnost <xref:System.Windows.Media.Animation.BeginStoryboard> Určuje, jak nové animace interakci s všechny existující dokumenty, které jsou již přidruženy k vlastnosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dvě tlačítka, které zvětšení při přesunu kurzoru myši nad nimi a zmenší, pokud kurzor se přesune jinam. Pokud myší na tlačítko a rychle odebrat kurzor, druhé animace se použije před dokončením první z nich. Bylo při překrývat s následujícím způsobem, který se zobrazí rozdíl mezi dvěma animace <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> hodnoty <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> a <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>. Hodnota <xref:System.Windows.Media.Animation.HandoffBehavior.Compose> kombinuje překrývajících se animací způsobí hladší přechod mezi animacemi při hodnotu <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> způsobí, že nový animace okamžitě nahradit dříve překrývajících se animací.  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.BeginStoryboard>
- <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>
- [Přehled animace](animation-overview.md)
- [Animace a časování témata s postupy](animation-and-timing-how-to-topics.md)
