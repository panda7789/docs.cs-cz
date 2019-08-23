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
ms.openlocfilehash: 38c7742f3e4691f29490e73b05616754415eac58
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953905"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="10ebd-102">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="10ebd-102">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="10ebd-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované <xref:System.Windows.Automation> v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="10ebd-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="10ebd-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API služby Windows Automation: Automatizace](https://go.microsoft.com/fwlink/?LinkID=156746)uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="10ebd-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](https://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="10ebd-105">V této části se dozvíte, jak <xref:System.Windows.Automation.AutomationElement> implementovat ukládání vlastností a vzorů ovládacích prvků do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="10ebd-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="10ebd-106">Aktivace žádosti o mezipaměť</span><span class="sxs-lookup"><span data-stu-id="10ebd-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="10ebd-107">Vytvoření <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="10ebd-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="10ebd-108">Zadejte vlastnosti a vzory pro ukládání do mezipaměti <xref:System.Windows.Automation.CacheRequest.Add%2A>pomocí.</span><span class="sxs-lookup"><span data-stu-id="10ebd-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="10ebd-109">Určete rozsah ukládání do mezipaměti <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> nastavením vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="10ebd-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="10ebd-110">Určete zobrazení podstromu <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> nastavením vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="10ebd-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="10ebd-111">Nastavte vlastnost na <xref:System.Windows.Automation.AutomationElementMode.None> hodnotu, pokud chcete zvýšit efektivitu tím, že nenačtete úplný odkaz na objekty. <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A></span><span class="sxs-lookup"><span data-stu-id="10ebd-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="10ebd-112">(Díky tomu nebude možné načíst aktuální hodnoty z těchto objektů.)</span><span class="sxs-lookup"><span data-stu-id="10ebd-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="10ebd-113">Aktivujte žádost pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloku (`Using` v Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="10ebd-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="10ebd-114">Po získání <xref:System.Windows.Automation.AutomationElement> objektů nebo přihlášení k odběru událostí dezaktivujte požadavek pomocí <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Pokud <xref:System.Windows.Automation.CacheRequest.Push%2A> bylo použito) nebo likvidací objektu vytvořeného pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="10ebd-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="10ebd-115">(Použijte <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` v bloku (`Using` v Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="10ebd-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="10ebd-116">Vlastnosti třída AutomationElement neobsahuje mezipaměti</span><span class="sxs-lookup"><span data-stu-id="10ebd-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="10ebd-117"><xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement> Když je aktivní, získá <xref:System.Windows.Automation.AutomationElement> objekty pomocí nebo; nebo získá jako zdroj události, kterou jste zaregistrovali v okamžiku, kdy <xref:System.Windows.Automation.CacheRequest> byla aktivní. <xref:System.Windows.Automation.CacheRequest></span><span class="sxs-lookup"><span data-stu-id="10ebd-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="10ebd-118">(Mezipaměť můžete vytvořit také předáním <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jedné <xref:System.Windows.Automation.TreeWalker> z metod.)</span><span class="sxs-lookup"><span data-stu-id="10ebd-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="10ebd-119">Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtěte vlastnost <xref:System.Windows.Automation.AutomationElement.Cached%2A> z vlastnosti <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="10ebd-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="10ebd-120">Získání vzorů v mezipaměti a jejich vlastností</span><span class="sxs-lookup"><span data-stu-id="10ebd-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="10ebd-121"><xref:System.Windows.Automation.AutomationElement.FindAll%2A> <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> <xref:System.Windows.Automation.AutomationElement> Když je aktivní, získá <xref:System.Windows.Automation.AutomationElement> objekty pomocí nebo; nebo získá jako zdroj události, kterou jste zaregistrovali v okamžiku, kdy <xref:System.Windows.Automation.CacheRequest> byla aktivní. <xref:System.Windows.Automation.CacheRequest></span><span class="sxs-lookup"><span data-stu-id="10ebd-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="10ebd-122">(Mezipaměť můžete vytvořit také předáním <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jedné <xref:System.Windows.Automation.TreeWalker> z metod.)</span><span class="sxs-lookup"><span data-stu-id="10ebd-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="10ebd-123">Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo<xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> k načtení vzoru uloženého v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="10ebd-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="10ebd-124">Načte hodnoty vlastností z `Cached` vlastnosti vzoru ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="10ebd-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10ebd-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="10ebd-125">Example</span></span>  
 <span data-ttu-id="10ebd-126">Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí nástroje <xref:System.Windows.Automation.CacheRequest.Activate%2A> pro <xref:System.Windows.Automation.CacheRequest>aktivaci.</span><span class="sxs-lookup"><span data-stu-id="10ebd-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="10ebd-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="10ebd-127">Example</span></span>  
 <span data-ttu-id="10ebd-128">Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí nástroje <xref:System.Windows.Automation.CacheRequest.Push%2A> pro <xref:System.Windows.Automation.CacheRequest>aktivaci.</span><span class="sxs-lookup"><span data-stu-id="10ebd-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="10ebd-129">S výjimkou případů, kdy chcete vnořit požadavky do mezipaměti, je vhodnější použít <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="10ebd-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="10ebd-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="10ebd-130">See also</span></span>

- [<span data-ttu-id="10ebd-131">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="10ebd-131">Caching in UI Automation Clients</span></span>](../../../docs/framework/ui-automation/caching-in-ui-automation-clients.md)
