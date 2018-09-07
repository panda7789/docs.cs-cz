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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 10f947fc44e69368e30614e0b41eaf7c73fb6563
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44084946"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="82e81-102">Oznámení pro kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="82e81-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="82e81-103">Existují situace, ve kterých může úplného uvolňování paměti kolekce (to znamená, že kolekce generace 2) modulem common language runtime nepříznivě ovlivnit výkon.</span><span class="sxs-lookup"><span data-stu-id="82e81-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="82e81-104">To může být problém zvláště u serverů, které zpracovávají velký objem požadavků. v takovém případě dlouhé uvolnění paměti může způsobit vypršení časového limitu požadavku. Pokud chcete zabránit celé kolekce, ze které se vyskytují během kritických období, můžete být upozorněni, že úplné uvolnění paměti se blíží a pak provedete akce vedoucí k přesměrování zatížení k jiné instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="82e81-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="82e81-105">Můžete také zahájit kolekce sami, za předpokladu, že není potřeba zpracovávat požadavky na aktuální instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="82e81-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="82e81-106"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda registruje pro oznámení, chcete-li být vyvolána, když modul runtime detekuje, že se blíží úplného uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="82e81-107">Existují dvě části pro toto oznámení: když se blíží úplného uvolňování paměti kolekce a po dokončení úplného uvolňování paměti kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="82e81-108">Blokování uvolnění paměti pouze zvýšit oznámení.</span><span class="sxs-lookup"><span data-stu-id="82e81-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="82e81-109">Když [ \<gcConcurrent >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) konfigurační element je povolen, nevyvolá uvolnění paměti na pozadí, oznámení.</span><span class="sxs-lookup"><span data-stu-id="82e81-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="82e81-110">Chcete-li zjistit, kdy bylo vyvoláno upozornění, použijte <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="82e81-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="82e81-111">Obvykle se používají tyto metody v `while` smyčky průběžně získat <xref:System.GCNotificationStatus> výčet, který se zobrazuje stav oznámení.</span><span class="sxs-lookup"><span data-stu-id="82e81-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="82e81-112">Pokud je tato hodnota <xref:System.GCNotificationStatus.Succeeded>, abyste udělali toto:</span><span class="sxs-lookup"><span data-stu-id="82e81-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
-   <span data-ttu-id="82e81-113">V reakci na oznámení získali díky <xref:System.GC.WaitForFullGCApproach%2A> metodu, můžete přesměrovat úlohy a potenciálně způsobit kolekce sami.</span><span class="sxs-lookup"><span data-stu-id="82e81-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
-   <span data-ttu-id="82e81-114">V reakci na oznámení získali díky <xref:System.GC.WaitForFullGCComplete%2A> metodu, můžete provést aktuální instance serveru k dispozici pro zpracování požadavků znovu.</span><span class="sxs-lookup"><span data-stu-id="82e81-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="82e81-115">Může také shromažďovat informace.</span><span class="sxs-lookup"><span data-stu-id="82e81-115">You can also gather information.</span></span> <span data-ttu-id="82e81-116">Například můžete použít <xref:System.GC.CollectionCount%2A> metoda k zaznamenání počtu kolekcí.</span><span class="sxs-lookup"><span data-stu-id="82e81-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="82e81-117"><xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody jsou navrženy pro práci společně.</span><span class="sxs-lookup"><span data-stu-id="82e81-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="82e81-118">Pomocí jednoho bez nich můžete výsledky neurčitý.</span><span class="sxs-lookup"><span data-stu-id="82e81-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="82e81-119">Úplné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="82e81-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="82e81-120">Modul runtime způsobuje úplného uvolňování paměti kolekce, když je splněna některá z následujících scénářů:</span><span class="sxs-lookup"><span data-stu-id="82e81-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
-   <span data-ttu-id="82e81-121">Dostatek paměti má byla povýšeny do generace 2 způsobit další generaci 2 kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="82e81-122">Dostatek paměti byl povýšen na velkých objektových haldách způsobit další generaci 2 kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="82e81-123">Sběr generace 1 je eskalován jej kolekce generace 2 z důvodu dalších faktorů.</span><span class="sxs-lookup"><span data-stu-id="82e81-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="82e81-124">Prahové hodnoty, které zadáte <xref:System.GC.RegisterForFullGCNotification%2A> metoda platí pro první dva scénáře.</span><span class="sxs-lookup"><span data-stu-id="82e81-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="82e81-125">První scénář, nebude však vždycky dostat oznámení v době úměrná prahové hodnoty, kterou zadáte pro dva důvody:</span><span class="sxs-lookup"><span data-stu-id="82e81-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
-   <span data-ttu-id="82e81-126">Modul runtime nekontroluje každý přidělení malých objektů (z důvodů výkonu).</span><span class="sxs-lookup"><span data-stu-id="82e81-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
-   <span data-ttu-id="82e81-127">Pouze generace 1 kolekce propagace paměti do 2. generace.</span><span class="sxs-lookup"><span data-stu-id="82e81-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="82e81-128">Třetí scénář také přispívá ke nejistota když bude oznámení zasláno.</span><span class="sxs-lookup"><span data-stu-id="82e81-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="82e81-129">I když to není zárukou, že bude užitečný způsob, jak zmírnit efekty nevhodnou úplného uvolňování přesměrování požadavků během této doby nebo nevyvolá kolekci, sami když ho může lépe vyhovovat.</span><span class="sxs-lookup"><span data-stu-id="82e81-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="82e81-130">Parametry prahová hodnota oznámení</span><span class="sxs-lookup"><span data-stu-id="82e81-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="82e81-131"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda má dva parametry k určení prahové hodnoty 2. generace objektů a haldy pro velké objekty.</span><span class="sxs-lookup"><span data-stu-id="82e81-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="82e81-132">Pokud jsou splněny tyto hodnoty, by měla být zvýšena oznámení uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="82e81-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="82e81-133">Následující tabulka popisuje tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="82e81-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="82e81-134">Parametr</span><span class="sxs-lookup"><span data-stu-id="82e81-134">Parameter</span></span>|<span data-ttu-id="82e81-135">Popis</span><span class="sxs-lookup"><span data-stu-id="82e81-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="82e81-136">Číslo mezi 1 a 99, která určuje, kdy by měla být zvýšena oznámení založené na objektech, které jsou povýšeny do generace 2.</span><span class="sxs-lookup"><span data-stu-id="82e81-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="82e81-137">Číslo mezi 1 a 99, která určuje, kdy by měla být zvýšena oznámení založené na objektech, které jsou přiděleny do haldy pro velké objekty.</span><span class="sxs-lookup"><span data-stu-id="82e81-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="82e81-138">Pokud zadáte hodnotu, která je příliš vysoká, je vysoká pravděpodobnost, že bude zasláno oznámení, ale může být příliš dlouhou dobou čekat, než modul runtime způsobí, že kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="82e81-139">Pokud jste zahájit kolekce sami, může uvolnit více objektů, než by uvolnit, pokud modul runtime způsobí, že kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="82e81-140">Pokud zadáte hodnotu, která je příliš nízká, modul runtime může způsobit kolekci předtím, než máte dostatek času na upozornění.</span><span class="sxs-lookup"><span data-stu-id="82e81-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82e81-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="82e81-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="82e81-142">Popis</span><span class="sxs-lookup"><span data-stu-id="82e81-142">Description</span></span>  
 <span data-ttu-id="82e81-143">V následujícím příkladu skupiny serverů služby příchozích webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="82e81-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="82e81-144">Pro simulaci zatížení zpracování požadavků, bajtová pole se přidají do <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="82e81-145">Každý server zaregistruje pro oznámení uvolnění paměti a poté spustí vlákno na `WaitForFullGCProc` metody uživatele k nepřetržitému monitorování <xref:System.GCNotificationStatus> výčet, který je vrácený <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="82e81-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="82e81-146"><xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody volání svých metod uživatele zpracování událostí při vyvolání oznámení:</span><span class="sxs-lookup"><span data-stu-id="82e81-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
