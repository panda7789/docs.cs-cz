---
title: "Trasování událostí pro Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
caps.latest.revision: "42"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5ebffd082f5d1b07ab016c0e5e72d6ad23542147
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="etw-tracing"></a><span data-ttu-id="24df5-102">Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="24df5-102">ETW Tracing</span></span>
<span data-ttu-id="24df5-103">Tento příklad ukazuje, jak implementovat trasování začátku do konce (E2E) pomocí události trasování událostí pro Windows (ETW) a `ETWTraceListener` je součástí této ukázky.</span><span class="sxs-lookup"><span data-stu-id="24df5-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="24df5-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a zahrnuje trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="24df5-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24df5-105">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="24df5-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="24df5-106">Tato ukázka se předpokládá, že jste obeznámeni s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="24df5-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="24df5-107">Každý zdroj trasování v <xref:System.Diagnostics> trasování model může mít více modulů naslouchání trasování, které určují, kdy a jak je sledovat data.</span><span class="sxs-lookup"><span data-stu-id="24df5-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="24df5-108">Typ naslouchací proces definuje formát, ve kterém se protokolují data trasování.</span><span class="sxs-lookup"><span data-stu-id="24df5-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="24df5-109">Následující příklad kódu ukazuje, jak přidat naslouchací proces do konfigurace.</span><span class="sxs-lookup"><span data-stu-id="24df5-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel"   
             switchValue="Verbose,ActivityTracing"  
             propagateActivity="true">  
            <listeners>  
                <add type=  
                   "System.Diagnostics.DefaultTraceListener"  
                   name="Default">  
                   <filter type="" />  
                </add>  
                <add name="ETW">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
        <add type=  
            "Microsoft.ServiceModel.Samples.EtwTraceListener, ETWTraceListener"  
            name="ETW" traceOutputOptions="Timestamp">  
            <filter type="" />  
       </add>  
    </sharedListeners>  
</system.diagnostics>  
```  
  
 <span data-ttu-id="24df5-110">Před použitím této naslouchací proces, je nutné spustit relaci trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="24df5-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="24df5-111">Pomocí Logman.exe nebo Tracelog.exe lze spustit tuto relaci.</span><span class="sxs-lookup"><span data-stu-id="24df5-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="24df5-112">Soubor SetupETW.bat je součástí této ukázky, takže můžete nastavit relaci trasování ETW souborem CleanupETW.bat pro zavření relace a dokončení souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="24df5-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="24df5-113">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="24df5-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="24df5-114">Další informace o těchto nástrojích najdete v tématu [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)</span><span class="sxs-lookup"><span data-stu-id="24df5-114">For more information about these tools, see [http://go.microsoft.com/fwlink/?LinkId=56580](http://go.microsoft.com/fwlink/?LinkId=56580)</span></span>  
  
 <span data-ttu-id="24df5-115">Při použití ETWTraceListener, trasování jsou protokolovány v souborech binární ETL.</span><span class="sxs-lookup"><span data-stu-id="24df5-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="24df5-116">Pomocí trasování ServiceModel zapnuta, zobrazí všechny vygenerované trasování ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="24df5-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="24df5-117">Použití [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pro zobrazení ETL a .svclog souborů protokolu.</span><span class="sxs-lookup"><span data-stu-id="24df5-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="24df5-118">Prohlížeč vytvoří zobrazení o začátku do konce systému, který umožňuje trasování zprávy z zdroje do cíle a bod spotřeby.</span><span class="sxs-lookup"><span data-stu-id="24df5-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="24df5-119">Naslouchací proces trasování ETW podporuje cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="24df5-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="24df5-120">Chcete-li povolit tuto funkci, přejděte na **spustit**, **spustit** a typ `cmd` a spusťte příkaz konzolu.</span><span class="sxs-lookup"><span data-stu-id="24df5-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="24df5-121">V následujícím příkazu nahraďte `<logfilename>` parametr s názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="24df5-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="24df5-122">`-f` a `-max` přepínače jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="24df5-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="24df5-123">Určí binární formát cyklické a protokolu maximální velikost 1000MB v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="24df5-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="24df5-124">`-p` Přepínač slouží k určení zprostředkovatel trasování.</span><span class="sxs-lookup"><span data-stu-id="24df5-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="24df5-125">V našem příkladu `"{411a0819-c24b-428c-83e2-26b41091702e}"` je identifikátor GUID pro "XML ETW ukázka zprostředkovatele".</span><span class="sxs-lookup"><span data-stu-id="24df5-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="24df5-126">Chcete-li spustit relaci, zadejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="24df5-126">To start the session, type in the following command.</span></span>  
  
```  
Logman start Wcf  
```  
  
 <span data-ttu-id="24df5-127">Po dokončení protokolování, můžete zastavit relace pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="24df5-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```  
