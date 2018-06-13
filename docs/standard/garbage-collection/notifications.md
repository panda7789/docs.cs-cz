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
ms.openlocfilehash: d3470ebdd55adc97a60f07228c441cb7c94a53e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579155"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="67e9c-102">Oznámení pro kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="67e9c-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="67e9c-103">Existují situace, ve kterých může kolekci úplného uvolňování paměti (který je kolekcí generace 2) podle modul common language runtime nepříznivě ovlivnit výkon.</span><span class="sxs-lookup"><span data-stu-id="67e9c-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="67e9c-104">To může být problém zvláště u serverů, které zpracovávají velké objemy požadavků. v takovém případě dlouho uvolňování může způsobit časový limit požadavku. Pokud chcete zabránit úplnou kolekci z výskytu kritické období, můžete být upozorněni, kolekci úplného uvolňování paměti se blíží a pak proveďte akce přesměrování zatížení k jiné instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="67e9c-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="67e9c-105">Můžete může také způsobit kolekci sami, za předpokladu, že aktuální instance serveru nemusí zpracovávat žádosti.</span><span class="sxs-lookup"><span data-stu-id="67e9c-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="67e9c-106"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda registruje pro oznámení se vyvolá, když modul runtime detekuje, že se blíží úplné uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="67e9c-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="67e9c-107">Toto oznámení, skládá ze dvou částí: když se blíží kolekci úplného uvolňování paměti a po dokončení úplné uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="67e9c-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="67e9c-108">Pouze blokující kolekce paměti vyvolat oznámení.</span><span class="sxs-lookup"><span data-stu-id="67e9c-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="67e9c-109">Když [ \<gcconcurrent – >](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) konfigurační prvek je povoleno, pozadí kolekce nevydá oznámení.</span><span class="sxs-lookup"><span data-stu-id="67e9c-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="67e9c-110">Chcete-li zjistit, kdy bylo vyvoláno upozornění, použijte <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="67e9c-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="67e9c-111">Obvykle se používá tyto metody v `while` opakování ve smyčce bude průběžně získat <xref:System.GCNotificationStatus> výčet, který se zobrazí stav oznámení.</span><span class="sxs-lookup"><span data-stu-id="67e9c-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="67e9c-112">Pokud je tato hodnota <xref:System.GCNotificationStatus.Succeeded>, můžete provést následující:</span><span class="sxs-lookup"><span data-stu-id="67e9c-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
-   <span data-ttu-id="67e9c-113">V reakci na oznámení, které byly získány <xref:System.GC.WaitForFullGCApproach%2A> metodu, můžete přesměrovat zatížení a případně vyvolat kolekci sami.</span><span class="sxs-lookup"><span data-stu-id="67e9c-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
-   <span data-ttu-id="67e9c-114">V reakci na oznámení, které byly získány <xref:System.GC.WaitForFullGCComplete%2A> metodu, můžete provést aktuální instanci serveru, která je k dispozici pro zpracování požadavků zopakovat.</span><span class="sxs-lookup"><span data-stu-id="67e9c-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="67e9c-115">Může také shromažďovat informace.</span><span class="sxs-lookup"><span data-stu-id="67e9c-115">You can also gather information.</span></span> <span data-ttu-id="67e9c-116">Například můžete použít <xref:System.GC.CollectionCount%2A> metoda zaznamenání počet kolekcí.</span><span class="sxs-lookup"><span data-stu-id="67e9c-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="67e9c-117"><xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody se nedají používat společně.</span><span class="sxs-lookup"><span data-stu-id="67e9c-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="67e9c-118">Pomocí jednoho bez dalších může vytvářet neurčitém výsledky.</span><span class="sxs-lookup"><span data-stu-id="67e9c-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="67e9c-119">Úplné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="67e9c-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="67e9c-120">Modul runtime způsobí kolekce úplného uvolňování paměti, když některá z následujících scénářů:</span><span class="sxs-lookup"><span data-stu-id="67e9c-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
-   <span data-ttu-id="67e9c-121">Dostatek paměti, se použije do 2 způsobí další kolekce generace 2. generace.</span><span class="sxs-lookup"><span data-stu-id="67e9c-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="67e9c-122">Dostatek paměti, se použije do velkého objektu haldy způsobí další kolekce 2. generace.</span><span class="sxs-lookup"><span data-stu-id="67e9c-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
-   <span data-ttu-id="67e9c-123">Kolekce generace 1 je Eskalovat do kolekce generace 2 z důvodu dalších faktorů.</span><span class="sxs-lookup"><span data-stu-id="67e9c-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="67e9c-124">Prahové hodnoty v zadáte <xref:System.GC.RegisterForFullGCNotification%2A> metoda platí pro první dva scénáře.</span><span class="sxs-lookup"><span data-stu-id="67e9c-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="67e9c-125">První scénář, nebude však vždycky dostat oznámení v době úměrná prahové hodnoty, které zadáte dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="67e9c-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
-   <span data-ttu-id="67e9c-126">Modul runtime nekontroluje každý přidělení malé objektu (z důvodů výkonu).</span><span class="sxs-lookup"><span data-stu-id="67e9c-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
-   <span data-ttu-id="67e9c-127">Pouze generace 1 kolekce povýšení paměti do 2. generace.</span><span class="sxs-lookup"><span data-stu-id="67e9c-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="67e9c-128">Třetí scénář také přispívá k nejistoty z když obdržíte oznámení.</span><span class="sxs-lookup"><span data-stu-id="67e9c-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="67e9c-129">I když to není záruku, ukáže jako vhodný způsob, jak pomocí přesměrování požadavků během této doby nebo zcizení kolekce, sami při můžete se lépe shromáždit, a minimalizoval vliv kolekci nevhodnou úplného uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="67e9c-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="67e9c-130">Oznámení prahové hodnoty parametrů</span><span class="sxs-lookup"><span data-stu-id="67e9c-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="67e9c-131"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda má dva parametry k určení prahové hodnoty objekty 2. generace a haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="67e9c-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="67e9c-132">Pokud jsou splněny tyto hodnoty, má se vrhnout oznámení kolekce paměti.</span><span class="sxs-lookup"><span data-stu-id="67e9c-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="67e9c-133">Následující tabulka popisuje tyto parametry.</span><span class="sxs-lookup"><span data-stu-id="67e9c-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="67e9c-134">Parametr</span><span class="sxs-lookup"><span data-stu-id="67e9c-134">Parameter</span></span>|<span data-ttu-id="67e9c-135">Popis</span><span class="sxs-lookup"><span data-stu-id="67e9c-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="67e9c-136">Číslo mezi 1 a 99, která určuje, kdy by měl vyvolána oznámení založené na objektech podporována ve 2. generace.</span><span class="sxs-lookup"><span data-stu-id="67e9c-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="67e9c-137">Číslo mezi 1 a 99, která určuje, kdy by měl vyvolána oznámení založené na objekty, které mají při přidělování v haldě velkého objektu.</span><span class="sxs-lookup"><span data-stu-id="67e9c-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="67e9c-138">Pokud zadáte hodnotu, která je příliš vysoká, je vysoká pravděpodobnost, že dostanete oznámení, ale může být příliš dlouhou dobou čekání před modulu runtime způsobí, že kolekce.</span><span class="sxs-lookup"><span data-stu-id="67e9c-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="67e9c-139">Pokud jste vyvolat kolekci sami, může získat více objektů, než by uvolnit, pokud modul runtime, způsobí kolekce.</span><span class="sxs-lookup"><span data-stu-id="67e9c-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="67e9c-140">Pokud zadáte hodnotu, která je příliš nízká, modul runtime může způsobit kolekce předtím, než jste předtím dostatek času na upozorněni.</span><span class="sxs-lookup"><span data-stu-id="67e9c-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67e9c-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="67e9c-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="67e9c-142">Popis</span><span class="sxs-lookup"><span data-stu-id="67e9c-142">Description</span></span>  
 <span data-ttu-id="67e9c-143">V následujícím příkladu skupiny serverů služby příchozích webových požadavků.</span><span class="sxs-lookup"><span data-stu-id="67e9c-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="67e9c-144">Pro simulaci zatížení zpracování žádostí, bajtová pole jsou přidány do <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="67e9c-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="67e9c-145">Každý server zaregistruje pro oznámení kolekce paměti a pak spustí vlákna na `WaitForFullGCProc` uživatele metoda neustále monitorovat <xref:System.GCNotificationStatus> výčet, který je vrácený <xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="67e9c-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="67e9c-146"><xref:System.GC.WaitForFullGCApproach%2A> a <xref:System.GC.WaitForFullGCComplete%2A> metody volání svých uživatelů metod zpracování událostí po vyvolání oznámení:</span><span class="sxs-lookup"><span data-stu-id="67e9c-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
