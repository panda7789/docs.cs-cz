---
title: "Postupy: Spuštění animace při změně hodnoty vlastnosti"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4d722be0f0367f7e6e98ef1c8451ce58ee28fedd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a>Postupy: Spuštění animace při změně hodnoty vlastnosti
Tento příklad ukazuje, jak používat <xref:System.Windows.Trigger> zahájíte <xref:System.Windows.Media.Animation.Storyboard> při změně hodnoty vlastnosti. Můžete použít <xref:System.Windows.Trigger> uvnitř <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, nebo <xref:System.Windows.DataTemplate>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Trigger> pro animaci <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> při jeho <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost stane `true`.  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 Použité vlastností animace <xref:System.Windows.Trigger> objekty chovat způsobem složitější než <xref:System.Windows.EventTrigger> animací nebo animace spuštěna pomocí <xref:System.Windows.Media.Animation.Storyboard> metody.  Jejich "aby handoff" animací definované jiná <xref:System.Windows.Trigger> objekty, ale tvoří s <xref:System.Windows.EventTrigger> a metoda aktivované animace.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Trigger>  
 [Vlastnost animace techniky – přehled](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Přehled scénářů](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
