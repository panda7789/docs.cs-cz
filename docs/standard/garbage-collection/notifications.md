---
title: Oznámení pro kolekci paměti
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- garbage collection, notifications
ms.assetid: e12d8e74-31e3-4035-a87d-f3e66f0a9b89
ms.openlocfilehash: d5646c4969c95350ab4cd63b16f6f99ffba3a4ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131538"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="d60f1-102">Oznámení pro kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="d60f1-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="d60f1-103">Existují situace, ve kterých úplné uvolnění paměti (to znamená generace 2 kolekce) podle prostředí common language runtime může nepříznivě ovlivnit výkon.</span><span class="sxs-lookup"><span data-stu-id="d60f1-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="d60f1-104">To může být problém zejména se servery, které zpracovávají velké objemy požadavků; v tomto případě dlouhé uvolňování paměti může způsobit časový čas požadavku. Chcete-li zabránit úplné kolekce dochází během kritického období, můžete být upozorněni, že úplné uvolnění paměti se blíží a pak provést akci k přesměrování úlohy do jiné instance serveru.</span><span class="sxs-lookup"><span data-stu-id="d60f1-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="d60f1-105">Můžete také vyvolat kolekce sami, za předpokladu, že aktuální instance serveru není nutné zpracovávat požadavky.</span><span class="sxs-lookup"><span data-stu-id="d60f1-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="d60f1-106">Metoda <xref:System.GC.RegisterForFullGCNotification%2A> registruje pro oznámení, které mají být vyvolány, když za běhu cítí, že úplné uvolnění paměti se blíží.</span><span class="sxs-lookup"><span data-stu-id="d60f1-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="d60f1-107">Existují dvě části tohoto oznámení: při úplné uvolňování paměti se blíží a po dokončení úplné uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="d60f1-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d60f1-108">Pouze blokování uvolňování paměti vyvolat oznámení.</span><span class="sxs-lookup"><span data-stu-id="d60f1-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="d60f1-109">Pokud je povolen [ \<prvek gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) konfigurace, uvolnění paměti na pozadí nevyvolá oznámení.</span><span class="sxs-lookup"><span data-stu-id="d60f1-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="d60f1-110">Chcete-li zjistit, kdy bylo <xref:System.GC.WaitForFullGCApproach%2A> vyvoláno oznámení, použijte metody a. <xref:System.GC.WaitForFullGCComplete%2A></span><span class="sxs-lookup"><span data-stu-id="d60f1-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="d60f1-111">Obvykle použijete tyto metody `while` ve smyčce neustále <xref:System.GCNotificationStatus> získat výčet, který zobrazuje stav oznámení.</span><span class="sxs-lookup"><span data-stu-id="d60f1-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="d60f1-112">Pokud je <xref:System.GCNotificationStatus.Succeeded>tato hodnota , můžete provést následující kroky:</span><span class="sxs-lookup"><span data-stu-id="d60f1-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="d60f1-113">V reakci na oznámení <xref:System.GC.WaitForFullGCApproach%2A> získané pomocí metody můžete přesměrovat úlohy a případně vyvolat kolekce sami.</span><span class="sxs-lookup"><span data-stu-id="d60f1-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="d60f1-114">V reakci na oznámení <xref:System.GC.WaitForFullGCComplete%2A> získané metodou můžete zpřístupnit aktuální instanci serveru pro zpracování požadavků znovu.</span><span class="sxs-lookup"><span data-stu-id="d60f1-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="d60f1-115">Můžete také shromažďovat informace.</span><span class="sxs-lookup"><span data-stu-id="d60f1-115">You can also gather information.</span></span> <span data-ttu-id="d60f1-116">Metodu <xref:System.GC.CollectionCount%2A> můžete například použít k zaznamenání počtu kolekcí.</span><span class="sxs-lookup"><span data-stu-id="d60f1-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="d60f1-117">A <xref:System.GC.WaitForFullGCApproach%2A> metody <xref:System.GC.WaitForFullGCComplete%2A> jsou navrženy tak, aby spolupracovaly.</span><span class="sxs-lookup"><span data-stu-id="d60f1-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="d60f1-118">Použití jednoho bez druhého může vést k neurčitým výsledkům.</span><span class="sxs-lookup"><span data-stu-id="d60f1-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="d60f1-119">Úplné uvolnění paměti</span><span class="sxs-lookup"><span data-stu-id="d60f1-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="d60f1-120">Za běhu způsobí úplné uvolnění paměti, pokud jsou splněny některé z následujících scénářů:</span><span class="sxs-lookup"><span data-stu-id="d60f1-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="d60f1-121">Dostatek paměti byla povýšena do generace 2 způsobit další generace 2 kolekce.</span><span class="sxs-lookup"><span data-stu-id="d60f1-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="d60f1-122">Dostatek paměti byla povýšena do haldy velkého objektu způsobit další generace 2 kolekce.</span><span class="sxs-lookup"><span data-stu-id="d60f1-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="d60f1-123">Kolekce generace 1 je eskalována na kolekci generace 2 kvůli jiným faktorům.</span><span class="sxs-lookup"><span data-stu-id="d60f1-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="d60f1-124">Prahové hodnoty zadané <xref:System.GC.RegisterForFullGCNotification%2A> v metodě platí pro první dva scénáře.</span><span class="sxs-lookup"><span data-stu-id="d60f1-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="d60f1-125">V prvním scénáři však ne vždy obdržíte oznámení v době úměrné prahové hodnotě, kterou zadáte, ze dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="d60f1-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="d60f1-126">Runtime nekontroluje každé přidělení malých objektů (z důvodů výkonu).</span><span class="sxs-lookup"><span data-stu-id="d60f1-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="d60f1-127">Pouze generace 1 kolekce podporovat paměť do generace 2.</span><span class="sxs-lookup"><span data-stu-id="d60f1-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="d60f1-128">Třetí scénář také přispívá k nejistotě, kdy obdržíte oznámení.</span><span class="sxs-lookup"><span data-stu-id="d60f1-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="d60f1-129">I když to není záruka, se ukáže jako užitečný způsob, jak zmírnit účinky nevhodnou úplné uvolnění paměti přesměrováním požadavky během této doby nebo vyvolání kolekce sami, když může být lépe přizpůsobena.</span><span class="sxs-lookup"><span data-stu-id="d60f1-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="d60f1-130">Parametry prahové hodnoty oznámení</span><span class="sxs-lookup"><span data-stu-id="d60f1-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="d60f1-131">Metoda <xref:System.GC.RegisterForFullGCNotification%2A> má dva parametry k určení prahové hodnoty generace 2 objektů a haldy velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="d60f1-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="d60f1-132">Pokud jsou tyto hodnoty splněny, by měla být vyvolána oznámení o uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d60f1-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="d60f1-133">Následující tabulka popisuje tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="d60f1-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="d60f1-134">Parametr</span><span class="sxs-lookup"><span data-stu-id="d60f1-134">Parameter</span></span>|<span data-ttu-id="d60f1-135">Popis</span><span class="sxs-lookup"><span data-stu-id="d60f1-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="d60f1-136">Číslo mezi 1 a 99, který určuje, kdy by měla být zvýšena oznámení na základě objektů povýšen v generaci 2.</span><span class="sxs-lookup"><span data-stu-id="d60f1-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="d60f1-137">Číslo mezi 1 a 99, který určuje, kdy by měla být zvýšena oznámení na základě objektů, které jsou přiděleny v haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="d60f1-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="d60f1-138">Pokud zadáte hodnotu, která je příliš vysoká, je vysoká pravděpodobnost, že obdržíte oznámení, ale může být příliš dlouhá doba čekání, než za běhu způsobí kolekci.</span><span class="sxs-lookup"><span data-stu-id="d60f1-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="d60f1-139">Pokud vyvoláte kolekce sami, můžete získat více objektů, než by být vyvolána, pokud runtime způsobí kolekce.</span><span class="sxs-lookup"><span data-stu-id="d60f1-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="d60f1-140">Pokud zadáte hodnotu, která je příliš nízká, může za běhu způsobit kolekce dříve, než jste měli dostatek času na oznámení.</span><span class="sxs-lookup"><span data-stu-id="d60f1-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d60f1-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="d60f1-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="d60f1-142">Popis</span><span class="sxs-lookup"><span data-stu-id="d60f1-142">Description</span></span>  
 <span data-ttu-id="d60f1-143">V následujícím příkladu skupina serverů obsluhuje příchozí webové požadavky.</span><span class="sxs-lookup"><span data-stu-id="d60f1-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="d60f1-144">Chcete-li simulovat zatížení zpracování požadavků, bajtová <xref:System.Collections.Generic.List%601> pole jsou přidány do kolekce.</span><span class="sxs-lookup"><span data-stu-id="d60f1-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="d60f1-145">Každý server registruje pro oznámení uvolnění paměti a `WaitForFullGCProc` potom spustí vlákno <xref:System.GCNotificationStatus> na metodu uživatele <xref:System.GC.WaitForFullGCApproach%2A> průběžně <xref:System.GC.WaitForFullGCComplete%2A> sledovat výčet, který je vrácen a metody.</span><span class="sxs-lookup"><span data-stu-id="d60f1-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="d60f1-146">A <xref:System.GC.WaitForFullGCApproach%2A> <xref:System.GC.WaitForFullGCComplete%2A> metody volání jejich příslušné metody zpracování událostí uživatele při oznámení je aktivována:</span><span class="sxs-lookup"><span data-stu-id="d60f1-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="d60f1-147">Tato metoda `RedirectRequests` volá metodu uživatele, která instruuje server služby řízení front požadavků, aby pozastavil odesílání požadavků na server.</span><span class="sxs-lookup"><span data-stu-id="d60f1-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="d60f1-148">To je simulováno nastavením `bAllocate` `false` proměnné na úrovni třídy tak, aby nebyly přiděleny žádné další objekty.</span><span class="sxs-lookup"><span data-stu-id="d60f1-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="d60f1-149">Dále je `FinishExistingRequests` volána metoda uživatele k dokončení zpracování čekajících požadavků serveru.</span><span class="sxs-lookup"><span data-stu-id="d60f1-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="d60f1-150">To je simulováno vymazáním <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="d60f1-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="d60f1-151">Nakonec uvolňování paměti je vyvolána, protože zatížení je lehký.</span><span class="sxs-lookup"><span data-stu-id="d60f1-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="d60f1-152">Tato metoda volá `AcceptRequests` metodu uživatele k obnovení přijímání požadavků, protože server již není náchylný k úplnému uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d60f1-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="d60f1-153">Tato akce je simulována nastavením `bAllocate` proměnné tak, aby `true` objekty mohou pokračovat v přidávání do <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="d60f1-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="d60f1-154">Následující kód obsahuje `Main` metodu příkladu.</span><span class="sxs-lookup"><span data-stu-id="d60f1-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="d60f1-155">Následující kód obsahuje `WaitForFullGCProc` metodu uživatele, která obsahuje nepřetržitou smyčku while pro kontrolu oznámení o uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="d60f1-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="d60f1-156">Následující kód obsahuje `OnFullGCApproachNotify` metodu, jak je volána z</span><span class="sxs-lookup"><span data-stu-id="d60f1-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="d60f1-157">`WaitForFullGCProc`Metoda.</span><span class="sxs-lookup"><span data-stu-id="d60f1-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="d60f1-158">Následující kód obsahuje `OnFullGCApproachComplete` metodu, jak je volána z</span><span class="sxs-lookup"><span data-stu-id="d60f1-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="d60f1-159">`WaitForFullGCProc`Metoda.</span><span class="sxs-lookup"><span data-stu-id="d60f1-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="d60f1-160">Následující kód obsahuje uživatelské metody, které `OnFullGCApproachNotify` `OnFullGCCompleteNotify` jsou volány z metody a.</span><span class="sxs-lookup"><span data-stu-id="d60f1-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="d60f1-161">Uživatelské metody přesměrovat požadavky, dokončit existující požadavky a potom obnovit požadavky po úplné uvolnění paměti došlo.</span><span class="sxs-lookup"><span data-stu-id="d60f1-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="d60f1-162">Celý ukázkový kód je následující:</span><span class="sxs-lookup"><span data-stu-id="d60f1-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d60f1-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="d60f1-163">See also</span></span>

- [<span data-ttu-id="d60f1-164">Kolekce paměti</span><span class="sxs-lookup"><span data-stu-id="d60f1-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
