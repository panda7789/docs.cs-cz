---
title: 'Postupy: Spuštění animace při změně hodnoty vlastnosti'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 2be85a9ae93d504d98930468ad2e257385e835f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54705294"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Postupy: Spuštění animace při změně hodnoty vlastnosti
Tento příklad ukazuje způsob použití <xref:System.Windows.Trigger> spustit <xref:System.Windows.Media.Animation.Storyboard> při změně hodnoty vlastnosti. Můžete použít <xref:System.Windows.Trigger> uvnitř <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, nebo <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Trigger> pro animaci <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> při jeho <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost se stane `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Animace použít vlastností <xref:System.Windows.Trigger> objekty se chovají způsobem složitější než <xref:System.Windows.EventTrigger> animace nebo animace spuštěna pomocí <xref:System.Windows.Media.Animation.Storyboard> metody.  Jsou "předání" s použitím animací definované jinými <xref:System.Windows.Trigger> objekty, ale compose s <xref:System.Windows.EventTrigger> a aktivaci metody animace.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Trigger>
- [Přehled způsobů animace vlastností](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)
- [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
