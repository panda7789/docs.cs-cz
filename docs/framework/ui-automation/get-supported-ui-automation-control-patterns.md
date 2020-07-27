---
title: Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní
description: Přečtěte si příklad, který ukazuje, jak načíst objekty řídicího vzoru z prvků automatizace uživatelského rozhraní.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control patterns, getting
- UI Automation, getting control patterns
- getting, control patterns
ms.assetid: 006c54c9-50bf-48d9-a855-9d62eb95603a
ms.openlocfilehash: f2905b81a1af2f86c78b082f0241e2181c384d25
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164160"
---
# <a name="get-supported-ui-automation-control-patterns"></a><span data-ttu-id="e4d5e-103">Získání podporovaných vzorů ovládacích prvků pro automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e4d5e-103">Get Supported UI Automation Control Patterns</span></span>
> [!NOTE]
> <span data-ttu-id="e4d5e-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e4d5e-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="e4d5e-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="e4d5e-106">Toto téma ukazuje, jak načíst objekty vzoru ovládacího prvku z [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvků.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-106">This topic shows how to retrieve control pattern objects from [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elements.</span></span>  
  
### <a name="obtain-all-control-patterns"></a><span data-ttu-id="e4d5e-107">Získání všech vzorů ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e4d5e-107">Obtain All Control Patterns</span></span>  
  
1. <span data-ttu-id="e4d5e-108">Získejte, na <xref:System.Windows.Automation.AutomationElement> jejichž řídicích vzorech vás zajímáte.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-108">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="e4d5e-109">Volání <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> pro získání všech vzorů ovládacích prvků z elementu.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-109">Call <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> to get all control patterns from the element.</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="e4d5e-110">Důrazně doporučujeme, aby klient nepoužíval <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A> .</span><span class="sxs-lookup"><span data-stu-id="e4d5e-110">It is strongly recommended that a client not use <xref:System.Windows.Automation.AutomationElement.GetSupportedPatterns%2A>.</span></span> <span data-ttu-id="e4d5e-111">Výkon může být vážně ovlivněn, protože tato metoda volá <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> interně pro každý existující vzor ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-111">Performance can be severely affected as this method calls <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> internally for each existing control pattern.</span></span> <span data-ttu-id="e4d5e-112">Pokud je to možné, klient by měl volat <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> pro klíčové vzory zájmu.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-112">If possible, a client should call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> for the key patterns of interest.</span></span>  
  
### <a name="obtain-a-specific-control-pattern"></a><span data-ttu-id="e4d5e-113">Získání konkrétního vzoru ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e4d5e-113">Obtain a Specific Control Pattern</span></span>  
  
1. <span data-ttu-id="e4d5e-114">Získejte, na <xref:System.Windows.Automation.AutomationElement> jejichž řídicích vzorech vás zajímáte.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-114">Get the <xref:System.Windows.Automation.AutomationElement> whose control patterns you are interested in.</span></span>  
  
2. <span data-ttu-id="e4d5e-115">Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> k dotazování na konkrétní vzor.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-115">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> to query for a specific pattern.</span></span> <span data-ttu-id="e4d5e-116">Tyto metody jsou podobné, ale pokud se vzor nenajde, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> vyvolá výjimku a <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> vrátí `false` .</span><span class="sxs-lookup"><span data-stu-id="e4d5e-116">These methods are similar, but if the pattern is not found, <xref:System.Windows.Automation.AutomationElement.GetCurrentPattern%2A> raises an exception, and <xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A> returns `false`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4d5e-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="e4d5e-117">Example</span></span>  
 <span data-ttu-id="e4d5e-118">Následující příklad načte <xref:System.Windows.Automation.AutomationElement> pro položku seznamu a získá <xref:System.Windows.Automation.SelectionItemPattern> z tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="e4d5e-118">The following example retrieves an <xref:System.Windows.Automation.AutomationElement> for a list item and obtains a <xref:System.Windows.Automation.SelectionItemPattern> from that element.</span></span>  
  
 [!code-csharp[UIAClient_snip#103](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#103)]
 [!code-vb[UIAClient_snip#103](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#103)]  
  
## <a name="see-also"></a><span data-ttu-id="e4d5e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4d5e-119">See also</span></span>

- [<span data-ttu-id="e4d5e-120">Vzory ovládacích prvků automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="e4d5e-120">UI Automation Control Patterns for Clients</span></span>](ui-automation-control-patterns-for-clients.md)
