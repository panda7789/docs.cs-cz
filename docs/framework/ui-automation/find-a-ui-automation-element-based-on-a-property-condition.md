---
title: "Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
caps.latest.revision: "19"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: cafd84ce3acea80905d686f33f23338e3581a9c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="bf90f-102">Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost</span><span class="sxs-lookup"><span data-stu-id="bf90f-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="bf90f-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="bf90f-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bf90f-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="bf90f-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="bf90f-105">Toto téma obsahuje ukázkový kód, který ukazuje, jak najít prvek v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu podle určitou vlastnost nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bf90f-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf90f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf90f-106">Example</span></span>  
 <span data-ttu-id="bf90f-107">V následujícím příkladu sadu podmínek vlastností jsou určené, identifikovat určité elementu (nebo elementy) zájmu v <xref:System.Windows.Automation.AutomationElement> stromu.</span><span class="sxs-lookup"><span data-stu-id="bf90f-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="bf90f-108">Vyhledejte všechny odpovídající elementy se pak provádí pomocí <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metoda, která zahrnuje řadu <xref:System.Windows.Automation.AndCondition> logických operací omezit počet elementů odpovídající.</span><span class="sxs-lookup"><span data-stu-id="bf90f-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf90f-109">Při hledání z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, pokuste se získat jen přímé podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="bf90f-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="bf90f-110">Vyhledejte následníky může iterovat stovky nebo dokonce tisíce elementy, což může způsobit k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bf90f-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="bf90f-111">Pokud se pokoušíte získat konkrétní element na nižší úrovni, měli byste začít vyhledávání z okna aplikace nebo z kontejneru na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="bf90f-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="bf90f-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf90f-112">See Also</span></span>  
 [<span data-ttu-id="bf90f-113">Vlastnost InvokePattern a ukázkové položky nabídky ExpandCollapsePattern</span><span class="sxs-lookup"><span data-stu-id="bf90f-113">InvokePattern and ExpandCollapsePattern Menu Item Sample</span></span>](http://msdn.microsoft.com/en-us/b7fa141c-e2d1-4da2-a27f-81a7d1172210)  
 [<span data-ttu-id="bf90f-114">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bf90f-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)  
 [<span data-ttu-id="bf90f-115">Používání vlastnosti AutomationID</span><span class="sxs-lookup"><span data-stu-id="bf90f-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
