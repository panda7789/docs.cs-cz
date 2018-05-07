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
ms.openlocfilehash: 18f8fb4edf5f71904335180e43dd65bd9910bdef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-a-property-without-using-a-storyboard"></a>Postupy: Animace vlastnosti bez pomoci scénáře
Tento příklad ukazuje jeden ze způsobů použití animace do vlastnosti bez použití <xref:System.Windows.Media.Animation.Storyboard>.  
  
> [!NOTE]
>  Tato funkce není k dispozici v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. Informace o animaci na vlastnost ve [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], najdete v části [animace vlastnost pomocí scénáře](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md).  
  
 Chcete-li použít místní animace do vlastnosti, použijte <xref:System.Windows.UIElement.BeginAnimation%2A> metoda. Tato metoda přebírá dva parametry: <xref:System.Windows.DependencyProperty> určující vlastností pro animaci a animace chcete použít pro tuto vlastnost.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak animace barva šířky a pozadí <xref:System.Windows.Controls.Button>.  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
 Různé třídy animace v <xref:System.Windows.Media.Animation> obor názvů existuje pro různé typy vlastností animace. Další informace o animaci vlastnosti najdete v tématu [animace přehled](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md). Další informace o vlastnostech závislostí (typ vlastnosti, které jsou zobrazeny v těchto příkladech) a jejich funkce najdete v tématu [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
 Jiné způsoby animace bez použití <xref:System.Windows.Media.Animation.Storyboard> objekty; Další informace najdete v tématu [vlastnost animace techniky přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Animation.AnimationTimeline>  
 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>  
 <xref:System.Windows.Media.Animation>  
 <xref:System.Windows.Media.Animation.Storyboard>  
 [Přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
