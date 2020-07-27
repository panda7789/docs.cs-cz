---
title: Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost
description: Vyhledejte prvek automatizace uživatelského rozhraní na základě podmínky vlastnosti. Vyhledejte prvek v rámci stromu automatizace uživatelského rozhraní na základě konkrétní vlastnosti nebo vlastností.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 5e5fa4fde9049bd87b2722fa9b7d084d96ff6f42
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168435"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="765a3-104">Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost</span><span class="sxs-lookup"><span data-stu-id="765a3-104">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="765a3-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="765a3-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="765a3-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="765a3-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="765a3-107">Toto téma obsahuje příklad kódu, který ukazuje, jak najít prvek v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu na základě konkrétní vlastnosti nebo vlastností.</span><span class="sxs-lookup"><span data-stu-id="765a3-107">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="765a3-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="765a3-108">Example</span></span>  
 <span data-ttu-id="765a3-109">V následujícím příkladu jsou zadány sady podmínek vlastností, které identifikují určitý prvek (nebo prvky) v zájmu <xref:System.Windows.Automation.AutomationElement> stromu.</span><span class="sxs-lookup"><span data-stu-id="765a3-109">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="765a3-110">Hledání všech vyhovujících prvků je následně provedeno s <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metodou, která zahrnuje řadu <xref:System.Windows.Automation.AndCondition> logických operací pro omezení počtu vyhovujících prvků.</span><span class="sxs-lookup"><span data-stu-id="765a3-110">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="765a3-111">Při hledání z nástroje <xref:System.Windows.Automation.AutomationElement.RootElement%2A> byste měli zkusit získat pouze přímé podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="765a3-111">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="765a3-112">Hledání potomků může iterovat stovky nebo dokonce tisíce prvků, což může způsobit přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="765a3-112">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="765a3-113">Pokud se pokoušíte získat konkrétní prvek na nižší úrovni, měli byste zahájit hledání z okna aplikace nebo z kontejneru na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="765a3-113">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="765a3-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="765a3-114">See also</span></span>

- <span data-ttu-id="765a3-115">[Ukázka položky nabídky InvokePattern a ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="765a3-115">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="765a3-116">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="765a3-116">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="765a3-117">Používání vlastnosti AutomationID</span><span class="sxs-lookup"><span data-stu-id="765a3-117">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
