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
ms.openlocfilehash: 10ab202bd4b4c69a443a51aab96e184699ca3d81
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552889"
---
# <a name="get-ui-automation-element-properties"></a><span data-ttu-id="29500-102">Získání vlastností elementů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="29500-102">Get UI Automation Element Properties</span></span>
> [!NOTE]
>  <span data-ttu-id="29500-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="29500-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="29500-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: Automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="29500-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="29500-105">Toto téma ukazuje, jak načíst vlastnosti [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] elementu.</span><span class="sxs-lookup"><span data-stu-id="29500-105">This topic shows how to retrieve properties of a [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] element.</span></span>  
  
### <a name="get-a-current-property-value"></a><span data-ttu-id="29500-106">Získat aktuální hodnotu vlastnosti</span><span class="sxs-lookup"><span data-stu-id="29500-106">Get a Current Property Value</span></span>  
  
1.  <span data-ttu-id="29500-107">Získat <xref:System.Windows.Automation.AutomationElement> jehož vlastnosti chcete získat.</span><span class="sxs-lookup"><span data-stu-id="29500-107">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span>  
  
2.  <span data-ttu-id="29500-108">Volání <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, nebo načíst <xref:System.Windows.Automation.AutomationElement.Current%2A> vlastnost strukturu a získat hodnotu z jednoho z jejích členů.</span><span class="sxs-lookup"><span data-stu-id="29500-108">Call <xref:System.Windows.Automation.AutomationElement.GetCurrentPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Current%2A> property structure and get the value from one of its members.</span></span>  
  
### <a name="get-a-cached-property-value"></a><span data-ttu-id="29500-109">Získat hodnotu vlastnosti uložené v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="29500-109">Get a Cached Property Value</span></span>  
  
1.  <span data-ttu-id="29500-110">Získat <xref:System.Windows.Automation.AutomationElement> jehož vlastnosti chcete získat.</span><span class="sxs-lookup"><span data-stu-id="29500-110">Obtain the <xref:System.Windows.Automation.AutomationElement> whose property you wish to get.</span></span> <span data-ttu-id="29500-111">Vlastnost musí byl zadán v <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="29500-111">The property must have been specified in the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="29500-112">Volání <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, nebo načíst <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastnost strukturu a získat hodnotu z jednoho z jejích členů.</span><span class="sxs-lookup"><span data-stu-id="29500-112">Call <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A>, or retrieve the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property structure and get the value from one of its members.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29500-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="29500-113">Example</span></span>  
 <span data-ttu-id="29500-114">Následující příklad ukazuje různé způsoby, jak načíst aktuální vlastnosti <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="29500-114">The following example shows various ways to retrieve current properties of an <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
 [!code-csharp[UIAClient_snip#170](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#170)]
 [!code-vb[UIAClient_snip#170](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#170)]  
  
## <a name="see-also"></a><span data-ttu-id="29500-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="29500-115">See also</span></span>
- [<span data-ttu-id="29500-116">Vlastnosti automatizace uživatelského rozhraní pro klienty</span><span class="sxs-lookup"><span data-stu-id="29500-116">UI Automation Properties for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-properties-for-clients.md)
- [<span data-ttu-id="29500-117">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="29500-117">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)
- [<span data-ttu-id="29500-118">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="29500-118">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
