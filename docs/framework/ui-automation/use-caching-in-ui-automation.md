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
ms.openlocfilehash: 679192b611a423e095ee9acc956d247364940edf
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/04/2019
ms.locfileid: "74800805"
---
# <a name="use-caching-in-ui-automation"></a><span data-ttu-id="0cd2d-102">Použití mezipaměti při automatizaci uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cd2d-102">Use Caching in UI Automation</span></span>
> [!NOTE]
> <span data-ttu-id="0cd2d-103">Tato dokumentace je určena pro .NET Framework vývojářů, kteří chtějí používat spravované [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] třídy definované v oboru názvů <xref:System.Windows.Automation>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="0cd2d-104">Nejnovější informace o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]najdete v tématu [rozhraní API pro Windows Automation: automatizace uživatelského rozhraní](/windows/win32/winauto/entry-uiauto-win32).</span><span class="sxs-lookup"><span data-stu-id="0cd2d-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](/windows/win32/winauto/entry-uiauto-win32).</span></span>  
  
 <span data-ttu-id="0cd2d-105">V této části se dozvíte, jak implementovat ukládání do mezipaměti <xref:System.Windows.Automation.AutomationElement> vlastností a vzorů ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-105">This section shows how to implement caching of <xref:System.Windows.Automation.AutomationElement> properties and control patterns.</span></span>  
  
### <a name="activate-a-cache-request"></a><span data-ttu-id="0cd2d-106">Aktivace žádosti o mezipaměť</span><span class="sxs-lookup"><span data-stu-id="0cd2d-106">Activate a Cache Request</span></span>  
  
1. <span data-ttu-id="0cd2d-107">Vytvoření <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-107">Create a <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
2. <span data-ttu-id="0cd2d-108">Zadání vlastností a vzorů pro ukládání do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-108">Specify properties and patterns to cache by using <xref:System.Windows.Automation.CacheRequest.Add%2A>.</span></span>  
  
3. <span data-ttu-id="0cd2d-109">Určete rozsah ukládání do mezipaměti nastavením vlastnosti <xref:System.Windows.Automation.CacheRequest.TreeScope%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-109">Specify the scope of caching by setting the <xref:System.Windows.Automation.CacheRequest.TreeScope%2A> property.</span></span>  
  
4. <span data-ttu-id="0cd2d-110">Určete zobrazení podstromu nastavením vlastnosti <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-110">Specify the view of the subtree by setting the <xref:System.Windows.Automation.CacheRequest.TreeFilter%2A> property.</span></span>  
  
5. <span data-ttu-id="0cd2d-111">Nastavte vlastnost <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> na <xref:System.Windows.Automation.AutomationElementMode.None>, pokud chcete zvýšit efektivitu tím, že nenačtete úplný odkaz na objekty.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-111">Set the <xref:System.Windows.Automation.CacheRequest.AutomationElementMode%2A> property to <xref:System.Windows.Automation.AutomationElementMode.None> if you wish to increase efficiency by not retrieving a full reference to objects.</span></span> <span data-ttu-id="0cd2d-112">(Díky tomu nebude možné načíst aktuální hodnoty z těchto objektů.)</span><span class="sxs-lookup"><span data-stu-id="0cd2d-112">(This will make it impossible to retrieve current values from those objects.)</span></span>  
  
