---
title: 'Postupy: Spuštění animace při změně hodnoty vlastnosti'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: f127f00445a587ee097faa6bed28e124690de10e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33561314"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="320fa-102">Postupy: Spuštění animace při změně hodnoty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="320fa-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="320fa-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Trigger> zahájíte <xref:System.Windows.Media.Animation.Storyboard> při změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="320fa-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="320fa-104">Můžete použít <xref:System.Windows.Trigger> uvnitř <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, nebo <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="320fa-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="320fa-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="320fa-105">Example</span></span>  
 <span data-ttu-id="320fa-106">Následující příklad používá <xref:System.Windows.Trigger> pro animaci <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> při jeho <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost stane `true`.</span><span class="sxs-lookup"><span data-stu-id="320fa-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="320fa-107">Použité vlastností animace <xref:System.Windows.Trigger> objekty chovat způsobem složitější než <xref:System.Windows.EventTrigger> animací nebo animace spuštěna pomocí <xref:System.Windows.Media.Animation.Storyboard> metody.</span><span class="sxs-lookup"><span data-stu-id="320fa-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="320fa-108">Jejich "aby handoff" animací definované jiná <xref:System.Windows.Trigger> objekty, ale tvoří s <xref:System.Windows.EventTrigger> a metoda aktivované animace.</span><span class="sxs-lookup"><span data-stu-id="320fa-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="320fa-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="320fa-109">See Also</span></span>  
 <xref:System.Windows.Trigger>  
 [<span data-ttu-id="320fa-110">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="320fa-110">Property Animation Techniques Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [<span data-ttu-id="320fa-111">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="320fa-111">Storyboards Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)
