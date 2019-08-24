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
ms.openlocfilehash: edf519621c2113843b89d96948243e9c095d2a57
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988865"
---
# <a name="garbage-collection-notifications"></a><span data-ttu-id="40b73-102">Oznámení pro kolekci paměti</span><span class="sxs-lookup"><span data-stu-id="40b73-102">Garbage Collection Notifications</span></span>
<span data-ttu-id="40b73-103">Existují situace, kdy úplné uvolňování paměti (tj. generace 2) modulem CLR (Common Language Runtime) může negativně ovlivnit výkon.</span><span class="sxs-lookup"><span data-stu-id="40b73-103">There are situations in which a full garbage collection (that is, a generation 2 collection) by the common language runtime may adversely affect performance.</span></span> <span data-ttu-id="40b73-104">To může být problém zejména u serverů, které zpracovávají velké objemy požadavků. v takovém případě může dlouhý uvolňování paměti způsobit časový limit požadavku. Aby se zabránilo úplnému výskytu celé kolekce v průběhu kritického období, můžete být upozorněni na přístup k úplnému uvolňování paměti a pak provést akci přesměrování úlohy na jinou instanci serveru.</span><span class="sxs-lookup"><span data-stu-id="40b73-104">This can be an issue particularly with servers that process large volumes of requests; in this case, a long garbage collection can cause a request time-out. To prevent a full collection from occurring during a critical period, you can be notified that a full garbage collection is approaching and then take action to redirect the workload to another server instance.</span></span> <span data-ttu-id="40b73-105">Kolekci můžete také vyvolat sami a za předpokladu, že aktuální instance serveru nemusí zpracovávat požadavky.</span><span class="sxs-lookup"><span data-stu-id="40b73-105">You can also induce a collection yourself, provided that the current server instance does not need to process requests.</span></span>  
  
 <span data-ttu-id="40b73-106"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda zaregistruje oznámení, které se vygeneruje v případě, že je k disjetí kompletní uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="40b73-106">The <xref:System.GC.RegisterForFullGCNotification%2A> method registers for a notification to be raised when the runtime senses that a full garbage collection is approaching.</span></span> <span data-ttu-id="40b73-107">Toto oznámení obsahuje dvě části: při přístupu k úplnému uvolňování paměti a po dokončení úplného uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="40b73-107">There are two parts to this notification: when the full garbage collection is approaching and when the full garbage collection has completed.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="40b73-108">Pouze blokování uvolňování paměti vyvolává oznámení.</span><span class="sxs-lookup"><span data-stu-id="40b73-108">Only blocking garbage collections raise notifications.</span></span> <span data-ttu-id="40b73-109">Pokud je povolen prvek konfigurace [ \<> gcConcurrent](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) , nebudou uvolňování paměti na pozadí vyvolávat oznámení.</span><span class="sxs-lookup"><span data-stu-id="40b73-109">When the [\<gcConcurrent>](../../../docs/framework/configure-apps/file-schema/runtime/gcconcurrent-element.md) configuration element is enabled, background garbage collections will not raise notifications.</span></span>  
  
 <span data-ttu-id="40b73-110">Chcete-li zjistit, kdy bylo oznámení vyvoláno <xref:System.GC.WaitForFullGCApproach%2A> , <xref:System.GC.WaitForFullGCComplete%2A> použijte metody a.</span><span class="sxs-lookup"><span data-stu-id="40b73-110">To determine when a notification has been raised, use the <xref:System.GC.WaitForFullGCApproach%2A> and <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span> <span data-ttu-id="40b73-111">Obvykle tyto metody použijete ve `while` smyčce k průběžnému <xref:System.GCNotificationStatus> získávání výčtu, který zobrazuje stav oznámení.</span><span class="sxs-lookup"><span data-stu-id="40b73-111">Typically, you use these methods in a `while` loop to continually obtain a <xref:System.GCNotificationStatus> enumeration that shows the status of the notification.</span></span> <span data-ttu-id="40b73-112">Pokud je <xref:System.GCNotificationStatus.Succeeded>tato hodnota, můžete provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="40b73-112">If that value is <xref:System.GCNotificationStatus.Succeeded>, you can do the following:</span></span>  
  