6. <span data-ttu-id="0cd2d-113">Aktivujte žádost pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> v rámci bloku `using` (`Using` v Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="0cd2d-113">Activate the request by using <xref:System.Windows.Automation.CacheRequest.Activate%2A> within a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
 <span data-ttu-id="0cd2d-114">Po získání <xref:System.Windows.Automation.AutomationElement> objektů nebo přihlášení k odběru událostí deaktivujte požadavek pomocí <xref:System.Windows.Automation.CacheRequest.Pop%2A> (Pokud se <xref:System.Windows.Automation.CacheRequest.Push%2A> použil), nebo odstraněním objektu vytvořeného <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-114">After obtaining <xref:System.Windows.Automation.AutomationElement> objects or subscribing to events, deactivate the request by using <xref:System.Windows.Automation.CacheRequest.Pop%2A> (if <xref:System.Windows.Automation.CacheRequest.Push%2A> was used) or by disposing the object created by <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span> <span data-ttu-id="0cd2d-115">(Použijte <xref:System.Windows.Automation.CacheRequest.Activate%2A> v bloku `using` (`Using` v Microsoft Visual Basic .NET).</span><span class="sxs-lookup"><span data-stu-id="0cd2d-115">(Use <xref:System.Windows.Automation.CacheRequest.Activate%2A> in a `using` block (`Using` in Microsoft Visual Basic .NET).</span></span>  
  
### <a name="cache-automationelement-properties"></a><span data-ttu-id="0cd2d-116">Vlastnosti třída AutomationElement neobsahuje mezipaměti</span><span class="sxs-lookup"><span data-stu-id="0cd2d-116">Cache AutomationElement Properties</span></span>  
  
1. <span data-ttu-id="0cd2d-117">Když je aktivní <xref:System.Windows.Automation.CacheRequest>, získat <xref:System.Windows.Automation.AutomationElement> objektů pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; nebo můžete získat <xref:System.Windows.Automation.AutomationElement> jako zdroj události, kterou jste zaregistrovali v případě, že byla <xref:System.Windows.Automation.CacheRequest> aktivní.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-117">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="0cd2d-118">(Mezipaměť můžete vytvořit také tak, že předáte <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jednu z <xref:System.Windows.Automation.TreeWalker> metod.)</span><span class="sxs-lookup"><span data-stu-id="0cd2d-118">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="0cd2d-119">Použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> nebo načtěte vlastnost z vlastnosti <xref:System.Windows.Automation.AutomationElement.Cached%2A> <xref:System.Windows.Automation.AutomationElement>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-119">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPropertyValue%2A> or retrieve a property from the <xref:System.Windows.Automation.AutomationElement.Cached%2A> property of the <xref:System.Windows.Automation.AutomationElement>.</span></span>  
  
### <a name="obtain-cached-patterns-and-their-properties"></a><span data-ttu-id="0cd2d-120">Získání vzorů v mezipaměti a jejich vlastností</span><span class="sxs-lookup"><span data-stu-id="0cd2d-120">Obtain Cached Patterns and Their Properties</span></span>  
  
1. <span data-ttu-id="0cd2d-121">Když je aktivní <xref:System.Windows.Automation.CacheRequest>, získat <xref:System.Windows.Automation.AutomationElement> objektů pomocí <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> nebo <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; nebo můžete získat <xref:System.Windows.Automation.AutomationElement> jako zdroj události, kterou jste zaregistrovali v případě, že byla <xref:System.Windows.Automation.CacheRequest> aktivní.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-121">While a <xref:System.Windows.Automation.CacheRequest> is active, obtain <xref:System.Windows.Automation.AutomationElement> objects by using <xref:System.Windows.Automation.AutomationElement.FindFirst%2A> or <xref:System.Windows.Automation.AutomationElement.FindAll%2A>; or obtain an <xref:System.Windows.Automation.AutomationElement> as the source of an event that you registered for when the <xref:System.Windows.Automation.CacheRequest> was active.</span></span> <span data-ttu-id="0cd2d-122">(Mezipaměť můžete vytvořit také tak, že předáte <xref:System.Windows.Automation.CacheRequest> do GetUpdatedCache nebo jednu z <xref:System.Windows.Automation.TreeWalker> metod.)</span><span class="sxs-lookup"><span data-stu-id="0cd2d-122">(You can also create a cache by passing a <xref:System.Windows.Automation.CacheRequest> to GetUpdatedCache or one of the <xref:System.Windows.Automation.TreeWalker> methods.)</span></span>  
  
2. <span data-ttu-id="0cd2d-123">K načtení vzoru uloženého v mezipaměti použijte <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> nebo <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-123">Use <xref:System.Windows.Automation.AutomationElement.GetCachedPattern%2A> or <xref:System.Windows.Automation.AutomationElement.TryGetCachedPattern%2A> to retrieve a cached pattern.</span></span>  
  
3. <span data-ttu-id="0cd2d-124">Načte hodnoty vlastností z vlastnosti `Cached` vzoru ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-124">Retrieve property values from the `Cached` property of the control pattern.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cd2d-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cd2d-125">Example</span></span>  
 <span data-ttu-id="0cd2d-126">Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Activate%2A> pro aktivaci <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-126">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Activate%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span>  
  
 [!code-csharp[UIAClient_snip#107](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#107)]
 [!code-vb[UIAClient_snip#107](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#107)]  
  
## <a name="example"></a><span data-ttu-id="0cd2d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="0cd2d-127">Example</span></span>  
 <span data-ttu-id="0cd2d-128">Následující příklad kódu ukazuje různé aspekty ukládání do mezipaměti pomocí <xref:System.Windows.Automation.CacheRequest.Push%2A> pro aktivaci <xref:System.Windows.Automation.CacheRequest>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-128">The following code example shows various aspects of caching, using <xref:System.Windows.Automation.CacheRequest.Push%2A> to activate the <xref:System.Windows.Automation.CacheRequest>.</span></span> <span data-ttu-id="0cd2d-129">S výjimkou případů, kdy chcete vnořit požadavky do mezipaměti, je vhodnější použít <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cd2d-129">Except when you wish to nest cache requests, it is preferable to use <xref:System.Windows.Automation.CacheRequest.Activate%2A>.</span></span>  
  
 [!code-csharp[UIAClient_snip#108](../../../samples/snippets/csharp/VS_Snippets_Wpf/UIAClient_snip/CSharp/ClientForm.cs#108)]
 [!code-vb[UIAClient_snip#108](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UIAClient_snip/VisualBasic/ClientForm.vb#108)]  
  
## <a name="see-also"></a><span data-ttu-id="0cd2d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0cd2d-130">See also</span></span>

- [<span data-ttu-id="0cd2d-131">Práce s mezipamětí u klientů automatizace uživatelského rozhraní</span><span class="sxs-lookup"><span data-stu-id="0cd2d-131">Caching in UI Automation Clients</span></span>](caching-in-ui-automation-clients.md)
