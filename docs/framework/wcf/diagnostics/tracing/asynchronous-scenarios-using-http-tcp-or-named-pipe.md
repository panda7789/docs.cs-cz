---
title: "Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 76c4c225b333af6d376fa409a05ea5727ede6e8f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="da233-102">Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="da233-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="da233-103">Toto téma popisuje aktivity a přenosy pro různé Asynchronní požadavek nebo odpověď scénáře s více vlákny požadavky pomocí protokolu HTTP, TCP nebo pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="da233-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="da233-104">Asynchronní požadavek nebo odpověď bez chyb</span><span class="sxs-lookup"><span data-stu-id="da233-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="da233-105">Tato část popisuje aktivity a přenosy Asynchronní požadavek nebo odpověď scénář s více vlákny klienty.</span><span class="sxs-lookup"><span data-stu-id="da233-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="da233-106">Volající aktivity ukončí při `beginCall` vrátí, a `endCall` vrátí.</span><span class="sxs-lookup"><span data-stu-id="da233-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="da233-107">Pokud je volána zpětné volání, vrátí zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="da233-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="da233-108">Ukončí volané aktivity, kdy `beginCall` vrátí, `endCall` vrátí, nebo když zpětné volání vrátí, pokud byla volána z aktivity.</span><span class="sxs-lookup"><span data-stu-id="da233-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="da233-109">Asynchronní klienta bez zpětného volání</span><span class="sxs-lookup"><span data-stu-id="da233-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="da233-110">Bylo povoleno šíření na obou stranách, pomocí protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="da233-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 <span data-ttu-id="da233-111">![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span><span class="sxs-lookup"><span data-stu-id="da233-111">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asyn1.gif "Asyn1")</span></span>  
  
 <span data-ttu-id="da233-112">Obrázek 1.</span><span class="sxs-lookup"><span data-stu-id="da233-112">Figure 1.</span></span> <span data-ttu-id="da233-113">Asynchronní klienta, bez zpětného volání, `propagateActivity` = `true` na obou stranách HTTP</span><span class="sxs-lookup"><span data-stu-id="da233-113">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, HTTP</span></span>  
  
 <span data-ttu-id="da233-114">Pokud `propagateActivity` = `true`, ProcessMessage označuje, která ProcessAction aktivita se má přenést do.</span><span class="sxs-lookup"><span data-stu-id="da233-114">If `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="da233-115">Pro scénáře založené na protokolu HTTP, je vyvolána ReceiveBytes na první zprávu k odeslání a pro dobu životnosti požadavku existuje.</span><span class="sxs-lookup"><span data-stu-id="da233-115">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="da233-116">Propagace je zakázána na buď stranách, pomocí protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="da233-116">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="da233-117">Pokud `propagateActivity` = `false` na obou stranách ProcessMessage neindikuje která ProcessAction aktivita se má přenést do.</span><span class="sxs-lookup"><span data-stu-id="da233-117">If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="da233-118">Proto nové dočasné ProcessAction aktivitu se nové ID vyvolání.</span><span class="sxs-lookup"><span data-stu-id="da233-118">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="da233-119">Pokud požadavek na ServiceModel kód je nalezena shoda asynchronní odpovědi, ID aktivity lze načíst z lokální kontext.</span><span class="sxs-lookup"><span data-stu-id="da233-119">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="da233-120">Skutečné aktivity ProcessAction lze přesunout do s ID tohoto.</span><span class="sxs-lookup"><span data-stu-id="da233-120">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="da233-121">![Asynchronní scénáře použití HTTP &#47; TCP &#47; Pojmenovaný kanál](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span><span class="sxs-lookup"><span data-stu-id="da233-121">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async2.gif "Async2")</span></span>  
  
 <span data-ttu-id="da233-122">Obrázek 2.</span><span class="sxs-lookup"><span data-stu-id="da233-122">Figure 2.</span></span> <span data-ttu-id="da233-123">Asynchronní klienta, bez zpětného volání, `propagateActivity` = `false` na obou stranách HTTP</span><span class="sxs-lookup"><span data-stu-id="da233-123">Asynchronous client, no callback, `propagateActivity`=`false` on either side, HTTP</span></span>  
  
 <span data-ttu-id="da233-124">Pro scénáře založené na protokolu HTTP, je vyvolána ReceiveBytes na první zprávu k odeslání a pro dobu životnosti požadavku existuje.</span><span class="sxs-lookup"><span data-stu-id="da233-124">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="da233-125">Vytvoření procesu akce aktivity na asynchronní klienta při `propagateActivity` = `false` na volající nebo volaný a zprávu odpovědi nezahrnuje hlavičku akce.</span><span class="sxs-lookup"><span data-stu-id="da233-125">A Process Action activity is created on an asynchronous client when `propagateActivity`=`false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="da233-126">Bylo povoleno šíření na obou stranách, pomocí TCP nebo pojmenované kanály</span><span class="sxs-lookup"><span data-stu-id="da233-126">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="da233-127">![Asynchronní scénáře použití HTTP &#47; TCP &#47; Pojmenovaný kanál](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span><span class="sxs-lookup"><span data-stu-id="da233-127">![Asynchronous scenarios using HTTP&#47;TCP&#47;Named Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/async3.gif "Async3")</span></span>  
  
 <span data-ttu-id="da233-128">Obrázek 3.</span><span class="sxs-lookup"><span data-stu-id="da233-128">Figure 3.</span></span> <span data-ttu-id="da233-129">Asynchronní klienta, bez zpětného volání, `propagateActivity` = `true` na obou stranách pojmenovaný kanál/TCP</span><span class="sxs-lookup"><span data-stu-id="da233-129">Asynchronous client, no callback, `propagateActivity`=`true` on both sides, Named-Pipe/TCP</span></span>  
  
 <span data-ttu-id="da233-130">Pro scénář založený na TCP nebo pojmenované kanály ReceiveBytes je volána, když klient je otevřena a existuje pro životnost připojení.</span><span class="sxs-lookup"><span data-stu-id="da233-130">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="da233-131">Podobně jako obrázek 1, pokud `propagateActivity` = `true`, ProcessMessage označuje, která ProcessAction aktivita se má přenést do.</span><span class="sxs-lookup"><span data-stu-id="da233-131">Similar to Figure 1, if `propagateActivity`=`true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="da233-132">Propagace je zakázána na buď stranách, pomocí TCP nebo pojmenované kanály</span><span class="sxs-lookup"><span data-stu-id="da233-132">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="da233-133">Pro scénář založený na TCP nebo pojmenované kanály ReceiveBytes je volána, když klient je otevřena a existuje pro životnost připojení.</span><span class="sxs-lookup"><span data-stu-id="da233-133">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="da233-134">Podobně jako Fig.2, pokud `propagateActivity` = `false` na obou stranách ProcessMessage neindikuje která ProcessAction aktivita se má přenést do.</span><span class="sxs-lookup"><span data-stu-id="da233-134">Similar to Fig.2, If `propagateActivity`=`false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="da233-135">Proto nové dočasné ProcessAction aktivitu se nové ID vyvolání.</span><span class="sxs-lookup"><span data-stu-id="da233-135">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="da233-136">Pokud požadavek na ServiceModel kód je nalezena shoda asynchronní odpovědi, ID aktivity lze načíst z lokální kontext.</span><span class="sxs-lookup"><span data-stu-id="da233-136">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="da233-137">Skutečné aktivity ProcessAction lze přesunout do s ID tohoto.</span><span class="sxs-lookup"><span data-stu-id="da233-137">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 <span data-ttu-id="da233-138">![Asynchronní scénáře použití HTTP &#47; TCP &#47; Pojmenované kanály](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span><span class="sxs-lookup"><span data-stu-id="da233-138">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named Pipes](../../../../../docs/framework/wcf/diagnostics/tracing/media/async4.gif "Async4")</span></span>  
  
 <span data-ttu-id="da233-139">Obrázek 4.</span><span class="sxs-lookup"><span data-stu-id="da233-139">Figure 4.</span></span> <span data-ttu-id="da233-140">Asynchronní klienta, bez zpětného volání, `propagateActivity` = `false` na obou stranách pojmenovaný kanál/TCP</span><span class="sxs-lookup"><span data-stu-id="da233-140">Asynchronous client, no callback, `propagateActivity`=`false` on either side, Named-Pipe/TCP</span></span>  
  
### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="da233-141">Asynchronní klienta s zpětného volání</span><span class="sxs-lookup"><span data-stu-id="da233-141">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="da233-142">Tento scénář přidá aktivity G a A', pro zpětné volání a `endCall`a jejich přenosy vstup/výstup.</span><span class="sxs-lookup"><span data-stu-id="da233-142">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="da233-143">V této části ukážeme pouze pomocí protokolu HTTP s `propragateActivity` = `true`.</span><span class="sxs-lookup"><span data-stu-id="da233-143">This section only demonstrates using HTTP with `propragateActivity`=`true`.</span></span> <span data-ttu-id="da233-144">Však další aktivity a přenosy se rovněž vztahují na ostatních případech (tedy `propagateActivity` = `false`, pomocí TCP nebo pojmenované kanály).</span><span class="sxs-lookup"><span data-stu-id="da233-144">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="da233-145">Zpětné volání vytvoří novou aktivitu (G), když klient zavolá kód uživatele upozornit, že výsledky jsou připraveny.</span><span class="sxs-lookup"><span data-stu-id="da233-145">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="da233-146">Uživatelský kód pak zavolá `endCall` v rámci zpětného volání (jak je znázorněno na obrázku 5), nebo mimo zpětného volání (obrázek 6).</span><span class="sxs-lookup"><span data-stu-id="da233-146">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="da233-147">Protože není známo, která aktivita uživatele `endCall` je volána, tato aktivita označené `A’`.</span><span class="sxs-lookup"><span data-stu-id="da233-147">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="da233-148">Je možné, že A, může být stejný jako nebo liší od A.</span><span class="sxs-lookup"><span data-stu-id="da233-148">It is possible that A’ can be identical to or different from A.</span></span>  
  
 <span data-ttu-id="da233-149">![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span><span class="sxs-lookup"><span data-stu-id="da233-149">![Asynchronous scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback1.gif "AsyncCallback1")</span></span>  
  
 <span data-ttu-id="da233-150">Obrázek 5.</span><span class="sxs-lookup"><span data-stu-id="da233-150">Figure 5.</span></span> <span data-ttu-id="da233-151">Asynchronní klienta se zpětné volání, `endCall` v zpětného volání</span><span class="sxs-lookup"><span data-stu-id="da233-151">Asynchronous client with callback, `endCall` in Callback</span></span>  
  
 <span data-ttu-id="da233-152">![Asynchronní scénáře](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span><span class="sxs-lookup"><span data-stu-id="da233-152">![Asynchronous Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/media/asynccallback2.gif "AsyncCallback2")</span></span>  
  
 <span data-ttu-id="da233-153">Obrázek 6.</span><span class="sxs-lookup"><span data-stu-id="da233-153">Figure 6.</span></span> <span data-ttu-id="da233-154">Asynchronní klienta se zpětné volání, `endCall` mimo zpětného volání</span><span class="sxs-lookup"><span data-stu-id="da233-154">Asynchronous client with callback, `endCall` outside of Callback</span></span>  
  
### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="da233-155">Asynchronní Server s zpětného volání</span><span class="sxs-lookup"><span data-stu-id="da233-155">Asynchronous Server with Callback</span></span>  
 <span data-ttu-id="da233-156">![Asynchronní scénáře použití HTTP &#47; TCP &#47; S názvem & č. 45; Kanál](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span><span class="sxs-lookup"><span data-stu-id="da233-156">![Asynchronous scenarios using HTTP&#47;TCP&#47; Named&#45;Pipe](../../../../../docs/framework/wcf/diagnostics/tracing/media/aynchserver.gif "AynchServer")</span></span>  
  
 <span data-ttu-id="da233-157">Na obrázku 7.</span><span class="sxs-lookup"><span data-stu-id="da233-157">Figure 7.</span></span> <span data-ttu-id="da233-158">Asynchronní server s zpětného volání</span><span class="sxs-lookup"><span data-stu-id="da233-158">Asynchronous server, with callback</span></span>  
  
 <span data-ttu-id="da233-159">Kanál zásobníku volání zpět klientovi na příjem zpráv: trasování pro zpracování jsou vygenerované v aktivitě ProcessRequest sám sebe.</span><span class="sxs-lookup"><span data-stu-id="da233-159">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="da233-160">Asynchronní požadavek nebo odpověď s chybami</span><span class="sxs-lookup"><span data-stu-id="da233-160">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="da233-161">Přijme chybový zpráva chyby během `endCall`.</span><span class="sxs-lookup"><span data-stu-id="da233-161">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="da233-162">Jinak aktivity a přenosy jsou podobná předchozí scénáře.</span><span class="sxs-lookup"><span data-stu-id="da233-162">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="da233-163">Asynchronní jednosměrný s nebo bez chyby</span><span class="sxs-lookup"><span data-stu-id="da233-163">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="da233-164">Žádná odpověď nebo selhání je vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="da233-164">No response or fault is returned to the client.</span></span>
