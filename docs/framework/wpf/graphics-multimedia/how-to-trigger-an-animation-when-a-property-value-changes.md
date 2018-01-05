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
ms.workload: dotnet
ms.openlocfilehash: 0eb4542d8baf86f01417eb1925028a00471b40b5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="da8a6-102">Postupy: Spuštění animace při změně hodnoty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="da8a6-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="da8a6-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Trigger> zahájíte <xref:System.Windows.Media.Animation.Storyboard> při změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="da8a6-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="da8a6-104">Můžete použít <xref:System.Windows.Trigger> uvnitř <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, nebo <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="da8a6-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="da8a6-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="da8a6-105">Example</span></span>  
 <span data-ttu-id="da8a6-106">Následující příklad používá <xref:System.Windows.Trigger> pro animaci <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> při jeho <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost stane `true`.</span><span class="sxs-lookup"><span data-stu-id="da8a6-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="da8a6-107">Použité vlastností animace <xref:System.Windows.Trigger> objekty chovat způsobem složitější než <xref:System.Windows.EventTrigger> animací nebo animace spuštěna pomocí <xref:System.Windows.Media.Animation.Storyboard> metody.</span><span class="sxs-lookup"><span data-stu-id="da8a6-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="da8a6-108">Jejich "aby handoff" animací definované jiná <xref:System.Windows.Trigger> objekty, ale tvoří s <xref:System.Windows.EventTrigger> a metoda aktivované animace.</span><span class="sxs-lookup"><span data-stu-id="da8a6-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da8a6-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="da8a6-109">See Also</span></span>  
 <xref:System.Windows.Trigger>  
 [<span data-ttu-id="da8a6-110">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="da8a6-110">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="da8a6-111">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="da8a6-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
