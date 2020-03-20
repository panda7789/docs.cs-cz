---
title: Přenos
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: e0ebfff97cd33e7a588a1ab92399a97a0fbec039
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185709"
---
# <a name="transfer"></a><span data-ttu-id="f0995-102">Přenos</span><span class="sxs-lookup"><span data-stu-id="f0995-102">Transfer</span></span>
<span data-ttu-id="f0995-103">Toto téma popisuje přenos v modelu trasování aktivity Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="f0995-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="f0995-104">Definice přenosu</span><span class="sxs-lookup"><span data-stu-id="f0995-104">Transfer Definition</span></span>  
 <span data-ttu-id="f0995-105">Přenosy mezi aktivitami představují příčinné vztahy mezi událostmi v souvisejících aktivitách v rámci koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="f0995-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="f0995-106">Dvě aktivity souvisejí s přenosy při řízení toků mezi těmito aktivitami, například volání metody překračování hranic aktivity.</span><span class="sxs-lookup"><span data-stu-id="f0995-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="f0995-107">V WCF při bajtů jsou příchozí na službu, listen at aktivita je převedena na příjem bajtů aktivity, kde je vytvořen objekt zprávy.</span><span class="sxs-lookup"><span data-stu-id="f0995-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="f0995-108">Seznam scénářů trasování od konce a jejich příslušné aktivity a návrh trasování naleznete v [tématu Scénáře trasování mezi koncovými místy](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="f0995-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="f0995-109">Chcete-li vyzařovat trasování `ActivityTracing` přenosu, použijte nastavení na zdroji trasování, jak je znázorněno následujícím konfiguračním kódem.</span><span class="sxs-lookup"><span data-stu-id="f0995-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="f0995-110">Použití přenosu ke korelaci aktivit v rámci koncových bodů</span><span class="sxs-lookup"><span data-stu-id="f0995-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="f0995-111">Aktivity a převody umožňují uživateli probabilistically vyhledat hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="f0995-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="f0995-112">Například pokud přenášíme tam a zpět mezi aktivitami M a N v součástech M a N a k chybě dojde v N hned po převodu zpět na M, můžeme vyvodit závěr, že je to pravděpodobně způsobeno předáváním dat N zpět do M.</span><span class="sxs-lookup"><span data-stu-id="f0995-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="f0995-113">Trasování přenosu je emitován z aktivity M do aktivity N, pokud je tok řízení mezi M a N. Například N provádí některé práce pro M z důvodu volání metody překročení hranice aktivity.</span><span class="sxs-lookup"><span data-stu-id="f0995-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="f0995-114">N již může existovat nebo byla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="f0995-114">N may already exist or has been created.</span></span> <span data-ttu-id="f0995-115">N je zplozena M, když N je nová aktivita, která provádí některé práce pro M.</span><span class="sxs-lookup"><span data-stu-id="f0995-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="f0995-116">Po převodu z M na N nesmí následovat převod zpět z N do M. Důvodem je, že M může plodit nějakou práci v N a nesledovat, když N dokončí tuto práci.</span><span class="sxs-lookup"><span data-stu-id="f0995-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="f0995-117">Ve skutečnosti M může ukončit před N dokončí svůj úkol.</span><span class="sxs-lookup"><span data-stu-id="f0995-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="f0995-118">K tomu dochází v aktivitě "Open ServiceHost" (M), která spouští aktivity posluchače (N) a pak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="f0995-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="f0995-119">Převod zpět z N na M znamená, že N dokončil práci související s M.</span><span class="sxs-lookup"><span data-stu-id="f0995-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="f0995-120">N můžete pokračovat v provádění jiné zpracování nesouvisí s M, například existující ověřovací aktivity (N), který udržuje příjem žádostí o přihlášení (M) z různých aktivit přihlášení.</span><span class="sxs-lookup"><span data-stu-id="f0995-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="f0995-121">Vztah vnoření nemusí nutně existovat mezi aktivitami M a N. K tomu může dojít ze dvou důvodů.</span><span class="sxs-lookup"><span data-stu-id="f0995-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="f0995-122">Za prvé, když aktivita M nesleduje skutečné zpracování provedené v N, i když M inicioval N. Za druhé, když N již existuje.</span><span class="sxs-lookup"><span data-stu-id="f0995-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="f0995-123">Příklad převodů</span><span class="sxs-lookup"><span data-stu-id="f0995-123">Example of Transfers</span></span>  
 <span data-ttu-id="f0995-124">V následujícím seznamu jsou uvedeny dva příklady přenosu.</span><span class="sxs-lookup"><span data-stu-id="f0995-124">The following lists two transfer examples.</span></span>  
  
