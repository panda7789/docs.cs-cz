---
title: Přenos
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: 52b0cf35a2f8bab17252d3711f3143738c2bc39c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587765"
---
# <a name="transfer"></a><span data-ttu-id="847cf-102">Přenos</span><span class="sxs-lookup"><span data-stu-id="847cf-102">Transfer</span></span>
<span data-ttu-id="847cf-103">Toto téma popisuje přenos v modelu trasování aktivity Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="847cf-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="847cf-104">Definice přenosu</span><span class="sxs-lookup"><span data-stu-id="847cf-104">Transfer Definition</span></span>  
 <span data-ttu-id="847cf-105">Přenosy mezi aktivitami reprezentují příčinné vztahy mezi událostmi v souvisejících aktivitách v rámci koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="847cf-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="847cf-106">Dvě aktivity souvisejí s přenosy při řízení toků mezi těmito aktivitami, například volání metody přechází přes hranice aktivity.</span><span class="sxs-lookup"><span data-stu-id="847cf-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="847cf-107">Pokud jsou v rámci služby WCF Příchozí bajty na službu, je aktivita naslouchání v aktivitě přenesena do aktivity příjem bajtů, kde je objekt zprávy vytvořen.</span><span class="sxs-lookup"><span data-stu-id="847cf-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="847cf-108">Seznam kompletních scénářů trasování a jejich činnost a návrh trasování najdete v tématu [kompletní scénáře sledování](end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="847cf-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="847cf-109">Chcete-li vygenerovat trasování přenosu, použijte `ActivityTracing` nastavení ve zdroji trasování, jak je znázorněno v následujícím kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="847cf-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="847cf-110">Použití přenosu ke korelaci aktivit v rámci koncových bodů</span><span class="sxs-lookup"><span data-stu-id="847cf-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="847cf-111">Aktivity a přenosy umožňují uživateli probabilistically najít hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="847cf-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="847cf-112">Pokud například přenášíme mezi aktivitami M a N v komponentách M a N a dojde k selhání, dojde v N pravém okamžiku po převodu zpět na M, takže můžeme vykreslit závěr, že je pravděpodobný, aby se data back-N přenesla do M.</span><span class="sxs-lookup"><span data-stu-id="847cf-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="847cf-113">Trasování přenosu je vygenerováno z aktivity M k aktivitě N, pokud existuje tok řízení mezi M a N. Například N provede nějakou práci pro M, protože volání metody přebírá hranice aktivit.</span><span class="sxs-lookup"><span data-stu-id="847cf-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="847cf-114">N možná již existuje nebo byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="847cf-114">N may already exist or has been created.</span></span> <span data-ttu-id="847cf-115">N je založen na M, pokud N je nová aktivita, která provádí určitou práci pro M.</span><span class="sxs-lookup"><span data-stu-id="847cf-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="847cf-116">Přenos z M na N se nesmí následován přenosem zpátky z N do M. Důvodem je to, že M dokáže vytvořit určitou práci v N a Nesledovat, když N dokončí tuto práci.</span><span class="sxs-lookup"><span data-stu-id="847cf-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="847cf-117">Ve skutečnosti může M skončit, než N dokončí jeho úlohu.</span><span class="sxs-lookup"><span data-stu-id="847cf-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="847cf-118">K tomu dojde v aktivitě "Open ServiceHost" (M), která vytvoří aktivity naslouchacího procesu (N) a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="847cf-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="847cf-119">Přenos zpátky z N do M znamená, že N dokončila se práce související s M.</span><span class="sxs-lookup"><span data-stu-id="847cf-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="847cf-120">N může pokračovat v provádění jiných zpracování, které nesouvisí s M, například stávající aktivita ověřovatele (N), která udržuje požadavky na přihlášení (M) z různých přihlašovacích aktivit.</span><span class="sxs-lookup"><span data-stu-id="847cf-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="847cf-121">Vztah vnořování nemusí nutně existovat mezi aktivitami M a N. K tomu může dojít z důvodu dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="847cf-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="847cf-122">První, když aktivita M nemonitoruje skutečné zpracování provedené v N, i když M iniciované N. Sekunda, pokud N již existuje.</span><span class="sxs-lookup"><span data-stu-id="847cf-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="847cf-123">Příklad přenosů</span><span class="sxs-lookup"><span data-stu-id="847cf-123">Example of Transfers</span></span>  
 <span data-ttu-id="847cf-124">Následující seznam obsahuje dva příklady přenosu.</span><span class="sxs-lookup"><span data-stu-id="847cf-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="847cf-125">Při vytváření hostitele služby získá konstruktor řízení z volajícího kódu nebo volání přenese do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="847cf-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="847cf-126">Po dokončení zpracování konstruktoru vrátí řízení volajícímu kódu nebo konstruktor převede zpět na volající kód.</span><span class="sxs-lookup"><span data-stu-id="847cf-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="847cf-127">Toto je případ vnořené relace.</span><span class="sxs-lookup"><span data-stu-id="847cf-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="847cf-128">Když naslouchací proces spustí zpracování dat přenosu, vytvoří nové vlákno a zahodí se k aktivitě přijímání bajtů vhodným kontextem pro zpracování, předání řízení a dat.</span><span class="sxs-lookup"><span data-stu-id="847cf-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="847cf-129">Když vlákno dokončilo zpracování žádosti, aktivita přijetí bajtů předá do naslouchacího procesu nic zpátky.</span><span class="sxs-lookup"><span data-stu-id="847cf-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="847cf-130">V tomto případě máme přenos v systému, ale nemusíte ho přenést z nové aktivity vlákna.</span><span class="sxs-lookup"><span data-stu-id="847cf-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="847cf-131">Tyto dvě aktivity souvisejí, ale nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="847cf-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="847cf-132">Sekvence přenosu aktivity</span><span class="sxs-lookup"><span data-stu-id="847cf-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="847cf-133">Sekvence přenosu aktivit ve správném formátu zahrnuje následující kroky.</span><span class="sxs-lookup"><span data-stu-id="847cf-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="847cf-134">Zahájení nové aktivity, která se skládá z výběru nové gAId.</span><span class="sxs-lookup"><span data-stu-id="847cf-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="847cf-135">Vygeneruje ze stávajícího ID aktivity trasování přenosu pro tento nový gAId.</span><span class="sxs-lookup"><span data-stu-id="847cf-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="847cf-136">Nastavení nového ID v TLS</span><span class="sxs-lookup"><span data-stu-id="847cf-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="847cf-137">Vygenerujte počáteční trasování pro indikaci začátku nové aktivity.</span><span class="sxs-lookup"><span data-stu-id="847cf-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="847cf-138">Návrat k původní aktivitě se skládá z následujících:</span><span class="sxs-lookup"><span data-stu-id="847cf-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="847cf-139">Poslat trasování přenosu do původního gAIdu</span><span class="sxs-lookup"><span data-stu-id="847cf-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="847cf-140">Vygeneruje trasování stop k označení konce nové aktivity.</span><span class="sxs-lookup"><span data-stu-id="847cf-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="847cf-141">Nastavte TLS na starou gAId.</span><span class="sxs-lookup"><span data-stu-id="847cf-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="847cf-142">Následující příklad kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="847cf-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="847cf-143">Tato ukázka předpokládá, že při přesunu do nové aktivity je provedeno blokující volání, včetně trasování pro pozastavení/obnovení.</span><span class="sxs-lookup"><span data-stu-id="847cf-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```csharp
// 0. Create a trace source  
TraceSource ts = new TraceSource("myTS");  

// 1. remember existing ("ambient") activity for clean up  
Guid oldGuid = Trace.CorrelationManager.ActivityId;  
// this will be our new activity  
Guid newGuid = Guid.NewGuid();

// 2. call transfer, indicating that we are switching to the new AID  
ts.TraceTransfer(667, "Transferring.", newGuid);  

// 3. Suspend the current activity.  
ts.TraceEvent(TraceEventType.Suspend, 667, "Suspend: Activity " + i-1);  

// 4. set the new AID in TLS  
Trace.CorrelationManager.ActivityId = newGuid;  

// 5. Emit the start trace  
ts.TraceEvent(TraceEventType.Start, 667, "Boundary: Activity " + i);  

// trace something  
ts.TraceEvent(TraceEventType.Information, 667, "Hello from activity " + i);  

// Perform Work  
// some work.  
// Return  
ts.TraceEvent(TraceEventType.Information, 667, "Work complete on activity " + i);

// 6. Emit the transfer returning to the original activity  
ts.TraceTransfer(667, "Transferring Back.", oldGuid);  

// 7. Emit the End trace  
ts.TraceEvent(TraceEventType.Stop, 667, "Boundary: Activity " + i);  

// 8. Change the tls variable to the original AID  
Trace.CorrelationManager.ActivityId = oldGuid;

// 9. Resume the old activity  
ts.TraceEvent(TraceEventType.Resume, 667, "Resume: Activity " + i-1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="847cf-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="847cf-144">See also</span></span>

- [<span data-ttu-id="847cf-145">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="847cf-145">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="847cf-146">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="847cf-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="847cf-147">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="847cf-147">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="847cf-148">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="847cf-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
