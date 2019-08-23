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
ms.openlocfilehash: 71711c0392576930e97986078ec5926ff6ca9813
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963010"
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Postupy: Animace vlastnosti bez pomoci scénáře
Tento příklad ukazuje jeden způsob, jak použít animaci na vlastnost bez použití <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
> Tato funkce není k dispozici [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]v. Informace o animování vlastnosti v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]naleznete v tématu [animace vlastnosti pomocí scénáře](how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Chcete-li použít místní animaci na vlastnost, použijte <xref:System.Windows.UIElement.BeginAnimation%2A> metodu. Tato metoda používá dva parametry: a <xref:System.Windows.DependencyProperty> , který určuje vlastnost, která má být animována, a animaci, která má být použita pro tuto vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak animovat šířku a barvu <xref:System.Windows.Controls.Button>pozadí.  
  
 [!code-cpp[animateproperty#11](~/samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](~/samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Různé třídy animace v <xref:System.Windows.Media.Animation> oboru názvů existují pro animování různých typů vlastností. Další informace o animování vlastností najdete v tématu [Přehled animací](animation-overview.md). Další informace o vlastnostech závislosti (typu vlastností, které jsou uvedeny v těchto příkladech) a jejich funkcích naleznete v tématu [Přehled vlastností závislosti](../advanced/dependency-properties-overview.md).  
  
 Existují i jiné způsoby, jak animovat bez <xref:System.Windows.Media.Animation.Storyboard> použití objektů; další informace naleznete v tématu [Přehled postupů animace vlastností](property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.Animation.AnimationTimeline>
- <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>
- <xref:System.Windows.Media.Animation>
- <xref:System.Windows.Media.Animation.Storyboard>
- [Přehled způsobů animace vlastností](property-animation-techniques-overview.md)
- [Přehled animace](animation-overview.md)
