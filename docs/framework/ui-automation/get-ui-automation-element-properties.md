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
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 73678433692f5532f712f0d2c7a3c5bf138a87b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33405574"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="e8fd7-102">Získání vlastností elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8fd7-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="e8fd7-103">Tato dokumentace je určena pro rozhraní .NET Framework vývojáře, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="e8fd7-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="e8fd7-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], najdete v části [rozhraní API systému Windows automatizace: automatizace uživatelského rozhraní](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="e8fd7-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="e8fd7-105">Toto téma ukazuje, jak načíst vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="e8fd7-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="e8fd7-106">Získat aktuální hodnota vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e8fd7-106">Get a Current Property Value</span></span>  
  
1.  <span data-ttu-id="e8fd7-107">Získat <xref:System.Windows.Automation.AutomationElement> jehož vlastnosti chcete získat.</span><span class="sxs-lookup"><span data-stu-id="e8fd7-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2.  <span data-ttu-id="e8fd7-108">Volání <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, nebo načíst <xref:System.Windows.Automation.AutomationElement.Current%2A> vlastnost struktura a získat hodnotu z jednoho ze svých členů.</span><span class="sxs-lookup"><span data-stu-id="e8fd7-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="e8fd7-109">Získat hodnotu vlastnosti uloženou v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="e8fd7-109">Get a Cached Property Value</span></span>  
  
1.  <span data-ttu-id="e8fd7-110">Získat <xref:System.Windows.Automation.AutomationElement> jehož vlastnosti chcete získat.</span><span class="sxs-lookup"><span data-stu-id="e8fd7-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="e8fd7-111">Tato vlastnost musí byla zadaná v <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="e8fd7-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="e8fd7-112">Volání <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, nebo načíst <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastnost struktura a získat hodnotu z jednoho ze svých členů.</span><span class="sxs-lookup"><span data-stu-id="e8fd7-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8fd7-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8fd7-113">Example</span></span>  
 <span data-ttu-id="e8fd7-114">Následující příklad ukazuje různé způsoby, jak načíst aktuální vlastnosti <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="e8fd7-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="e8fd7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8fd7-115">See Also</span></span>  
 [<span data-ttu-id="e8fd7-116">Vlastnosti automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="e8fd7-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)  
 [<span data-ttu-id="e8fd7-117">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8fd7-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)  
 [<span data-ttu-id="e8fd7-118">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="e8fd7-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