- <span data-ttu-id="40b73-113">V reakci na oznámení získané s <xref:System.GC.WaitForFullGCApproach%2A> metodou můžete přesměrovat úlohu a případně vyvolávat kolekci sami.</span><span class="sxs-lookup"><span data-stu-id="40b73-113">In response to a notification obtained with the <xref:System.GC.WaitForFullGCApproach%2A> method, you can redirect the workload and possibly induce a collection yourself.</span></span>  
  
- <span data-ttu-id="40b73-114">V reakci na oznámení získané s <xref:System.GC.WaitForFullGCComplete%2A> metodou můžete nastavit, aby byla aktuální instance serveru k dispozici pro opětovné zpracování požadavků.</span><span class="sxs-lookup"><span data-stu-id="40b73-114">In response to a notification obtained with the <xref:System.GC.WaitForFullGCComplete%2A> method, you can make the current server instance available to process requests again.</span></span> <span data-ttu-id="40b73-115">Můžete také shromažďovat informace.</span><span class="sxs-lookup"><span data-stu-id="40b73-115">You can also gather information.</span></span> <span data-ttu-id="40b73-116">Například můžete použít <xref:System.GC.CollectionCount%2A> metodu k zaznamenání počtu kolekcí.</span><span class="sxs-lookup"><span data-stu-id="40b73-116">For example, you can use the <xref:System.GC.CollectionCount%2A> method to record the number of collections.</span></span>  
  
 <span data-ttu-id="40b73-117">Metody<xref:System.GC.WaitForFullGCComplete%2A>ajsou navržené tak, aby společně <xref:System.GC.WaitForFullGCApproach%2A> spolupracovaly.</span><span class="sxs-lookup"><span data-stu-id="40b73-117">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods are designed to work together.</span></span> <span data-ttu-id="40b73-118">Použití jednoho bez druhého může způsobit neurčité výsledky.</span><span class="sxs-lookup"><span data-stu-id="40b73-118">Using one without the other can produce indeterminate results.</span></span>  
  
## <a name="full-garbage-collection"></a><span data-ttu-id="40b73-119">Úplné uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="40b73-119">Full Garbage Collection</span></span>  
 <span data-ttu-id="40b73-120">Modul runtime způsobuje úplné uvolňování paměti v případě, kdy platí kterýkoli z následujících scénářů:</span><span class="sxs-lookup"><span data-stu-id="40b73-120">The runtime causes a full garbage collection when any of the following scenarios are true:</span></span>  
  
- <span data-ttu-id="40b73-121">Dostatek paměti bylo povýšeno na generaci 2 a způsobilo novou kolekci 2. generace.</span><span class="sxs-lookup"><span data-stu-id="40b73-121">Enough memory has been promoted into generation 2 to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="40b73-122">Do haldy velkých objektů bylo povýšeno dostatečné množství paměti, které způsobí novou kolekci 2. generace.</span><span class="sxs-lookup"><span data-stu-id="40b73-122">Enough memory has been promoted into the large object heap to cause the next generation 2 collection.</span></span>  
  
- <span data-ttu-id="40b73-123">Kolekce 1. generace je eskalace z kolekce 2. generace z důvodu jiných faktorů.</span><span class="sxs-lookup"><span data-stu-id="40b73-123">A collection of generation 1 is escalated to a collection of generation 2 due to other factors.</span></span>  
  
 <span data-ttu-id="40b73-124">Prahové hodnoty, které zadáte v <xref:System.GC.RegisterForFullGCNotification%2A> metodě, se vztahují na první dva scénáře.</span><span class="sxs-lookup"><span data-stu-id="40b73-124">The thresholds you specify in the <xref:System.GC.RegisterForFullGCNotification%2A> method apply to the first two scenarios.</span></span> <span data-ttu-id="40b73-125">V prvním scénáři ale nebudete vždy dostávat oznámení v čase, který je úměrný prahovým hodnotám, které zadáte, ze dvou důvodů:</span><span class="sxs-lookup"><span data-stu-id="40b73-125">However, in the first scenario you will not always receive the notification at the time proportional to the threshold values you specify for two reasons:</span></span>  
  
- <span data-ttu-id="40b73-126">Modul runtime nekontroluje každé přidělení malých objektů (z důvodů výkonu).</span><span class="sxs-lookup"><span data-stu-id="40b73-126">The runtime does not check each small object allocation (for performance reasons).</span></span>  
  
