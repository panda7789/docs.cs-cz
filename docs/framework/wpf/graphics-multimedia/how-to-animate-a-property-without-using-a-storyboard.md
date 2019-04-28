---
title: 'Postupy: Animace vlastnosti bez pomoci scénáře'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- non-Storyboard animation
- local animation [WPF]
- animation [WPF], non-Storyboard (local)
ms.assetid: d411db70-4df7-487d-82bc-95a7c1b2e7f8
ms.openlocfilehash: 93609cdeb4d879cbec0f90096e4fa2c131a2ec5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61761283"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Postupy: Animace vlastnosti bez pomoci scénáře
Tento příklad ukazuje jeden ze způsobů použití animace vlastnosti bez použití <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
>  Tato funkce není k dispozici v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Informace o animování vlastnosti v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], naleznete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Chcete-li použít místní animace na vlastnost, použijte <xref:System.Windows.UIElement.BeginAnimation%2A> metody. Tato metoda přebírá dva parametry: <xref:System.Windows.DependencyProperty> , který určuje vlastnost, která má animace a animace, který chcete použít pro tuto vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak animovat barva šířku a na pozadí <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Různé třídy animace v <xref:System.Windows.Media.Animation> oboru názvů existuje pro různé typy vlastností animace. Další informace o animace vlastností najdete v tématu [přehled animace](animation-overview.md). Další informace o vlastnosti závislosti (typ vlastnosti, které jsou uvedeny v těchto příkladech) a jejich funkcích najdete v části [přehled vlastností závislosti](../advanced/dependency-properties-overview.md).  
  
 Existují jiné způsoby, jak animovat bez použití <xref:System.Windows.Media.Animation.Storyboard> objekty; Další informace najdete v tématu [přehled způsobů animace vlastností](property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Přehled způsobů animace vlastností](property-animation-techniques-overview.md)
- [Přehled animace](animation-overview.md)