-   `OnFullGCApproachNotify`  
  
     <span data-ttu-id="67e9c-147">Tato metoda volá `RedirectRequests` uživatele metoda, která nastaví server služby Řízení front žádost o pozastavení odesílání požadavků na server.</span><span class="sxs-lookup"><span data-stu-id="67e9c-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="67e9c-148">To se simuluje nastavení proměnné úrovni třídy `bAllocate` k `false` tak, že jsou přiděleny žádné další objekty.</span><span class="sxs-lookup"><span data-stu-id="67e9c-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="67e9c-149">Dále `FinishExistingRequests` uživatele metoda je volána k dokončení zpracování žádosti čekající na serveru.</span><span class="sxs-lookup"><span data-stu-id="67e9c-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="67e9c-150">To se simuluje zrušením <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="67e9c-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="67e9c-151">Kolekce paměti je nakonec vyvolané, protože zatížení je light.</span><span class="sxs-lookup"><span data-stu-id="67e9c-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
-   `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="67e9c-152">Tato metoda volá metodu uživatele `AcceptRequests` obnovit přijímá žádosti, protože server už je ohrožena útoky založenými na kolekci úplného uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="67e9c-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="67e9c-153">Tato akce se simuluje nastavení `bAllocate` proměnnou `true` tak, aby objekty může pokračovat, který se přidává do <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="67e9c-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="67e9c-154">Obsahuje následující kód `Main` metoda v příkladu.</span><span class="sxs-lookup"><span data-stu-id="67e9c-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="67e9c-155">Obsahuje následující kód `WaitForFullGCProc` metoda uživatele, který obsahuje nepřetržitou při opakování ve smyčce bude kontrolovat oznámení pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="67e9c-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="67e9c-156">Obsahuje následující kód `OnFullGCApproachNotify` metoda, jak volat z</span><span class="sxs-lookup"><span data-stu-id="67e9c-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="67e9c-157">`WaitForFullGCProc` Metoda.</span><span class="sxs-lookup"><span data-stu-id="67e9c-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="67e9c-158">Obsahuje následující kód `OnFullGCApproachComplete` metoda, jak volat z</span><span class="sxs-lookup"><span data-stu-id="67e9c-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="67e9c-159">`WaitForFullGCProc` Metoda.</span><span class="sxs-lookup"><span data-stu-id="67e9c-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="67e9c-160">Následující kód obsahuje metody uživatele, které se nazývají z `OnFullGCApproachNotify` a `OnFullGCCompleteNotify` metody.</span><span class="sxs-lookup"><span data-stu-id="67e9c-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="67e9c-161">Metody uživatele přesměrovat požadavky, existující žádosti o dokončení a poté obnovit požadavky po úplné uvolnění paměti došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="67e9c-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="67e9c-162">Ukázka celý kódu vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="67e9c-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="67e9c-163">Viz také</span><span class="sxs-lookup"><span data-stu-id="67e9c-163">See Also</span></span>  
 [<span data-ttu-id="67e9c-164">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="67e9c-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
