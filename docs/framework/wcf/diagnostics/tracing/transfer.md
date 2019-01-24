---
title: Přenos
ms.date: 03/30/2017
ms.assetid: dfcfa36c-d3bb-44b4-aa15-1c922c6f73e6
ms.openlocfilehash: d6ca1f8471fb1513263354e2369891bf9ffcb583
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552917"
---
# <a name="transfer"></a><span data-ttu-id="b6cb0-102">Přenos</span><span class="sxs-lookup"><span data-stu-id="b6cb0-102">Transfer</span></span>
<span data-ttu-id="b6cb0-103">Toto téma popisuje přenosu v modelu trasování aktivity Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b6cb0-103">This topic describes transfer in the Windows Communication Foundation (WCF) activity tracing model.</span></span>  
  
## <a name="transfer-definition"></a><span data-ttu-id="b6cb0-104">Definice přenosu</span><span class="sxs-lookup"><span data-stu-id="b6cb0-104">Transfer Definition</span></span>  
 <span data-ttu-id="b6cb0-105">Přenosy mezi aktivitami představují příčinnou vztahy mezi událostmi v souvisejících činností v rámci koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-105">Transfers between activities represent causal relationships between events in the related activities within endpoints.</span></span> <span data-ttu-id="b6cb0-106">Dvě aktivity jsou propojeny s přenosy, když tok řízení mezi tyto aktivity, například volání metody přes hranice aktivity.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-106">Two activities are related with transfers when control flows between these activities, for example, a method call crossing activity boundaries.</span></span> <span data-ttu-id="b6cb0-107">Ve službě WCF když bajty příchozí službě, aktivita naslouchat na se přenesou do aktivity přijímání bajtů kde se vytvoří objekt zprávy.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-107">In WCF, when bytes are incoming on the service, the Listen At activity is transferred to the Receive Bytes activity where the message object is created.</span></span> <span data-ttu-id="b6cb0-108">Seznam scénáře trasování začátku do konce a jejich odpovídajících aktivit a trasování návrhu najdete v tématu [scénáře trasování začátku do konce](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span><span class="sxs-lookup"><span data-stu-id="b6cb0-108">For a list of end-to-end tracing scenarios, and their respective activity and tracing design, see [End-To-End Tracing Scenarios](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md).</span></span>  
  
 <span data-ttu-id="b6cb0-109">Chcete-li generovat přenos trasování, použijte `ActivityTracing` nastavení pro zdroj trasování, jak je ukázáno v následujícím kódu konfigurace.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-109">To emit transfer traces, use the `ActivityTracing` setting on the trace source as demonstrated by the following configuration code.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing">  
