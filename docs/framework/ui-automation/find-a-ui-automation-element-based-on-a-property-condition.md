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
ms.openlocfilehash: 83d3a36d08463cedf46c176208625e76907db2d8
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675105"
---
# <a name="find-a-ui-automation-element-based-on-a-property-condition"></a><span data-ttu-id="b8737-102">Hledání prvku automatizace uživatelského rozhraní na základě podmínky pro vlastnost</span><span class="sxs-lookup"><span data-stu-id="b8737-102">Find a UI Automation Element Based on a Property Condition</span></span>
> [!NOTE]
>  <span data-ttu-id="b8737-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="b8737-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="b8737-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="b8737-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="b8737-105">Toto téma obsahuje ukázkový kód, který ukazuje, jak vyhledat prvek v rámci [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] stromové struktury podle určitou vlastnost nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="b8737-105">This topic contains example code that shows how to locate an element within the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree based on a specific property or properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8737-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8737-106">Example</span></span>  
 <span data-ttu-id="b8737-107">V následujícím příkladu sadu podmínek vlastností jsou uvedeny, která určují určité elementu (nebo elementy), které vás zajímají v <xref:System.Windows.Automation.AutomationElement> stromu.</span><span class="sxs-lookup"><span data-stu-id="b8737-107">In the following example, a set of property conditions are specified that identify a certain element (or elements) of interest in the <xref:System.Windows.Automation.AutomationElement> tree.</span></span> <span data-ttu-id="b8737-108">Vyhledání všech odpovídajících prvků je pak provede s <xref:System.Windows.Automation.AutomationElement.FindAll%2A> metodu, která zahrnuje řadu <xref:System.Windows.Automation.AndCondition> logických operací omezit počet odpovídajících prvků.</span><span class="sxs-lookup"><span data-stu-id="b8737-108">A search for all matching elements is then performed with the <xref:System.Windows.Automation.AutomationElement.FindAll%2A> method that incorporates a series of <xref:System.Windows.Automation.AndCondition> boolean operations to limit the number of matching elements.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b8737-109">Při vyhledávání z <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, pokuste se získat přímé podřízené objekty.</span><span class="sxs-lookup"><span data-stu-id="b8737-109">When searching from the <xref:System.Windows.Automation.AutomationElement.RootElement%2A>, you should try to obtain only direct children.</span></span> <span data-ttu-id="b8737-110">Vyhledání potomků může iterovat stovky nebo i tisíce elementů, což může vést k přetečení zásobníku.</span><span class="sxs-lookup"><span data-stu-id="b8737-110">A search for descendants might iterate through hundreds or even thousands of elements, possibly resulting in a stack overflow.</span></span> <span data-ttu-id="b8737-111">Pokud se pokoušíte získat konkrétní elementu na nižší úrovni, měli byste začít hledání v okně aplikace nebo z kontejneru na nižší úrovni.</span><span class="sxs-lookup"><span data-stu-id="b8737-111">If you are attempting to obtain a specific element at a lower level, you should start your search from the application window or from a container at a lower level.</span></span>  
  
 [!code-csharp[InvokePatternApp#1100](../../../samples/snippets/csharp/VS_Snippets_Wpf/InvokePatternApp/CSharp/InvokePatternApp.cs#1100)]
 [!code-vb[InvokePatternApp#1100](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InvokePatternApp/VisualBasic/Client.vb#1100)]  
  
## <a name="see-also"></a><span data-ttu-id="b8737-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8737-112">See also</span></span>
- <span data-ttu-id="b8737-113">[Vlastnost InvokePattern a ukázkové položky nabídky ExpandCollapsePattern](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="b8737-113">[InvokePattern and ExpandCollapsePattern Menu Item Sample](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms771636(v=vs.90))</span></span>
- [<span data-ttu-id="b8737-114">Získání elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="b8737-114">Obtaining UI Automation Elements</span></span>](../../../docs/framework/ui-automation/obtaining-ui-automation-elements.md)
- [<span data-ttu-id="b8737-115">Používání vlastnosti AutomationID</span><span class="sxs-lookup"><span data-stu-id="b8737-115">Use the AutomationID Property</span></span>](../../../docs/framework/ui-automation/use-the-automationid-property.md)