Logman stop Wcf  
```  
  
 <span data-ttu-id="24df5-128">Tento proces vytvoří binární cyklické protokoly, které můžete zpracovat vaše nástroje, včetně [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="24df5-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="24df5-129">Můžete také zkontrolovat [cyklické trasování](../../../../docs/framework/wcf/samples/circular-tracing.md) ukázku Další informace o naslouchací proces alternativní postup cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="24df5-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="24df5-130">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="24df5-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="24df5-131">Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="24df5-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="24df5-132">Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="24df5-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="24df5-133">Pokud chcete používat příkazy RegisterProvider.bat, SetupETW.bat a CleanupETW.bat, musíte spustit pod účtem místního správce.</span><span class="sxs-lookup"><span data-stu-id="24df5-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="24df5-134">Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo novější, je nutné spustit také příkazovém řádku se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="24df5-134">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)] or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="24df5-135">Chcete-li to provést, klikněte pravým tlačítkem na ikonu příkazového řádku a potom klikněte na **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="24df5-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3.  <span data-ttu-id="24df5-136">Před spuštěním ukázky, spusťte RegisterProvider.bat na klientovi a serveru.</span><span class="sxs-lookup"><span data-stu-id="24df5-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="24df5-137">Výsledný soubor ETWTracingSampleLog.etl nastavíte ke generování trasování, které mohou být přečteny prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="24df5-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="24df5-138">Tento soubor naleznete ve složce C:\logs.</span><span class="sxs-lookup"><span data-stu-id="24df5-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="24df5-139">Pokud tato složka neexistuje, musí být vytvořen nebo jsou generovány žádné trasování.</span><span class="sxs-lookup"><span data-stu-id="24df5-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="24df5-140">Potom spusťte SetupETW.bat na počítače klienta a serveru, které chcete zahájit relaci trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="24df5-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="24df5-141">SetupETW.bat soubor naleznete ve složce CS\Client.</span><span class="sxs-lookup"><span data-stu-id="24df5-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4.  <span data-ttu-id="24df5-142">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="24df5-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="24df5-143">Po dokončení ukázku spusťte CleanupETW.bat vytvoření souboru ETWTracingSampleLog.etl.</span><span class="sxs-lookup"><span data-stu-id="24df5-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6.  <span data-ttu-id="24df5-144">Otevřete soubor ETWTracingSampleLog.etl z v rámci prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="24df5-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="24df5-145">Zobrazí se výzva k uložení binárního souboru formátovaný jako soubor .svclog.</span><span class="sxs-lookup"><span data-stu-id="24df5-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7.  <span data-ttu-id="24df5-146">Otevřete nově vytvořený .svclog souboru v rámci prohlížeče trasování služeb k zobrazení trasování událostí pro Windows a ServiceModel trasování.</span><span class="sxs-lookup"><span data-stu-id="24df5-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="24df5-147">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="24df5-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="24df5-148">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="24df5-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="24df5-149">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="24df5-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="24df5-150">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="24df5-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="24df5-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="24df5-151">See Also</span></span>  
 [<span data-ttu-id="24df5-152">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="24df5-152">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
