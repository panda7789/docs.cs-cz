---
title: 'Postupy: Spuštění animace při změně hodnoty vlastnosti'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], starting when property values change
- triggering animation [WPF]
- Storyboards [WPF], starting when property values change
ms.assetid: 12399c21-0300-4f4f-9e3a-d92d9907e5f5
ms.openlocfilehash: 7e3eecedf7d464eeb8e4f60f2f05fa06d2e23e09
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769301"
---
# <a name="how-to-trigger-an-animation-when-a-property-value-changes"></a><span data-ttu-id="e5b39-102">Postupy: Spuštění animace při změně hodnoty vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e5b39-102">How to: Trigger an Animation When a Property Value Changes</span></span>
<span data-ttu-id="e5b39-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Trigger> spustit <xref:System.Windows.Media.Animation.Storyboard> při změně hodnoty vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e5b39-103">This example shows how to use a <xref:System.Windows.Trigger> to start a <xref:System.Windows.Media.Animation.Storyboard> when a property value changes.</span></span> <span data-ttu-id="e5b39-104">Můžete použít <xref:System.Windows.Trigger> uvnitř <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, nebo <xref:System.Windows.DataTemplate>.</span><span class="sxs-lookup"><span data-stu-id="e5b39-104">You can use a <xref:System.Windows.Trigger> inside a <xref:System.Windows.Style>, <xref:System.Windows.Controls.ControlTemplate>, or <xref:System.Windows.DataTemplate>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5b39-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5b39-105">Example</span></span>  
 <span data-ttu-id="e5b39-106">Následující příklad používá <xref:System.Windows.Trigger> pro animaci <xref:System.Windows.UIElement.Opacity%2A> z <xref:System.Windows.Controls.Button> při jeho <xref:System.Windows.UIElement.IsMouseOver%2A> vlastnost se stane `true`.</span><span class="sxs-lookup"><span data-stu-id="e5b39-106">The following example uses a <xref:System.Windows.Trigger> to animate the <xref:System.Windows.UIElement.Opacity%2A> of a <xref:System.Windows.Controls.Button> when its <xref:System.Windows.UIElement.IsMouseOver%2A> property becomes `true`.</span></span>  
  
 [!code-xaml[AnimatePropertyStoryboards#PropertyTriggerExample](~/samples/snippets/xaml/VS_Snippets_Wpf/AnimatePropertyStoryboards/XAML/PropertyTriggerExample.xaml#propertytriggerexample)]  
  
 <span data-ttu-id="e5b39-107">Animace použít vlastností <xref:System.Windows.Trigger> objekty se chovají způsobem složitější než <xref:System.Windows.EventTrigger> animace nebo animace spuštěna pomocí <xref:System.Windows.Media.Animation.Storyboard> metody.</span><span class="sxs-lookup"><span data-stu-id="e5b39-107">Animations applied by property <xref:System.Windows.Trigger> objects behave in a more complex fashion than <xref:System.Windows.EventTrigger> animations or animations started using <xref:System.Windows.Media.Animation.Storyboard> methods.</span></span>  <span data-ttu-id="e5b39-108">Jsou "předání" s použitím animací definované jinými <xref:System.Windows.Trigger> objekty, ale compose s <xref:System.Windows.EventTrigger> a aktivaci metody animace.</span><span class="sxs-lookup"><span data-stu-id="e5b39-108">They "handoff" with animations defined by other <xref:System.Windows.Trigger> objects, but compose with <xref:System.Windows.EventTrigger> and method-triggered animations.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5b39-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5b39-109">See also</span></span>

- <xref:System.Windows.Trigger>
- [<span data-ttu-id="e5b39-110">Přehled způsobů animace vlastností</span><span class="sxs-lookup"><span data-stu-id="e5b39-110">Property Animation Techniques Overview</span></span>](property-animation-techniques-overview.md)
- [<span data-ttu-id="e5b39-111">Přehled scénářů</span><span class="sxs-lookup"><span data-stu-id="e5b39-111">Storyboards Overview</span></span>](storyboards-overview.md)
