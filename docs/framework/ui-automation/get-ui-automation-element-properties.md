---
title: Získání vlastností elementů automatizace uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 1b82302ff89d2e8407871cbfba6c10e8322ac4e7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74435495"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="bb630-102">Získání vlastností elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb630-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="bb630-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="bb630-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="bb630-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="bb630-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="bb630-105">Toto téma ukazuje, jak načíst vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]ho prvku.</span><span class="sxs-lookup"><span data-stu-id="bb630-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="bb630-106">Získat aktuální hodnotu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="bb630-106">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="bb630-107">Získejte <xref:System.Windows.Automation.AutomationElement>, jehož vlastnost se má získat.</span><span class="sxs-lookup"><span data-stu-id="bb630-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="bb630-108">Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>nebo načtěte strukturu vlastností <xref:System.Windows.Automation.AutomationElement.Current%2A> a získejte hodnotu z jednoho z jejích členů.</span><span class="sxs-lookup"><span data-stu-id="bb630-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="bb630-109">Získat hodnotu vlastnosti uložené v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="bb630-109">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="bb630-110">Získejte <xref:System.Windows.Automation.AutomationElement>, jehož vlastnost se má získat.</span><span class="sxs-lookup"><span data-stu-id="bb630-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="bb630-111">Vlastnost musí být zadána v <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="bb630-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="bb630-112">Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>nebo načtěte strukturu vlastností <xref:System.Windows.Automation.AutomationElement.Cached%2A> a získejte hodnotu z jednoho z jejích členů.</span><span class="sxs-lookup"><span data-stu-id="bb630-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb630-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb630-113">Example</span></span>  
 <span data-ttu-id="bb630-114">Následující příklad ukazuje různé způsoby načtení aktuálních vlastností <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="bb630-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="bb630-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bb630-115">See also</span></span>

- [<span data-ttu-id="bb630-116">Vlastnosti automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="bb630-116">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="bb630-117">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb630-117">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="bb630-118">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="bb630-118">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
