---
title: 'Postupy: Určení automatické rezervace časové osy'
ms.date: 03/30/2017
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
ms.openlocfilehash: 498aefa16b8a76262c01965b8992ef9a94b7ce28
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560062"
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Postupy: Určení automatické rezervace časové osy
Časové osy <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost určuje, zda splňuje při zpětného, až se dokončí dopředného iterace. Následující příklad ukazuje několik animací s identické doba trvání a cílové hodnoty, ale jiné <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> nastavení. K předvedení jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost chová jiné <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , některé animací nastavení opakování. Poslední zobrazí animace jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost funguje na vnořené časové osy.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