- <span data-ttu-id="f0995-125">Při vytváření hostitele služby získá konstruktor ovládací prvek z volajícího kódu nebo volajícího kódu se přenese do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="f0995-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="f0995-126">Po dokončení provádění konstruktoru vrátí ovládací prvek volajícího kódu nebo konstruktor přenese zpět do volajícího kódu.</span><span class="sxs-lookup"><span data-stu-id="f0995-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="f0995-127">To je případ vnořeného vztahu.</span><span class="sxs-lookup"><span data-stu-id="f0995-127">This is the case of a nested relationship.</span></span>  
  
- <span data-ttu-id="f0995-128">Když naslouchací proces začne zpracovávat přenosová data, vytvoří nové vlákno a předává aktivitě Příjem bajtů vhodný kontext pro zpracování, předávání řízení a dat.</span><span class="sxs-lookup"><span data-stu-id="f0995-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="f0995-129">Po dokončení zpracování požadavku toto vlákno, příjem bajtů aktivity předává nic zpět naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="f0995-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="f0995-130">V tomto případě máme převod v, ale žádný převod z nové aktivity vlákna.</span><span class="sxs-lookup"><span data-stu-id="f0995-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="f0995-131">Dvě aktivity jsou související, ale nejsou vnořené.</span><span class="sxs-lookup"><span data-stu-id="f0995-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="f0995-132">Posloupnost přenosu aktivity</span><span class="sxs-lookup"><span data-stu-id="f0995-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="f0995-133">Dobře formátovaná sekvence přenosu aktivity zahrnuje následující kroky.</span><span class="sxs-lookup"><span data-stu-id="f0995-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1. <span data-ttu-id="f0995-134">Začněte novou aktivitu, která se skládá z výběru nového gAId.</span><span class="sxs-lookup"><span data-stu-id="f0995-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2. <span data-ttu-id="f0995-135">Vyzařují trasu přenosu do nového gAId z aktuálního ID aktivity.</span><span class="sxs-lookup"><span data-stu-id="f0995-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3. <span data-ttu-id="f0995-136">Nastavení nového ID v TLS</span><span class="sxs-lookup"><span data-stu-id="f0995-136">Set the new ID in TLS</span></span>  
  
4. <span data-ttu-id="f0995-137">Vyzařují počáteční trasování označující začátek nové aktivity.</span><span class="sxs-lookup"><span data-stu-id="f0995-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5. <span data-ttu-id="f0995-138">Návrat k původní činnosti se skládá z následujících:</span><span class="sxs-lookup"><span data-stu-id="f0995-138">Return to the original activity consists of the following:</span></span>  
  
6. <span data-ttu-id="f0995-139">Vyzařují trasu přenosu do původního gAId</span><span class="sxs-lookup"><span data-stu-id="f0995-139">Emit a transfer trace to the original gAId</span></span>  
  
7. <span data-ttu-id="f0995-140">Vyzařovat stopování stop, které označuje konec nové aktivity.</span><span class="sxs-lookup"><span data-stu-id="f0995-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8. <span data-ttu-id="f0995-141">Nastavte TLS na starý gAId.</span><span class="sxs-lookup"><span data-stu-id="f0995-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="f0995-142">Následující příklad kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="f0995-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="f0995-143">Tato ukázka předpokládá, že blokování volání je provedeno při přenosu do nové aktivity a zahrnuje stopy pozastavit nebo obnovit.</span><span class="sxs-lookup"><span data-stu-id="f0995-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0995-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0995-144">See also</span></span>

- [<span data-ttu-id="f0995-145">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="f0995-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="f0995-146">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="f0995-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="f0995-147">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="f0995-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="f0995-148">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="f0995-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
