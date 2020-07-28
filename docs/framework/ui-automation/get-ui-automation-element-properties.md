---
title: Získání vlastností elementů automatizace uživatelského rozhraní
description: Viz pokyny a příklad, který ukazuje, jak načíst aktuální vlastnosti nebo vlastnosti uložené v mezipaměti prvku automatizace uživatelského rozhraní.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- properties, retrieving
- UI Automation, retrieving properties of elements
ms.assetid: 09576b1a-291f-435c-980e-dee32d899ae1
ms.openlocfilehash: 277822c9d89046bfbad50df16bce83da7dd45b3b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164112"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="f4674-103">Získání vlastností elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4674-103">Get UI Automation Element Properties</span></span>
> [!NOTE]
> <span data-ttu-id="f4674-104">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="f4674-104">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="f4674-105">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="f4674-105">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="f4674-106">Toto téma ukazuje, jak načíst vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] prvku.</span><span class="sxs-lookup"><span data-stu-id="f4674-106">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="f4674-107">Získat aktuální hodnotu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f4674-107">Get a Current Property Value</span></span>  
  
1. <span data-ttu-id="f4674-108">Získejte, <xref:System.Windows.Automation.AutomationElement> jehož vlastnost se má získat.</span><span class="sxs-lookup"><span data-stu-id="f4674-108">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2. <span data-ttu-id="f4674-109">Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A> nebo načtěte <xref:System.Windows.Automation.AutomationElement.Current%2A> strukturu vlastností a získejte hodnotu od jednoho z jejích členů.</span><span class="sxs-lookup"><span data-stu-id="f4674-109">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="f4674-110">Získat hodnotu vlastnosti uložené v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="f4674-110">Get a Cached Property Value</span></span>  
  
1. <span data-ttu-id="f4674-111">Získejte, <xref:System.Windows.Automation.AutomationElement> jehož vlastnost se má získat.</span><span class="sxs-lookup"><span data-stu-id="f4674-111">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="f4674-112">Vlastnost musí být zadána v <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="f4674-112">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="f4674-113">Zavolejte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtěte <xref:System.Windows.Automation.AutomationElement.Cached%2A> strukturu vlastností a získejte hodnotu od jednoho z jejích členů.</span><span class="sxs-lookup"><span data-stu-id="f4674-113">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f4674-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f4674-114">Example</span></span>  
 <span data-ttu-id="f4674-115">Následující příklad ukazuje různé způsoby, jak načíst aktuální vlastnosti <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="f4674-115">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="f4674-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="f4674-116">See also</span></span>

- [<span data-ttu-id="f4674-117">Vlastnosti automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="f4674-117">UI Automation Properties for Clients</span></span>](ui-automation-properties-for-clients.md)
- [<span data-ttu-id="f4674-118">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4674-118">Use Caching in UI Automation</span></span>](use-caching-in-ui-automation.md)
- [<span data-ttu-id="f4674-119">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="f4674-119">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