- <span data-ttu-id="40b73-127">Pouze kolekce 1. generace přivýší paměť do generace 2.</span><span class="sxs-lookup"><span data-stu-id="40b73-127">Only generation 1 collections promote memory into generation 2.</span></span>  
  
 <span data-ttu-id="40b73-128">Třetí scénář také přispívá k nejistotě, kdy obdržíte oznámení.</span><span class="sxs-lookup"><span data-stu-id="40b73-128">The third scenario also contributes to the uncertainty of when you will receive the notification.</span></span> <span data-ttu-id="40b73-129">I když se nejedná o záruku, ukáže se to jako užitečný způsob, jak zmírnit důsledky neoprávněného uvolňování paměti tím, že se žádosti v této době přesměrují, nebo když kolekci vyvoláte sami, když se dá lépe přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="40b73-129">Although this is not a guarantee, it does prove to be a useful way to mitigate the effects of an inopportune full garbage collection by redirecting the requests during this time or inducing the collection yourself when it can be better accommodated.</span></span>  
  
## <a name="notification-threshold-parameters"></a><span data-ttu-id="40b73-130">Parametry prahové hodnoty oznámení</span><span class="sxs-lookup"><span data-stu-id="40b73-130">Notification Threshold Parameters</span></span>  
 <span data-ttu-id="40b73-131"><xref:System.GC.RegisterForFullGCNotification%2A> Metoda má dva parametry pro určení prahových hodnot objektů generace 2 a haldy velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="40b73-131">The <xref:System.GC.RegisterForFullGCNotification%2A> method has two parameters to specify the threshold values of the generation 2 objects and the large object heap.</span></span> <span data-ttu-id="40b73-132">Po splnění těchto hodnot by se mělo vyvolat oznámení o uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="40b73-132">When those values are met, a garbage collection notification should be raised.</span></span> <span data-ttu-id="40b73-133">Tyto parametry jsou popsány v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="40b73-133">The following table describes these parameters.</span></span>  
  
|<span data-ttu-id="40b73-134">Parametr</span><span class="sxs-lookup"><span data-stu-id="40b73-134">Parameter</span></span>|<span data-ttu-id="40b73-135">Popis</span><span class="sxs-lookup"><span data-stu-id="40b73-135">Description</span></span>|  
|---------------|-----------------|  
|`maxGenerationThreshold`|<span data-ttu-id="40b73-136">Číslo mezi 1 a 99, které určuje, kdy má být oznámení vyvoláno na základě objektů povýšených v generaci 2.</span><span class="sxs-lookup"><span data-stu-id="40b73-136">A number between 1 and 99 that specifies when the notification should be raised based on the objects promoted in generation 2.</span></span>|  
|`largeObjectHeapThreshold`|<span data-ttu-id="40b73-137">Číslo mezi 1 a 99, které určuje, kdy má být oznámení vyvoláno v závislosti na objektech, které jsou přiděleny v haldě velkých objektů.</span><span class="sxs-lookup"><span data-stu-id="40b73-137">A number between 1 and 99 that specifies when the notification should be raised based on the objects that are allocated in the large object heap.</span></span>|  
  
 <span data-ttu-id="40b73-138">Pokud zadáte hodnotu, která je příliš vysoká, dojde k vysoké pravděpodobnosti, že obdržíte oznámení, ale může být příliš dlouhé období, než modul runtime vyvolá kolekci.</span><span class="sxs-lookup"><span data-stu-id="40b73-138">If you specify a value that is too high, there is a high probability that you will receive a notification, but it could be too long a period to wait before the runtime causes a collection.</span></span> <span data-ttu-id="40b73-139">Pokud kolekci vyvoláte sami, můžete získat více objektů, než by byla uvolněna v případě, že modul runtime vyvolá kolekci.</span><span class="sxs-lookup"><span data-stu-id="40b73-139">If you induce a collection yourself, you may reclaim more objects than would be reclaimed if the runtime causes the collection.</span></span>  
  
 <span data-ttu-id="40b73-140">Pokud zadáte hodnotu, která je příliš nízká, modul runtime může tuto kolekci způsobit předtím, než bude dostatek času na oznámení.</span><span class="sxs-lookup"><span data-stu-id="40b73-140">If you specify a value that is too low, the runtime may cause the collection before you have had sufficient time to be notified.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40b73-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="40b73-141">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="40b73-142">Popis</span><span class="sxs-lookup"><span data-stu-id="40b73-142">Description</span></span>  
 <span data-ttu-id="40b73-143">V následujícím příkladu skupina serverů obsluhuje příchozí webové požadavky.</span><span class="sxs-lookup"><span data-stu-id="40b73-143">In the following example, a group of servers service incoming Web requests.</span></span> <span data-ttu-id="40b73-144">Chcete-li simulovat úlohy zpracování požadavků, Bajtová pole jsou přidána do <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="40b73-144">To simulate the workload of processing requests, byte arrays are added to a <xref:System.Collections.Generic.List%601> collection.</span></span> <span data-ttu-id="40b73-145">Každý server zaregistruje oznámení pro uvolňování paměti a potom spustí vlákno v `WaitForFullGCProc` metodě uživatele, aby nepřetržitě <xref:System.GCNotificationStatus> sledovalo výčet <xref:System.GC.WaitForFullGCApproach%2A> , který je <xref:System.GC.WaitForFullGCComplete%2A> vrácen metodou a metodou.</span><span class="sxs-lookup"><span data-stu-id="40b73-145">Each server registers for a garbage collection notification and then starts a thread on the `WaitForFullGCProc` user method to continuously monitor the <xref:System.GCNotificationStatus> enumeration that is returned by the <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods.</span></span>  
  
 <span data-ttu-id="40b73-146">Metody<xref:System.GC.WaitForFullGCComplete%2A>avolají při vyvolání oznámení příslušné metody pro zpracování událostí: <xref:System.GC.WaitForFullGCApproach%2A></span><span class="sxs-lookup"><span data-stu-id="40b73-146">The <xref:System.GC.WaitForFullGCApproach%2A> and the <xref:System.GC.WaitForFullGCComplete%2A> methods call their respective event-handling user methods when a notification is raised:</span></span>  
  
