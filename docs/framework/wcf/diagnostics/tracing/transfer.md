---
title: Přenos
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: aa7535aa393544077a9802b5c3255d6e5f6accda
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33802997"
---
# <a name="transfer"></a><span data-ttu-id="4ca21-102">Přenos</span><span class="sxs-lookup"><span data-stu-id="4ca21-102">Transfer</span></span>
<span data-ttu-id="4ca21-103">Toto téma popisuje přenosu v modelu trasování aktivity Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4ca21-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="4ca21-104">Definice přenosu</span><span class="sxs-lookup"><span data-stu-id="4ca21-104">Transfer Definition</span></span>  
 <span data-ttu-id="4ca21-105">Přenosy mezi aktivitami představují příčinnou vztahy mezi událostmi v souvisejících činností v rámci koncové body.</span><span class="sxs-lookup"><span data-stu-id="4ca21-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="4ca21-106">Dvě aktivity souvisejí s přenosy při řízení toků mezi tyto aktivity, například volání metody při překročení hranice aktivity.</span><span class="sxs-lookup"><span data-stu-id="4ca21-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="4ca21-107">Ve WCF když bajtů je příchozí na službu, aktivity naslouchat na jsou přeneseny do aktivity přijímat bajtů kde se má vytvořit objekt zprávy.</span><span class="sxs-lookup"><span data-stu-id="4ca21-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="4ca21-108">Seznam trasování začátku do konce scénáře a jejich odpovídající aktivitu a trasování návrhu najdete v tématu [scénáře trasování začátku do konce](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="4ca21-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="4ca21-109">Chcete-li emitování přenos trasování, použijte `ActivityTracing` nastavení na zdroj trasování, jak je ukázáno v následujícím kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4ca21-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="4ca21-110">Pomocí přenosu ke korelaci aktivity v rámci koncové body</span><span class="sxs-lookup"><span data-stu-id="4ca21-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="4ca21-111">Aktivity a přenosy povolit uživatelům probabilistically najít hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="4ca21-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="4ca21-112">Pokud jsme přenosu přepínat mezi aktivitami M a N v uvedeném pořadí v součásti M a N a havárie se stane v pravé N po přenos zpět do M, jsme zakreslit závěru, že je pravděpodobně způsobená N pro předávání dat zpět na M.</span><span class="sxs-lookup"><span data-stu-id="4ca21-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="4ca21-113">Přenos trasování nevydává aktivity M aktivity N po toku řízení mezi M a N. Například N provádí některé pracovní pro M z důvodu překročení meze aktivit hranice volání metody.</span><span class="sxs-lookup"><span data-stu-id="4ca21-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="4ca21-114">N možná již existuje nebo byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="4ca21-114">N may already exist or has been created.</span></span> <span data-ttu-id="4ca21-115">N je vytvořený službou M po N nová aktivita, která provádí některé pracovní pro M.</span><span class="sxs-lookup"><span data-stu-id="4ca21-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="4ca21-116">Přenos z M k N nesmí následovat přenos zpět z N až M. Je to proto, že se mohou provést některé pracovní v N M a není sledovat, kdy N dokončí svou práci.</span><span class="sxs-lookup"><span data-stu-id="4ca21-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="4ca21-117">Ve skutečnosti M můžete ukončit předtím, než N dokončení úkolu.</span><span class="sxs-lookup"><span data-stu-id="4ca21-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="4ca21-118">K tomu dochází v aktivitě "Otevřete ServiceHost" (M), který vytvoří naslouchací proces aktivity (ne) a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="4ca21-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="4ca21-119">Přenos zpět z N až M znamená, že N dokončení práce související s M.</span><span class="sxs-lookup"><span data-stu-id="4ca21-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="4ca21-120">N můžete pokračovat v provádění další zpracování, které nejsou v relaci M, například stávající ověřovací aktivitu (ne), která udržuje přijímání žádostí o přihlášení (M) z jiné přihlašovací údaje aktivit.</span><span class="sxs-lookup"><span data-stu-id="4ca21-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="4ca21-121">Vnoření relace neexistuje nutně mezi aktivitami M a N. K tomu dochází z důvodu ze dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="4ca21-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="4ca21-122">První, když aktivita M nesleduje vlastní zpracování prováděla N i když iniciované M N. Druhá, když N již existuje.</span><span class="sxs-lookup"><span data-stu-id="4ca21-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="4ca21-123">Příklad přenosů</span><span class="sxs-lookup"><span data-stu-id="4ca21-123">Example of Transfers</span></span>  
 <span data-ttu-id="4ca21-124">Následující seznamy dva přenos příklady.</span><span class="sxs-lookup"><span data-stu-id="4ca21-124">The following lists two transfer examples.</span></span>  
  
