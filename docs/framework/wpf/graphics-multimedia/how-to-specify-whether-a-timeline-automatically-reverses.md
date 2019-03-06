---
title: 'Postupy: Určení automatické rezervace časové osy'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 0fe2d337d8afa5197475e5b9ee40950226596e8b
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354203"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Postupy: Určení automatické rezervace časové osy
Časové osy <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost určuje, zda hraje v opačném pořadí po dokončení dopředné iterace. Následující příklad ukazuje několik animace s identické doba trvání a cílové hodnoty, ale s různými <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> nastavení. K předvedení jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost chová se s různými <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , některé animace nastavení opakujte. Zobrazí se poslední animace jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost funguje na časové ose vnořené.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
