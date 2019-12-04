---
title: Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: c9f2b3019ee30ded59a7549a4d3be834c9ab9811
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716436"
---
# <a name="etw-tracing"></a><span data-ttu-id="c4c58-102">Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="c4c58-102">ETW Tracing</span></span>
<span data-ttu-id="c4c58-103">Tato ukázka předvádí, jak implementovat E2E (end to-end) trasování pomocí trasování událostí pro Windows (ETW) a `ETWTraceListener`, které jsou k dispozici v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="c4c58-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="c4c58-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a zahrnuje trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="c4c58-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4c58-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c4c58-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c4c58-106">Tato ukázka předpokládá, že máte zkušenosti s [trasováním a protokolováním zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="c4c58-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="c4c58-107">Každý zdroj trasování v modelu trasování <xref:System.Diagnostics> může mít několik posluchačů trasování, které určují, kde a jak se budou data trasovat.</span><span class="sxs-lookup"><span data-stu-id="c4c58-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="c4c58-108">Typ naslouchacího procesu definuje formát, ve kterém jsou data trasování protokolována.</span><span class="sxs-lookup"><span data-stu-id="c4c58-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="c4c58-109">Následující ukázka kódu ukazuje, jak přidat naslouchací proces do konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c4c58-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="c4c58-110">Před použitím tohoto naslouchacího procesu musí být spuštěná relace trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="c4c58-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="c4c58-111">Tuto relaci lze spustit pomocí programu Logman. exe nebo nástroji tracelog. exe.</span><span class="sxs-lookup"><span data-stu-id="c4c58-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="c4c58-112">Tato ukázka obsahuje soubor SetupETW. bat, takže můžete nastavit relaci trasování ETW spolu se souborem CleanupETW. bat pro ukončení relace a dokončení souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c4c58-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c4c58-113">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="c4c58-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="c4c58-114">Další informace o těchto nástrojích najdete v tématu <https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="c4c58-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="c4c58-115">Při použití ETWTraceListener se trasování zaznamenávají do binárních souborů. ETL.</span><span class="sxs-lookup"><span data-stu-id="c4c58-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="c4c58-116">Když je zapnuté trasování ServiceModel, všechna vygenerovaná trasování se zobrazí ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="c4c58-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="c4c58-117">Pro zobrazení souborů protokolu ETL a. svclog použijte [Nástroj Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="c4c58-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="c4c58-118">Prohlížeč vytvoří ucelený pohled na systém, který umožňuje trasovat zprávu z jejího zdroje do jejího cíle a bodu spotřeby.</span><span class="sxs-lookup"><span data-stu-id="c4c58-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="c4c58-119">Naslouchací proces trasování ETW podporuje cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="c4c58-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="c4c58-120">Tuto funkci povolíte tak, že přejdete na **Start**, **spustíte** a zadáte `cmd` a spustíte konzolu příkazů.</span><span class="sxs-lookup"><span data-stu-id="c4c58-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="c4c58-121">V následujícím příkazu nahraďte parametr `<logfilename>` názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="c4c58-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="c4c58-122">Přepínače `-f` a `-max` jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="c4c58-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="c4c58-123">Určují binární cyklický formát a maximální velikost protokolu až 000 MB v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="c4c58-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="c4c58-124">K určení poskytovatele trasování se používá `-p` přepínač.</span><span class="sxs-lookup"><span data-stu-id="c4c58-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="c4c58-125">V našem příkladu je `"{411a0819-c24b-428c-83e2-26b41091702e}"` identifikátor GUID pro "Ukázkový poskytovatel XML ETW".</span><span class="sxs-lookup"><span data-stu-id="c4c58-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="c4c58-126">Chcete-li spustit relaci, zadejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="c4c58-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="c4c58-127">Po dokončení protokolování můžete zastavit relaci pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="c4c58-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="c4c58-128">Tento proces generuje binární cyklické protokoly, které můžete zpracovat s vámi zvoleným nástrojem, včetně [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="c4c58-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="c4c58-129">Můžete si také projít ukázku [cyklického trasování](../../../../docs/framework/wcf/samples/circular-tracing.md) , kde najdete další informace o alternativním naslouchacího procesu, který provede cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="c4c58-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c4c58-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="c4c58-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="c4c58-131">Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4c58-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="c4c58-132">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4c58-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="c4c58-133">Chcete-li použít příkazy RegisterProvider. bat, SetupETW. bat a CleanupETW. bat, je nutné spustit pod účtem místního správce.</span><span class="sxs-lookup"><span data-stu-id="c4c58-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="c4c58-134">Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo novější, musíte také spustit příkazový řádek se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="c4c58-134">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)] or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="c4c58-135">Provedete to tak, že kliknete pravým tlačítkem na ikonu příkazového řádku a potom kliknete na **Spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="c4c58-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="c4c58-136">Před spuštěním ukázky spusťte na klientech a na serveru RegisterProvider. bat.</span><span class="sxs-lookup"><span data-stu-id="c4c58-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="c4c58-137">Tím se vytvoří výsledný soubor ETWTracingSampleLog. ETL, který vygeneruje trasování, které může číst prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="c4c58-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="c4c58-138">Tento soubor najdete ve složce C:\Logs.</span><span class="sxs-lookup"><span data-stu-id="c4c58-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="c4c58-139">Pokud tato složka neexistuje, je nutné ji vytvořit nebo nebudou vygenerována žádná trasování.</span><span class="sxs-lookup"><span data-stu-id="c4c58-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="c4c58-140">Pak na klientských a serverovém počítači spusťte SetupETW. bat a zahajte tak relaci trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="c4c58-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="c4c58-141">Soubor SetupETW. bat najdete ve složce CS\Client.</span><span class="sxs-lookup"><span data-stu-id="c4c58-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="c4c58-142">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="c4c58-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="c4c58-143">Po dokončení ukázky spusťte CleanupETW. bat, aby se dokončilo vytváření souboru ETWTracingSampleLog. ETL.</span><span class="sxs-lookup"><span data-stu-id="c4c58-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="c4c58-144">V prohlížeči trasování služby otevřete soubor ETWTracingSampleLog. ETL.</span><span class="sxs-lookup"><span data-stu-id="c4c58-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="c4c58-145">Zobrazí se výzva k uložení binárního naformátovaného souboru jako souboru. svclog.</span><span class="sxs-lookup"><span data-stu-id="c4c58-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="c4c58-146">Otevřete nově vytvořený soubor. svclog z prohlížeče trasování služby a zobrazte trasování ETW a ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="c4c58-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="c4c58-147">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="c4c58-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c4c58-148">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c4c58-148">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="c4c58-149">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="c4c58-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c4c58-150">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c4c58-150">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="c4c58-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4c58-151">See also</span></span>

- [<span data-ttu-id="c4c58-152">Ukázky monitorování technologie AppFabric</span><span class="sxs-lookup"><span data-stu-id="c4c58-152">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
