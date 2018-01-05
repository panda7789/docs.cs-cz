---
title: "Postupy: Určení automatické rezervace časové osy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- AutoReverse property of timelines [WPF]
- Timelines [WPF], AutoReverse property
ms.assetid: 1648dd90-1bee-409a-ac69-ac729867f557
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da1330a8513f43e7543f97838ef8e9be788af396
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-whether-a-timeline-automatically-reverses"></a>Postupy: Určení automatické rezervace časové osy
Časové osy <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost určuje, zda splňuje při zpětného, až se dokončí dopředného iterace. Následující příklad ukazuje několik animací s identické doba trvání a cílové hodnoty, ale jiné <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> nastavení. K předvedení jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost chová jiné <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> , některé animací nastavení opakování. Poslední zobrazí animace jak <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A> vlastnost funguje na vnořené časové osy.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[timingbehaviors_snip#AutoReverseAndRepeatBehaviorExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/AutoReverseExample.xaml#autoreverseandrepeatbehaviorexamplewholepage)]