-   <span data-ttu-id="4ca21-125">Při vytváření hostitele služby konstruktoru získá kontrolu z volající kód nebo kód volání přenáší do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="4ca21-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="4ca21-126">Po dokončení provádění konstruktoru volající kód vrátí ovládací prvek nebo konstruktoru přenáší zpět do volání kódu.</span><span class="sxs-lookup"><span data-stu-id="4ca21-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="4ca21-127">Toto je případ vnořené relace.</span><span class="sxs-lookup"><span data-stu-id="4ca21-127">This is the case of a nested relationship.</span></span>  
  
-   <span data-ttu-id="4ca21-128">Při spuštění zpracování přenosu dat naslouchací proces vytvoří nové vlákno a předá aktivitě přijímat bajtů odpovídající kontext pro zpracování a předání řízení a data.</span><span class="sxs-lookup"><span data-stu-id="4ca21-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="4ca21-129">Po dokončení zpracování požadavku daném vláknu aktivity přijímat bajtů nic předá zpět do naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="4ca21-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="4ca21-130">V takovém případě máme přenos v, ale žádný přenos mimo nová aktivita přístup z více vláken.</span><span class="sxs-lookup"><span data-stu-id="4ca21-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="4ca21-131">Dvě aktivity spolu souvisejí, ale není vnořený.</span><span class="sxs-lookup"><span data-stu-id="4ca21-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="4ca21-132">Pořadí aktivit přenosu</span><span class="sxs-lookup"><span data-stu-id="4ca21-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="4ca21-133">Posloupnost aktivit ve správném formátu přenos zahrnuje následující kroky.</span><span class="sxs-lookup"><span data-stu-id="4ca21-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1.  <span data-ttu-id="4ca21-134">Začněte novou aktivitu, který se skládá z výběru nové gAId.</span><span class="sxs-lookup"><span data-stu-id="4ca21-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2.  <span data-ttu-id="4ca21-135">Emitování přenos trasování do této nové gAId z ID aktuální aktivity</span><span class="sxs-lookup"><span data-stu-id="4ca21-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3.  <span data-ttu-id="4ca21-136">Nastavit nové ID v protokolu TLS</span><span class="sxs-lookup"><span data-stu-id="4ca21-136">Set the new ID in TLS</span></span>  
  
4.  <span data-ttu-id="4ca21-137">Emitování počáteční trasování označující začátek nové aktivity podle.</span><span class="sxs-lookup"><span data-stu-id="4ca21-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5.  <span data-ttu-id="4ca21-138">Vraťte se do původního aktivity se skládá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="4ca21-138">Return to the original activity consists of the following:</span></span>  
  
6.  <span data-ttu-id="4ca21-139">Emitování trasování do třídy přenosu původní gAId</span><span class="sxs-lookup"><span data-stu-id="4ca21-139">Emit a transfer trace to the original gAId</span></span>  
  
7.  <span data-ttu-id="4ca21-140">Emitování Zastavit trasování k označení konce nová aktivita</span><span class="sxs-lookup"><span data-stu-id="4ca21-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8.  <span data-ttu-id="4ca21-141">Nastavit starý gAId TLS.</span><span class="sxs-lookup"><span data-stu-id="4ca21-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="4ca21-142">Následující příklad kódu ukazuje, jak to udělat.</span><span class="sxs-lookup"><span data-stu-id="4ca21-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="4ca21-143">Tato ukázka předpokládá blokování volání, provádí při přenosu do nová aktivita a zahrnuje pozastavení nebo obnovení činnosti trasování.</span><span class="sxs-lookup"><span data-stu-id="4ca21-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="4ca21-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="4ca21-144">See Also</span></span>  
 [<span data-ttu-id="4ca21-145">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="4ca21-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="4ca21-146">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="4ca21-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="4ca21-147">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="4ca21-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="4ca21-148">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="4ca21-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