```  
  
## <a name="using-transfer-to-correlate-activities-within-endpoints"></a><span data-ttu-id="b6cb0-110">Pomocí přenosu v korelovat aktivity v rámci koncových bodů</span><span class="sxs-lookup"><span data-stu-id="b6cb0-110">Using Transfer to Correlate Activities Within Endpoints</span></span>  
 <span data-ttu-id="b6cb0-111">Aktivity a přenosy povolit uživateli probabilistically najít hlavní příčinu chyby.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-111">Activities and transfers permit the user to probabilistically locate the root cause of an error.</span></span> <span data-ttu-id="b6cb0-112">Například pokud jsme přenos vpřed a zpět mezi aktivitami M a N v uvedeném pořadí v součástech M a N a selhání se stane v pravé N po převodu zpět na M, jsme nakreslit do svého závěru, že je pravděpodobně v důsledku n. předání dat zpět do M.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-112">For example, if we transfer back and forth between activities M and N respectively in components M and N, and a crash happens in N right after the transfer back to M, we can draw the conclusion that it is likely due to N’s passing data back to M.</span></span>  
  
 <span data-ttu-id="b6cb0-113">Přenos trasování je vygenerován z aktivity M pro aktivitu N pokud tok řízení mezi M a N. Například N provede nějakou práci M kvůli volání metody přes hranice aktivit.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-113">A transfer trace is emitted from activity M to activity N when there is a flow of control between M and N. For example, N performs some work for M because of a method call crossing the activities’ boundaries.</span></span> <span data-ttu-id="b6cb0-114">Možná již existuje nebo byl vytvořen.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-114">N may already exist or has been created.</span></span> <span data-ttu-id="b6cb0-115">N je vytvořený službou M, když je N novou aktivitu prováděnou práci pro M.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-115">N is spawned by M when N is a new activity that performs some work for M.</span></span>  
  
 <span data-ttu-id="b6cb0-116">Přenos z M na N nemůže být následovaná převod zpět z N až M. Je to proto M můžete vytvořit podřízený práci ve N a do not track po N dokončení práce.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-116">A transfer from M to N may not be followed by a transfer back from N to M. This is because M can spawn some work in N and do not track when N completes that work.</span></span> <span data-ttu-id="b6cb0-117">Ve skutečnosti M může ukončit předtím, než N dokončení svých úkolů.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-117">In fact, M can terminate before N completes its task.</span></span> <span data-ttu-id="b6cb0-118">K tomu dojde za "Hostitel služby otevřít" aktivity (M), která vytvoří naslouchací proces aktivity (N) a poté ukončí.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-118">This happens in the "Open ServiceHost" activity (M) that spawns Listener activities (N) and then terminates.</span></span> <span data-ttu-id="b6cb0-119">Převod zpět z N až M znamená, že N Dokončená práce související se M.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-119">A transfer back from N to M means that N completed the work related to M.</span></span>  
  
 <span data-ttu-id="b6cb0-120">N můžete pokračovat v provádění jiné zpracování nesouvisí se M, například existující aktivitu authenticator (N), která udržuje přijímání žádostí o přihlášení (M) z jiné aktivity.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-120">N can continue performing other processing unrelated to M, for example, an existing authenticator activity (N) that keeps receiving login requests (M) from different login activities.</span></span>  
  
 <span data-ttu-id="b6cb0-121">Vztah vnoření neexistuje nutně mezi aktivitami M a N. Může to být způsobeno dva důvody.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-121">A nesting relationship does not necessarily exist between activities M and N. This can happen due to two reasons.</span></span> <span data-ttu-id="b6cb0-122">Nejprve, když aktivita M nesleduje vlastní zpracování provádět v N Přestože iniciované M N. Sekundy, když N již existuje.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-122">First, when activity M does not monitor the actual processing performed in N although M initiated N. Second, when N already exists.</span></span>  
  
## <a name="example-of-transfers"></a><span data-ttu-id="b6cb0-123">Příklad přenosů</span><span class="sxs-lookup"><span data-stu-id="b6cb0-123">Example of Transfers</span></span>  
 <span data-ttu-id="b6cb0-124">Následující seznamy dva přenos příklady.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-124">The following lists two transfer examples.</span></span>  
  
-   <span data-ttu-id="b6cb0-125">Při vytváření hostitele služby konstruktoru získá kontrolu dělat volající kód nebo volající kód převede do konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-125">When you create a service host, the constructor gains control from the calling code, or the calling code transfers to the constructor.</span></span> <span data-ttu-id="b6cb0-126">Po dokončení provádění konstruktoru vrátí řízení volajícímu kódu nebo konstruktor přenosech zpět do volající kód.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-126">When the constructor has finished executing, it returns control to the calling code, or the constructor transfers back to the calling code.</span></span> <span data-ttu-id="b6cb0-127">To platí vnořené relace.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-127">This is the case of a nested relationship.</span></span>  
  
-   <span data-ttu-id="b6cb0-128">Po spuštění zpracování přenosu dat naslouchací proces vytvoří nové vlákno a předá aktivitě přijímání bajtů vhodném kontextu pro zpracování a předání řízení a data.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-128">When a listener starts processing transport data, it creates a new thread and hands to the Receive Bytes activity the appropriate context for processing, passing control and data.</span></span> <span data-ttu-id="b6cb0-129">Po dokončení zpracování žádosti bylo vlákno aktivita přijímání bajtů nic předá zpět k naslouchacímu procesu.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-129">When that thread has finished processing the request, the Receive Bytes activity passes nothing back to the listener.</span></span> <span data-ttu-id="b6cb0-130">V tomto případě máme přenosu v ale nepřenášejí žádná aktivita nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-130">In this case, we have a transfer in but no transfer out of the new thread activity.</span></span> <span data-ttu-id="b6cb0-131">Dvě aktivity spolu souvisejí, ale ne vnořenou.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-131">The two activities are related but not nested.</span></span>  
  
## <a name="activity-transfer-sequence"></a><span data-ttu-id="b6cb0-132">Pořadí aktivit přenosu</span><span class="sxs-lookup"><span data-stu-id="b6cb0-132">Activity Transfer Sequence</span></span>  
 <span data-ttu-id="b6cb0-133">Pořadí přenosu ve správném formátu aktivit zahrnuje následující kroky.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-133">A well-formed activity transfer sequence includes the following steps.</span></span>  
  
1.  <span data-ttu-id="b6cb0-134">Začněte novou aktivitu, která se skládá z výběru nového gAId.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-134">Begin a new activity, which consists of selecting a new gAId.</span></span>  
  
2.  <span data-ttu-id="b6cb0-135">Generování trasování přenos do této nové gAId z aktuální ID aktivity</span><span class="sxs-lookup"><span data-stu-id="b6cb0-135">Emit a transfer trace to that new gAId from the current activity ID</span></span>  
  
3.  <span data-ttu-id="b6cb0-136">Nastavení nového ID v TLS</span><span class="sxs-lookup"><span data-stu-id="b6cb0-136">Set the new ID in TLS</span></span>  
  
4.  <span data-ttu-id="b6cb0-137">Generuje počáteční trasování označující začátek nové aktivity podle.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-137">Emit a start trace to indicate the beginning of the new activity by.</span></span>  
  
5.  <span data-ttu-id="b6cb0-138">Vrátit se k původní aktivity se skládá z následujících akcí:</span><span class="sxs-lookup"><span data-stu-id="b6cb0-138">Return to the original activity consists of the following:</span></span>  
  
6.  <span data-ttu-id="b6cb0-139">Generování trasování do třídy přenosu původní gAId</span><span class="sxs-lookup"><span data-stu-id="b6cb0-139">Emit a transfer trace to the original gAId</span></span>  
  
7.  <span data-ttu-id="b6cb0-140">Generování trasování Stop pro označení konce nová aktivita</span><span class="sxs-lookup"><span data-stu-id="b6cb0-140">Emit a Stop trace to indicate the end of the new activity</span></span>  
  
8.  <span data-ttu-id="b6cb0-141">Nastavte na staré gAId TLS.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-141">Set TLS to the old gAId.</span></span>  
  
 <span data-ttu-id="b6cb0-142">Následující příklad kódu ukazuje, jak to provést.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-142">The following code example demonstrates how to do this.</span></span> <span data-ttu-id="b6cb0-143">Tento příklad předpokládá blokovacího hovoru se provádí při přenosu do novou aktivitu a zahrnuje trasování operací pozastavit/pokračovat.</span><span class="sxs-lookup"><span data-stu-id="b6cb0-143">This sample assumes a blocking call is made when transferring to the new activity, and includes suspend/resume traces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b6cb0-144">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6cb0-144">See also</span></span>
- [<span data-ttu-id="b6cb0-145">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="b6cb0-145">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)
- [<span data-ttu-id="b6cb0-146">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="b6cb0-146">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="b6cb0-147">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="b6cb0-147">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="b6cb0-148">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="b6cb0-148">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
