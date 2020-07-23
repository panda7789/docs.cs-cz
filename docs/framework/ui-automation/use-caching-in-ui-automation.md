---
title: Použití mezipaměti při automatizaci uživatelského rozhraní
description: Podívejte se, jak používat ukládání do mezipaměti v automatizaci uživatelského rozhraní. Projděte si kroky pro aktivaci žádosti o mezipaměť, ukládání do mezipaměti třída AutomationElement neobsahuje vlastností a získání vzorů v mezipaměti.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- caching, UI Automation
- UI Automation, caching
ms.assetid: ec722dff-6009-4279-b86a-e18d3fa94ebf
ms.openlocfilehash: 8dff9db77e39dc66a16b6a7b395c76a3c768d48e
ms.sourcegitcommit: 40de8df14289e1e05b40d6e5c1daabd3c286d70c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/22/2020
ms.locfileid: "86924484"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="61258-104">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="61258-104">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="61258-105">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v <xref:System.Windows.Automation> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="61258-105">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="61258-106">Nejnovější informace o najdete [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] v tématu [rozhraní API služby Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="61258-106">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="61258-107">V této části se dozvíte, jak implementovat ukládání <xref:System.Windows.Automation.AutomationElement> vlastností a vzorů ovládacích prvků do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61258-107">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="61258-108">Aktivace žádosti o mezipaměť</span><span class="sxs-lookup"><span data-stu-id="61258-108">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="61258-109">Vytvořte <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="61258-109">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="61258-110">Zadejte vlastnosti a vzory pro ukládání do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A> .</span><span class="sxs-lookup"><span data-stu-id="61258-110">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="61258-111">Určete rozsah ukládání do mezipaměti nastavením <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="61258-111">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="61258-112">Určete zobrazení podstromu nastavením <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="61258-112">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="61258-113">Nastavte <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> vlastnost na hodnotu, <xref:System.Windows.Automation.AutomationElementMode.None> Pokud chcete zvýšit efektivitu tím, že nenačtete úplný odkaz na objekty.</span><span class="sxs-lookup"><span data-stu-id="61258-113">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="61258-114">(Díky tomu nebude možné načíst aktuální hodnoty z těchto objektů.)</span><span class="sxs-lookup"><span data-stu-id="61258-114">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="61258-115">Aktivujte žádost pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> `using` bloku ( `Using` v Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="61258-115">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="61258-116">Po získání <xref:System.Windows.Automation.AutomationElement> objektů nebo přihlášení k odběru událostí dezaktivujte požadavek pomocí <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Pokud <xref:System.Windows.Automation.CacheRequest.Push%2A> bylo použito) nebo likvidací objektu vytvořeného pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> .</span><span class="sxs-lookup"><span data-stu-id="61258-116">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="61258-117">(Použijte <xref:System.Windows.Automation.CacheRequest.Activate%2A> v `using` bloku ( `Using` v Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="61258-117">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="61258-118">Vlastnosti třída AutomationElement neobsahuje mezipaměti</span><span class="sxs-lookup"><span data-stu-id="61258-118">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="61258-119">Když <xref:System.Windows.Automation.CacheRequest> je aktivní, získá <xref:System.Windows.Automation.AutomationElement> objekty pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ; nebo získá <xref:System.Windows.Automation.AutomationElement> jako zdroj události, kterou jste zaregistrovali v okamžiku, kdy <xref:System.Windows.Automation.CacheRequest> byla aktivní.</span><span class="sxs-lookup"><span data-stu-id="61258-119">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="61258-120">(Mezipaměť můžete vytvořit také předáním <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jedné z <xref:System.Windows.Automation.TreeWalker> metod.)</span><span class="sxs-lookup"><span data-stu-id="61258-120">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="61258-121">Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtěte vlastnost z <xref:System.Windows.Automation.AutomationElement.Cached%2A> vlastnosti <xref:System.Windows.Automation.AutomationElement> .</span><span class="sxs-lookup"><span data-stu-id="61258-121">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="61258-122">Získání vzorů v mezipaměti a jejich vlastností</span><span class="sxs-lookup"><span data-stu-id="61258-122">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="61258-123">Když <xref:System.Windows.Automation.CacheRequest> je aktivní, získá <xref:System.Windows.Automation.AutomationElement> objekty pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A> ; nebo získá <xref:System.Windows.Automation.AutomationElement> jako zdroj události, kterou jste zaregistrovali v okamžiku, kdy <xref:System.Windows.Automation.CacheRequest> byla aktivní.</span><span class="sxs-lookup"><span data-stu-id="61258-123">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="61258-124">(Mezipaměť můžete vytvořit také předáním <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jedné z <xref:System.Windows.Automation.TreeWalker> metod.)</span><span class="sxs-lookup"><span data-stu-id="61258-124">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="61258-125">Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> k načtení vzoru uloženého v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61258-125">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="61258-126">Načte hodnoty vlastností z `Cached` vlastnosti vzoru ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="61258-126">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="61258-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="61258-127">Example</span></span>  
 <span data-ttu-id="61258-128">Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí nástroje <xref:System.Windows.Automation.CacheRequest.Activate%2A> pro aktivaci <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="61258-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="61258-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="61258-129">Example</span></span>  
 <span data-ttu-id="61258-130">Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí nástroje <xref:System.Windows.Automation.CacheRequest.Push%2A> pro aktivaci <xref:System.Windows.Automation.CacheRequest> .</span><span class="sxs-lookup"><span data-stu-id="61258-130">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="61258-131">S výjimkou případů, kdy chcete vnořit požadavky do mezipaměti, je vhodnější použít <xref:System.Windows.Automation.CacheRequest.Activate%2A> .</span><span class="sxs-lookup"><span data-stu-id="61258-131">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="61258-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="61258-132">See also</span></span>

- [<span data-ttu-id="61258-133">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="61258-133">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
