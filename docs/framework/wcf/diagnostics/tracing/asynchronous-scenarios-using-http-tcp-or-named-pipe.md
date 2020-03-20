---
title: Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 6ae96c0aac5010adf37eb78ed57d1549885ece58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185788"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a><span data-ttu-id="5e3dc-102">Asynchronní scénáře použití HTTP, TCP nebo pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="5e3dc-102">Asynchronous Scenarios using HTTP, TCP, or Named-Pipe</span></span>
<span data-ttu-id="5e3dc-103">Toto téma popisuje aktivity a přenosy pro různé scénáře asynchronní požadavek/odpověď s vícevláknové požadavky pomocí HTTP, TCP nebo pojmenované kanálu.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-103">This topic describes the activities and transfers for different asynchronous request/reply scenarios, with multithreaded requests using HTTP, TCP, or named pipe.</span></span>  
  
## <a name="asynchronous-requestreply-without-errors"></a><span data-ttu-id="5e3dc-104">Asynchronní požadavek/odpověď bez chyb</span><span class="sxs-lookup"><span data-stu-id="5e3dc-104">Asynchronous Request/Reply without Errors</span></span>  
 <span data-ttu-id="5e3dc-105">Tato část popisuje aktivity a přenosy pro scénář asynchronní požadavek/odpověď s vícevláknovými klienty.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-105">This section describes the activities and transfers for an asynchronous request/reply scenario, with multithreaded clients.</span></span>  
  
 <span data-ttu-id="5e3dc-106">Volající aktivita ukončí, `beginCall` když `endCall` vrátí a vrátí.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-106">The caller activity terminates when `beginCall` returns, and `endCall` returns.</span></span> <span data-ttu-id="5e3dc-107">Pokud je voláno zpětné volání, vrátí zpětné volání.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-107">If a callback is called, the callback returns.</span></span>  
  
 <span data-ttu-id="5e3dc-108">Volaná aktivita `beginCall` končí, když vrátí, `endCall` vrátí nebo když zpětné volání vrátí, pokud byla volána z této aktivity.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-108">The called activity terminates when `beginCall` returns, `endCall` returns, or when the callback returns if it was called from that activity.</span></span>  
  
