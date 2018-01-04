---
title: "Postupy: Animace vlastnosti pomocí AnimationClock"
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
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 145ff1be88f1af6692a8cf374e871479ed38d7bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>Postupy: Animace vlastnosti pomocí AnimationClock
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.Animation.Clock> objekty, které se použije animaci vlastnost.  
  
 Existují tři způsoby, jak animace vlastnosti závislosti:  
  
-   Vytvoření <xref:System.Windows.Media.Animation.AnimationTimeline> a přidružte ji k vlastnosti pomocí <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Pomocí objektu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda použití jedné <xref:System.Windows.Media.Animation.AnimationTimeline> pro vlastnost target.  
  
-   Vytvoření <xref:System.Windows.Media.Animation.AnimationClock> z <xref:System.Windows.Media.Animation.AnimationTimeline> a použijte ho pro vlastnost.  
  
 <xref:System.Windows.Media.Animation.Storyboard>objekty a <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metoda umožňují animace vlastnosti bez přímo vytváření a distribuci hodiny (příklady najdete v tématu [animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md) a [animace vlastnosti bez Použití scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)); hodiny jsou vytvořen a distribuován pro vás automaticky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.AnimationClock> a použijte ho pro dvě podobné vlastnosti.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Příklad znázorňující postup interaktivně řízení <xref:System.Windows.Media.Animation.Clock> po zahájení, najdete v části [interaktivně řízení hodiny, které](../../../../docs/framework/wpf/graphics-multimedia/how-to-interactively-control-a-clock.md).  
  
## <a name="see-also"></a>Viz také  
 [Animace vlastnosti pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)  
 [Animace vlastnosti bez pomoci scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)  
 [Přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
