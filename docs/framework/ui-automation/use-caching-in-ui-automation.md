---
title: Použití mezipaměti při automatizaci uživatelského rozhraní
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 8f948f95250b078d5af90506359a3b92f9c85601
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/31/2018
ms.locfileid: "43331912"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="61265-102">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="61265-102">Use Caching in UI Automation</span></span>
> [!NOTE]
>  <span data-ttu-id="61265-103">Tato dokumentace je určená pro vývojáře rozhraní .NET Framework, kteří chtějí používat spravovanou [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tříd definovaných v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="61265-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="61265-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], naleznete v tématu [Windows Automation API: automatizace uživatelského rozhraní](https://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="61265-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="61265-105">Tato část ukazuje, jak implementovat ukládání do mezipaměti <xref:System.Windows.Automation.AutomationElement> vzory vlastností a ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="61265-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="61265-106">Aktivovat žádost o mezipaměti</span><span class="sxs-lookup"><span data-stu-id="61265-106">Activate a Cache Request</span></span>  
  
1.  <span data-ttu-id="61265-107">Vytvoření <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="61265-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2.  <span data-ttu-id="61265-108">Zadejte vlastnosti a vzorce do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="61265-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3.  <span data-ttu-id="61265-109">Zadejte rozsah ukládání do mezipaměti tak, že nastavíte <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="61265-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4.  <span data-ttu-id="61265-110">Určete zobrazení podstrom nastavením <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="61265-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5.  <span data-ttu-id="61265-111">Nastavte <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> vlastnost <xref:System.Windows.Automation.AutomationElementMode.None> Pokud chcete zvýšit efektivitu nenačítání úplný odkaz na objekty.</span><span class="sxs-lookup"><span data-stu-id="61265-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="61265-112">(To znamená, že není možné načíst aktuální hodnoty z těchto objektů.)</span><span class="sxs-lookup"><span data-stu-id="61265-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6.  <span data-ttu-id="61265-113">Aktivovat žádost pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> v rámci `using` blok (`Using` v aplikaci Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="61265-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="61265-114">Po získání <xref:System.Windows.Automation.AutomationElement> objekty nebo přihlášení k odběru událostí, deaktivovat žádost pomocí <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Pokud <xref:System.Windows.Automation.CacheRequest.Push%2A> byla použita) nebo uvolnění objektu vytvořeného <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="61265-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="61265-115">(Použití <xref:System.Windows.Automation.CacheRequest.Activate%2A> v `using` blok (`Using` v aplikaci Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="61265-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="61265-116">Třída AutomationElement vlastnosti mezipaměti</span><span class="sxs-lookup"><span data-stu-id="61265-116">Cache AutomationElement Properties</span></span>  
  
1.  <span data-ttu-id="61265-117">Zatímco <xref:System.Windows.Automation.CacheRequest> je aktivní, získat <xref:System.Windows.Automation.AutomationElement> objektů pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; nebo získat <xref:System.Windows.Automation.AutomationElement> jako zdroj události, které jste zaregistrovali pro případ <xref:System.Windows.Automation.CacheRequest> byl aktivní.</span><span class="sxs-lookup"><span data-stu-id="61265-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="61265-118">(Můžete také vytvořit mezipaměť předáním <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache nebo jeden z <xref:System.Windows.Automation.TreeWalker> metody.)</span><span class="sxs-lookup"><span data-stu-id="61265-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2.  <span data-ttu-id="61265-119">Použití <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtení vlastnosti z <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastnost <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="61265-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="61265-120">Získat vzory v mezipaměti a jejich vlastnosti</span><span class="sxs-lookup"><span data-stu-id="61265-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1.  <span data-ttu-id="61265-121">Zatímco <xref:System.Windows.Automation.CacheRequest> je aktivní, získat <xref:System.Windows.Automation.AutomationElement> objektů pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; nebo získat <xref:System.Windows.Automation.AutomationElement> jako zdroj události, které jste zaregistrovali pro případ <xref:System.Windows.Automation.CacheRequest> byl aktivní.</span><span class="sxs-lookup"><span data-stu-id="61265-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="61265-122">(Můžete také vytvořit mezipaměť předáním <xref:System.Windows.Automation.CacheRequest> GetUpdatedCache nebo jeden z <xref:System.Windows.Automation.TreeWalker> metody.)</span><span class="sxs-lookup"><span data-stu-id="61265-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2.  <span data-ttu-id="61265-123">Použití <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> načíst vzor uložený v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61265-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3.  <span data-ttu-id="61265-124">Načíst hodnoty vlastností z `Cached` vlastnost vzor ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="61265-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61265-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="61265-125">Example</span></span>  
 <span data-ttu-id="61265-126">Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti, pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> aktivovat <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="61265-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="61265-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="61265-127">Example</span></span>  
 <span data-ttu-id="61265-128">Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti, pomocí <xref:System.Windows.Automation.CacheRequest.Push%2A> aktivovat <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="61265-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="61265-129">S výjimkou toho, když budete chtít vnořit požadavků mezipaměti, je vhodnější použít <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="61265-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="61265-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="61265-130">See Also</span></span>  
 [<span data-ttu-id="61265-131">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="61265-131">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
