---
title: Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements, finding by property conditions
- UI Automation, finding elements by property conditions
ms.assetid: 3acaee5a-6ce8-4c3e-81c8-67e59eb74477
ms.openlocfilehash: 3ca609551955b32ad8b63296975ce10f097d9c30
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433586"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="0c55b-102">Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost</span><span class="sxs-lookup"><span data-stu-id="0c55b-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
> <span data-ttu-id="0c55b-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="0c55b-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0c55b-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="0c55b-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0c55b-105">Toto téma obsahuje příklad kódu, který ukazuje, jak najít prvek v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromu na základě konkrétní vlastnosti nebo vlastností.</span><span class="sxs-lookup"><span data-stu-id="0c55b-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c55b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c55b-106">Example</span></span>  
 <span data-ttu-id="0c55b-107">V následujícím příkladu jsou zadány sady podmínek vlastností, které identifikují určitý prvek (nebo prvky) v zájmu <xref:System.Windows.Automation.AutomationElement> stromové struktuře.</span><span class="sxs-lookup"><span data-stu-id="0c55b-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="0c55b-108">Hledání všech vyhovujících prvků je následně provedeno pomocí metody <xref:System.Windows.Automation.AutomationElement.FindAll%2A>, která zahrnuje řadu <xref:System.Windows.Automation.AndCondition> logických operací pro omezení počtu vyhovujících prvků.</span><span class="sxs-lookup"><span data-stu-id="0c55b-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0c55b-109">Při hledání z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>byste se měli pokusit získat pouze přímé podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="0c55b-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="0c55b-110">Hledání potomků může iterovat stovky nebo dokonce tisíce prvků, což může způsobit přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="0c55b-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="0c55b-111">Pokud se pokoušíte získat konkrétní prvek na nižší úrovni, měli byste zahájit hledání z okna aplikace nebo z kontejneru na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="0c55b-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="0c55b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c55b-112">See also</span></span>

- <span data-ttu-id="0c55b-113">[Ukázka položky nabídky InvokePattern a ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="0c55b-113">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="0c55b-114">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0c55b-114">Obtaining UI Automation Elements</span></span>](obtaining-ui-automation-elements.md)
- [<span data-ttu-id="0c55b-115">Používání vlastnosti AutomationID</span><span class="sxs-lookup"><span data-stu-id="0c55b-115">Use the AutomationID Property</span></span>](use-the-automationid-property.md)