- `OnFullGCApproachNotify`  
  
     <span data-ttu-id="40b73-147">Tato metoda volá `RedirectRequests` metodu uživatele, která dává pokyn serveru služby Řízení front zpráv k pozastavení odesílání požadavků na server.</span><span class="sxs-lookup"><span data-stu-id="40b73-147">This method calls the `RedirectRequests` user method, which instructs the request queuing server to suspend sending requests to the server.</span></span> <span data-ttu-id="40b73-148">To je simulované nastavením proměnné `bAllocate` `false` na úrovni třídy tak, aby nebyly přiděleny žádné další objekty.</span><span class="sxs-lookup"><span data-stu-id="40b73-148">This is simulated by setting the class-level variable `bAllocate` to `false` so that no more objects are allocated.</span></span>  
  
     <span data-ttu-id="40b73-149">Dále je volána metoda uživatelekdokončenízpracovánípožadavkůnaserver,kteréčekajínavyřízení.`FinishExistingRequests`</span><span class="sxs-lookup"><span data-stu-id="40b73-149">Next, the `FinishExistingRequests` user method is called to finish processing the pending server requests.</span></span> <span data-ttu-id="40b73-150">To se simuluje vymazáním <xref:System.Collections.Generic.List%601> kolekce.</span><span class="sxs-lookup"><span data-stu-id="40b73-150">This is simulated by clearing the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
     <span data-ttu-id="40b73-151">Nakonec je vyvolaný uvolňování paměti, protože zatížení je lehké.</span><span class="sxs-lookup"><span data-stu-id="40b73-151">Finally, a garbage collection is induced because the workload is light.</span></span>  
  
