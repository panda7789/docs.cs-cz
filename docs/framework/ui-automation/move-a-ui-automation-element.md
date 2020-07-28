---
title: Přesunutí elementu automatizace uživatelského rozhraní
description: Viz vzorový kód, který ukazuje, jak přesunout prvek automatizace uživatelského rozhraní do zadaného umístění obrazovky. Používá vzory ovládacích prvků třídu WindowPattern a TransformPattern.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- moving elements
- elements, moving
- UI Automation, moving elements
ms.assetid: 4042cb44-e27e-4a03-ac36-9be1eed65b47
ms.openlocfilehash: 4c8bec4e6d7a241588a3ab261cb80ce9ac242024
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166153"
---
# <a name="move-a-ui-automation-element"></a><span data-ttu-id="dd8ea-104">Přesunutí elementu automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="dd8ea-104">Move a UI Automation Element</span></span>
> [!NOTE]
> <span data-ttu-id="dd8ea-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="dd8ea-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="dd8ea-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="dd8ea-107">Tento příklad ukazuje, jak přesunout [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvek do zadaného umístění obrazovky.</span><span class="sxs-lookup"><span data-stu-id="dd8ea-107">This example demonstrates how to move a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element to a specified screen location.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd8ea-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd8ea-108">Example</span></span>  
 <span data-ttu-id="dd8ea-109">Následující příklad používá <xref:System.Windows.Automation.WindowPattern> <xref:System.Windows.Automation.TransformPattern> vzory ovládacích prvků a k programovému přesunutí cílové aplikace Win32 do diskrétního umístění obrazovky a sledování <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent> .</span><span class="sxs-lookup"><span data-stu-id="dd8ea-109">The following example uses the <xref:System.Windows.Automation.WindowPattern> and <xref:System.Windows.Automation.TransformPattern> control patterns to programmatically move a Win32 target application to discrete screen locations and track the <xref:System.Windows.Automation.AutomationElement.BoundingRectangleProperty> <xref:System.Windows.Automation.AutomationElement.AutomationPropertyChangedEvent>.</span></span>  
  
 [!code-csharp[WindowMove#1301](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1301)]
 [!code-vb[WindowMove#1301](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1301)]  
[!code-csharp[WindowMove#1300](../../../samples/snippets/csharp/VS_Snippets_Wpf/WindowMove/CSharp/WindowMove.cs#1300)]
[!code-vb[WindowMove#1300](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WindowMove/VisualBasic/windowmove.vb#1300)]  
  
## <a name="see-also"></a><span data-ttu-id="dd8ea-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd8ea-110">See also</span></span>

- [<span data-ttu-id="dd8ea-111">Ukázka třídu WindowPattern</span><span class="sxs-lookup"><span data-stu-id="dd8ea-111">WindowPattern Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Accessibility/WindowMove)
