---
title: 'Postupy: Animace vlastnosti pomocí AnimationClock'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- animation [WPF], properties [WPF], with AnimationClocks
- AnimationClocks [WPF]
ms.assetid: e6542021-714c-4675-9567-04f1c7380834
ms.openlocfilehash: d93f1eb352aef4f5e74512a8deeb0ec3fe7943c0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57357180"
---
# <a name="how-to-animate-a-property-by-using-an-animationclock"></a>Postupy: Animace vlastnosti pomocí AnimationClock
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.Animation.Clock> objekty animovat vlastnost.  
  
 Existují tři způsoby, jak animovat vlastnost závislosti:  
  
-   Vytvoření <xref:System.Windows.Media.Animation.AnimationTimeline> a přidružte jej k vlastnosti pomocí <xref:System.Windows.Media.Animation.Storyboard>.  
  
-   Použití objektu <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> způsob, jak použít jediné <xref:System.Windows.Media.Animation.AnimationTimeline> cílové vlastnosti.  
  
-   Vytvoření <xref:System.Windows.Media.Animation.AnimationClock> ze <xref:System.Windows.Media.Animation.AnimationTimeline> a použít ji pro vlastnost.  
  
 <xref:System.Windows.Media.Animation.Storyboard> objekty a <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody umožňují animace vlastnosti bez přímo vytváření a distribuci hodiny (příklady najdete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md) a [animace vlastnosti bez Scénáře použití](how-to-animate-a-property-without-using-a-storyboard.md)); hodiny se vytvořila a distribuovala za vás automaticky.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Media.Animation.AnimationClock> a použít ji pro dvě podobné vlastnosti.  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](~/samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 Příklad ukazuje, jak interaktivní řízení <xref:System.Windows.Media.Animation.Clock> po jeho spuštění, naleznete v tématu [interaktivní řízení hodin](how-to-interactively-control-a-clock.md).  
  
## <a name="see-also"></a>Viz také:
- [Animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md)
- [Animace vlastnosti bez pomoci scénáře](how-to-animate-a-property-without-using-a-storyboard.md)
- [Přehled způsobů animace vlastností](property-animation-techniques-overview.md)