- `OnFullGCCompleteNotify`  
  
     <span data-ttu-id="40b73-152">Tato metoda volá metodu `AcceptRequests` uživatele, aby obnovila přijímání požadavků, protože server již není náchylný k úplnému uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="40b73-152">This method calls the user method `AcceptRequests` to resume accepting requests because the server is no longer susceptible to a full garbage collection.</span></span> <span data-ttu-id="40b73-153">Tato akce je simulována nastavením `bAllocate` `true` proměnné tak, aby bylo možné <xref:System.Collections.Generic.List%601> obnovit objekty do kolekce.</span><span class="sxs-lookup"><span data-stu-id="40b73-153">This action is simulated by setting the `bAllocate` variable to `true` so that objects can resume being added to the <xref:System.Collections.Generic.List%601> collection.</span></span>  
  
 <span data-ttu-id="40b73-154">Následující kód obsahuje `Main` metodu příkladu.</span><span class="sxs-lookup"><span data-stu-id="40b73-154">The following code contains the `Main` method of the example.</span></span>  
  
 [!code-cpp[GCNotification#2](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#2)]
 [!code-csharp[GCNotification#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#2)]
 [!code-vb[GCNotification#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#2)]  
  
 <span data-ttu-id="40b73-155">Následující kód obsahuje `WaitForFullGCProc` metodu uživatele, která obsahuje nepřetržitou smyčku while ke kontrole oznámení o uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="40b73-155">The following code contains the `WaitForFullGCProc` user method, that contains a continuous while loop to check for garbage collection notifications.</span></span>  
  
 [!code-cpp[GCNotification#8](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#8)]
 [!code-csharp[GCNotification#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#8)]
 [!code-vb[GCNotification#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#8)]  
  
 <span data-ttu-id="40b73-156">Následující kód obsahuje `OnFullGCApproachNotify` metodu volanou z</span><span class="sxs-lookup"><span data-stu-id="40b73-156">The following code contains the `OnFullGCApproachNotify` method as called from the</span></span>  
  
 <span data-ttu-id="40b73-157">`WaitForFullGCProc`Metoda.</span><span class="sxs-lookup"><span data-stu-id="40b73-157">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#5](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#5)]
 [!code-csharp[GCNotification#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#5)]
 [!code-vb[GCNotification#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#5)]  
  
 <span data-ttu-id="40b73-158">Následující kód obsahuje `OnFullGCApproachComplete` metodu volanou z</span><span class="sxs-lookup"><span data-stu-id="40b73-158">The following code contains the `OnFullGCApproachComplete` method as called from the</span></span>  
  
 <span data-ttu-id="40b73-159">`WaitForFullGCProc`Metoda.</span><span class="sxs-lookup"><span data-stu-id="40b73-159">`WaitForFullGCProc` method.</span></span>  
  
 [!code-cpp[GCNotification#6](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#6)]
 [!code-csharp[GCNotification#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#6)]
 [!code-vb[GCNotification#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#6)]  
  
 <span data-ttu-id="40b73-160">Následující kód obsahuje uživatelské metody, které jsou volány z `OnFullGCApproachNotify` metod a. `OnFullGCCompleteNotify`</span><span class="sxs-lookup"><span data-stu-id="40b73-160">The following code contains the user methods that are called from the `OnFullGCApproachNotify` and `OnFullGCCompleteNotify` methods.</span></span> <span data-ttu-id="40b73-161">Metody uživatele přesměrují požadavky, dokončí stávající žádosti a pak obnoví požadavky po úplném uvolnění paměti.</span><span class="sxs-lookup"><span data-stu-id="40b73-161">The user methods redirect requests, finish existing requests, and then resume requests after a full garbage collection has occurred.</span></span>  
  
 [!code-cpp[GCNotification#9](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#9)]
 [!code-csharp[GCNotification#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#9)]
 [!code-vb[GCNotification#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#9)]  
  
 <span data-ttu-id="40b73-162">Celá ukázka kódu je následující:</span><span class="sxs-lookup"><span data-stu-id="40b73-162">The entire code sample is as follows:</span></span>  
  
 [!code-cpp[GCNotification#1](../../../samples/snippets/cpp/VS_Snippets_CLR/GCNotification/cpp/program.cpp#1)]
 [!code-csharp[GCNotification#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GCNotification/cs/Program.cs#1)]
 [!code-vb[GCNotification#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GCNotification/vb/program.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="40b73-163">Viz také:</span><span class="sxs-lookup"><span data-stu-id="40b73-163">See also</span></span>

- [<span data-ttu-id="40b73-164">Uvolňování paměti</span><span class="sxs-lookup"><span data-stu-id="40b73-164">Garbage Collection</span></span>](../../../docs/standard/garbage-collection/index.md)