### <a name="asynchronous-client-without-callback"></a><span data-ttu-id="5e3dc-109">Asynchronní klient bez zpětného volání</span><span class="sxs-lookup"><span data-stu-id="5e3dc-109">Asynchronous Client without Callback</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a><span data-ttu-id="5e3dc-110">Šíření je povoleno na obou stranách pomocí protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="5e3dc-110">Propagation is Enabled on Both Sides, using HTTP</span></span>  
 ![Asynchronní klient bez zpětného volání, kde je propagateActivity nastavena na hodnotu true na obou stranách.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 <span data-ttu-id="5e3dc-112">If `propagateActivity=true`, ProcessMessage označuje, které ProcessAction aktivity k přenosu.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-112">If `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
 <span data-ttu-id="5e3dc-113">Pro scénáře založené na protokolu HTTP ReceiveBytes je vyvolána na první zprávu odeslat a existuje po dobu životnosti požadavku.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-113">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a><span data-ttu-id="5e3dc-114">Šíření je zakázáno na obou stranách pomocí protokolu HTTP</span><span class="sxs-lookup"><span data-stu-id="5e3dc-114">Propagation is Disabled on Either Sides, using HTTP</span></span>  
 <span data-ttu-id="5e3dc-115">Pokud `propagateActivity=false` na obou stranách ProcessMessage neoznačuje, které ProcessAction aktivity k přenosu.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-115">If `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="5e3dc-116">Proto je vyvolána nová dočasná aktivita ProcessAction s novým ID.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-116">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="5e3dc-117">Pokud je asynchronní odpověď spárována s požadavkem v kódu ServiceModel, id aktivity lze načíst z místního kontextu.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-117">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="5e3dc-118">Skutečná aktivita ProcessAction může být převedena na s tímto ID.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-118">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Asynchronní klient bez zpětného volání, kde je propagateActivity nastavena na false na obou stranách.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 <span data-ttu-id="5e3dc-120">Pro scénáře založené na protokolu HTTP ReceiveBytes je vyvolána na první zprávu odeslat a existuje po dobu životnosti požadavku.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-120">For HTTP-based scenarios, ReceiveBytes is invoked on the first message to send, and exists for the lifetime of the request.</span></span>  
  
 <span data-ttu-id="5e3dc-121">Aktivita akce procesu je vytvořena na `propagateActivity=false` asynchronního klienta, když na volajícího nebo volaný, a když zpráva odpovědi neobsahuje hlavičku akce.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-121">A Process Action activity is created on an asynchronous client when `propagateActivity=false` at the caller or callee, and when the response message does not include an Action header.</span></span>  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="5e3dc-122">Šíření je povoleno na obou stranách pomocí protokolu TCP nebo pojmenovaného kanálu</span><span class="sxs-lookup"><span data-stu-id="5e3dc-122">Propagation is Enabled on Both Sides, using TCP or Named Pipe</span></span>  
 ![Asynchronní klient bez zpětného volání, kde je propagateActivity nastavena na hodnotu true na obou stranách a pojmenovaný kanál/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 <span data-ttu-id="5e3dc-124">Pro scénář založený na pojmenovaném kanálu nebo TCP receivebytes je vyvolána při otevření klienta a existuje po dobu životnosti připojení.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-124">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="5e3dc-125">Podobně jako první obrázek, if `propagateActivity=true`, ProcessMessage označuje, které ProcessAction aktivity k přenosu.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-125">Similar to the first image, if `propagateActivity=true`, ProcessMessage indicates which ProcessAction activity to transfer to.</span></span>  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a><span data-ttu-id="5e3dc-126">Šíření je zakázáno na obou stranách pomocí protokolu TCP nebo pojmenovaného kanálu.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-126">Propagation is Disabled on Either Sides, using TCP or Named Pipe</span></span>  
 <span data-ttu-id="5e3dc-127">Pro scénář založený na pojmenovaném kanálu nebo TCP receivebytes je vyvolána při otevření klienta a existuje po dobu životnosti připojení.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-127">For a Named-Pipe or TCP-based scenario, ReceiveBytes is invoked when the client is opened, and exists for the lifetime of the connection.</span></span>  
  
 <span data-ttu-id="5e3dc-128">Podobně jako druhý obrázek, pokud `propagateActivity=false` na obou stranách ProcessMessage neoznačuje, které ProcessAction aktivity k přenosu.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-128">Similar to the second image, if `propagateActivity=false` on either side, ProcessMessage does not indicate which ProcessAction activity to transfer to.</span></span> <span data-ttu-id="5e3dc-129">Proto je vyvolána nová dočasná aktivita ProcessAction s novým ID.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-129">Therefore, a new temporary ProcessAction activity with a new ID is invoked.</span></span> <span data-ttu-id="5e3dc-130">Pokud je asynchronní odpověď spárována s požadavkem v kódu ServiceModel, id aktivity lze načíst z místního kontextu.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-130">When the asynchronous response is matched to the request in ServiceModel code, the Activity ID can be retrieved from the local context.</span></span> <span data-ttu-id="5e3dc-131">Skutečná aktivita ProcessAction může být převedena na s tímto ID.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-131">The actual ProcessAction activity can be transferred to with that ID.</span></span>  
  
 ![Asynchronní klient bez zpětného volání, kde je propagateActivity nastavena na false na obou stranách a pojmenované kanálu/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a><span data-ttu-id="5e3dc-133">Asynchronní klient s zpětným voláním</span><span class="sxs-lookup"><span data-stu-id="5e3dc-133">Asynchronous client with Callback</span></span>  
 <span data-ttu-id="5e3dc-134">Tento scénář přidá aktivity G a A', pro zpětné volání a `endCall`, a jejich převody dovnitř / ven.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-134">This scenario adds activities G and A’, for the callback and `endCall`, and their transfers in/out.</span></span>  
  
 <span data-ttu-id="5e3dc-135">Tato část ukazuje pouze `propagateActivity` = `true`pomocí protokolu HTTP s .</span><span class="sxs-lookup"><span data-stu-id="5e3dc-135">This section only demonstrates using HTTP with `propagateActivity`=`true`.</span></span> <span data-ttu-id="5e3dc-136">Další aktivity a převody se však vztahují `propagateActivity` = `false`také na ostatní případy (tj. pomocí protokolu TCP nebo pojmenovaného kanálu).</span><span class="sxs-lookup"><span data-stu-id="5e3dc-136">However, the additional activities and transfers also apply to the other cases (that is, `propagateActivity`=`false`, using TCP or Named-Pipe).</span></span>  
  
 <span data-ttu-id="5e3dc-137">Zpětné volání vytvoří novou aktivitu (G), když klient volá uživatelský kód upozornit, že výsledky jsou připraveny.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-137">The callback creates a new activity (G) when the client calls user code to notify that results are ready.</span></span> <span data-ttu-id="5e3dc-138">Uživatelský kód `endCall` pak volá v rámci zpětného volání (jak je znázorněno na obrázku 5) nebo mimo zpětné volání (obrázek 6).</span><span class="sxs-lookup"><span data-stu-id="5e3dc-138">User code then calls `endCall` within the callback (as shown in Figure 5) or outside the callback (Figure 6).</span></span> <span data-ttu-id="5e3dc-139">Vzhledem k tomu, `endCall` že není známo, ze které `A’`aktivity uživatele je volána, je tato aktivita označena .</span><span class="sxs-lookup"><span data-stu-id="5e3dc-139">Because it is not known which user activity `endCall` is being called from, this activity is labeled `A’`.</span></span> <span data-ttu-id="5e3dc-140">Je možné, že A' může být totožný nebo odlišný od A.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-140">It is possible that A’ can be identical to or different from A.</span></span>  
  
 ![Zobrazuje asynchronního klienta s zpětným voláním, endcall v zpětném volání.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Zobrazuje asynchronního klienta s zpětným voláním, endcall mimo zpětné volání.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a><span data-ttu-id="5e3dc-143">Asynchronní server s zpětným voláním</span><span class="sxs-lookup"><span data-stu-id="5e3dc-143">Asynchronous Server with Callback</span></span>  
 ![Zobrazuje asynchronní server s zpětným voláním.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 <span data-ttu-id="5e3dc-145">Zásobník kanálu volá zpět klienta na přijetí zprávy: trasování pro toto zpracování jsou emitovány v samotné aktivitě ProcessRequest.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-145">The channel stack calls back the client on Message Receive: traces for this processing are emitted in the ProcessRequest activity itself.</span></span>  
  
## <a name="asynchronous-requestreply-with-errors"></a><span data-ttu-id="5e3dc-146">Asynchronní požadavek/odpověď s chybami</span><span class="sxs-lookup"><span data-stu-id="5e3dc-146">Asynchronous Request/Reply with Errors</span></span>  
 <span data-ttu-id="5e3dc-147">Během souboru jsou `endCall`přijímány chyby chyb</span><span class="sxs-lookup"><span data-stu-id="5e3dc-147">Fault message errors are received during `endCall`.</span></span> <span data-ttu-id="5e3dc-148">V opačném případě aktivity a převody jsou podobné předchozím scénářům.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-148">Otherwise, activities and transfers are similar to previous scenarios.</span></span>  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a><span data-ttu-id="5e3dc-149">Asynchronní jednosměrný s chybami nebo bez chyb</span><span class="sxs-lookup"><span data-stu-id="5e3dc-149">Asynchronous One-Way with or without Errors</span></span>  
 <span data-ttu-id="5e3dc-150">Klientovi není vrácena žádná odpověď ani chyba.</span><span class="sxs-lookup"><span data-stu-id="5e3dc-150">No response or fault is returned to the client.</span></span>