-   `OnFullGCApproachNotify`  
  
     <span data-ttu-id="82e81-147">Tato metoda volá `RedirectRequests` metody uživatele, který nastaví server služby Řízení front žádost o pozastavení odesílání požadavku na server.</span><span class="sxs-lookup"><span data-stu-id="82e81-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="82e81-148">To se simuluje nastavením proměnné úrovni třídy `bAllocate` k `false` tak, aby se přidělují žádné další objekty.</span><span class="sxs-lookup"><span data-stu-id="82e81-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="82e81-149">Dále `FinishExistingRequests` uživatele metoda je volána na dokončení zpracování žádosti čekající na vyřízení serveru.</span><span class="sxs-lookup"><span data-stu-id="82e81-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="82e81-150">To se simuluje zrušením <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="82e81-151">Uvolňování paměti je vyvolaných finally, protože je zatížení světla.</span><span class="sxs-lookup"><span data-stu-id="82e81-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
-   `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="82e81-152">Tato metoda volá metodu uživatele `AcceptRequests` obnovit přijímá žádosti, protože na serveru už není náchylné k úplné uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="82e81-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="82e81-153">Tato akce se simuluje tak, že nastavíte `bAllocate` proměnnou `true` tak, aby objekty může pokračovat se přidávají do <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="82e81-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="82e81-154">Následující kód obsahuje `Main` metoda v příkladu.</span><span class="sxs-lookup"><span data-stu-id="82e81-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="82e81-155">Následující kód obsahuje `WaitForFullGCProc` metody uživatele, obsahující průběžné ke kontrole oznámení pro kolekci paměti smyčku while.</span><span class="sxs-lookup"><span data-stu-id="82e81-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="82e81-156">Následující kód obsahuje `OnFullGCApproachNotify` způsob, jak volat z</span><span class="sxs-lookup"><span data-stu-id="82e81-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="82e81-157">`WaitForFullGCProc` Metoda.</span><span class="sxs-lookup"><span data-stu-id="82e81-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="82e81-158">Následující kód obsahuje `OnFullGCApproachComplete` způsob, jak volat z</span><span class="sxs-lookup"><span data-stu-id="82e81-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="82e81-159">`WaitForFullGCProc` Metoda.</span><span class="sxs-lookup"><span data-stu-id="82e81-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="82e81-160">Následující kód obsahuje metody uživatele, které se volají z `OnFullGCApproachNotify` a `OnFullGCCompleteNotify` metody.</span><span class="sxs-lookup"><span data-stu-id="82e81-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="82e81-161">Metody uživatele přesměrování požadavků, Dokončit existující žádosti o a poté obnovit požadavky po úplné uvolnění paměti došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="82e81-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="82e81-162">Vzorový kód celé vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="82e81-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="82e81-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82e81-163">See also</span></span>

- [<span data-ttu-id="82e81-164">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="82e81-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
