---
title: Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: 7b194d9430f27fb85723a91f5786ed11a60bfa85
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040983"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="10215-102">Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="10215-102">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="10215-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="10215-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="10215-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="10215-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="10215-105">Toto téma ukazuje, jak načíst objekty vzoru ovládacího prvku [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] z prvků.</span><span class="sxs-lookup"><span data-stu-id="10215-105">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="10215-106">Získání všech vzorů ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="10215-106">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="10215-107">Získejte, <xref:System.Windows.Automation.AutomationElement> na jejichž řídicích vzorech vás zajímáte.</span><span class="sxs-lookup"><span data-stu-id="10215-107">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="10215-108">Volání <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pro získání všech vzorů ovládacích prvků z elementu.</span><span class="sxs-lookup"><span data-stu-id="10215-108">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="10215-109">Důrazně doporučujeme, aby klient nepoužíval <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span><span class="sxs-lookup"><span data-stu-id="10215-109">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="10215-110">Výkon může být vážně ovlivněn, protože tato metoda volá <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> interně pro každý existující vzor ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10215-110">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="10215-111">Pokud je to možné, klient by <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> měl volat pro klíčové vzory zájmu.</span><span class="sxs-lookup"><span data-stu-id="10215-111">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="10215-112">Získání konkrétního vzoru ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="10215-112">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="10215-113">Získejte, <xref:System.Windows.Automation.AutomationElement> na jejichž řídicích vzorech vás zajímáte.</span><span class="sxs-lookup"><span data-stu-id="10215-113">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="10215-114">Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> k dotazování na konkrétní vzor.</span><span class="sxs-lookup"><span data-stu-id="10215-114">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="10215-115">Tyto metody jsou podobné, ale pokud se vzor nenajde, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> vyvolá výjimku a <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="10215-115">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10215-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="10215-116">Example</span></span>  
 <span data-ttu-id="10215-117">Následující příklad načte <xref:System.Windows.Automation.AutomationElement> pro položku seznamu a získá <xref:System.Windows.Automation.SelectionItemPattern> z tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="10215-117">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="10215-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10215-118">See also</span></span>

- [<span data-ttu-id="10215-119">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="10215-119">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)
