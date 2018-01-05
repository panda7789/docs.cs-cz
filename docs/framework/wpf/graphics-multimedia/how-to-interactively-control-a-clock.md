---
title: "Postupy: Interaktivní řízení hodin"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controlling clocks interactively [WPF]
- clocks [WPF], controlling interactively
ms.assetid: d0b520e0-2f18-4cef-977f-2909e709548a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d24a5154607bf535cbf995705332092bb86ca02e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-interactively-control-a-clock"></a>Postupy: Interaktivní řízení hodin
A <xref:System.Windows.Media.Animation.Clock> objektu <xref:System.Windows.Media.Animation.ClockController> vlastnost umožňuje interaktivně spuštění, pozastavení, obnovení, Hledat, posunutí hodiny na jeho výplně období a zastavte hodiny. Pouze kořenové hodiny stromu časování lze řídit interaktivně.  
  
> [!NOTE]
>  Existují další způsoby, jak interaktivně ovládacího prvku animace, které nevyžadují pracovat přímo s hodiny: Můžete taky scénářů. Scénářů jsou podporovány v značek a kódu. Příklad, naleznete v části [animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) nebo [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md).  
  
 V následujícím příkladu je možné několik tlačítka interaktivně určit hodiny animace.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/ClockControllerExample.cs#graphicsmmclockcontrollerexample)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMClockControllerExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/clockcontrollerexample.vb#graphicsmmclockcontrollerexample)]  
  
## <a name="see-also"></a>Viz také  
 [Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
