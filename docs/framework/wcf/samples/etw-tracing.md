---
title: Trasování událostí pro Windows
description: Tato ukázka předvádí, jak implementovat E2E (end to-end) trasování pomocí trasování událostí pro Windows (ETW) a ETWTraceListener.
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 210186285ed749a5d1567becd6738939b0bd9d03
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244423"
---
# <a name="etw-tracing"></a><span data-ttu-id="50104-103">Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="50104-103">ETW Tracing</span></span>
<span data-ttu-id="50104-104">Tato ukázka předvádí, jak implementovat E2E (end to-end) trasování pomocí trasování událostí pro Windows (ETW) a `ETWTraceListener` který je součástí této ukázky.</span><span class="sxs-lookup"><span data-stu-id="50104-104">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="50104-105">Ukázka je založena na [Začínáme](getting-started-sample.md) a zahrnuje trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="50104-105">The sample is based on the [Getting Started](getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50104-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="50104-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="50104-107">Tato ukázka předpokládá, že máte zkušenosti s [trasováním a protokolováním zpráv](tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="50104-107">This sample assumes that you are familiar with [Tracing and Message Logging](tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="50104-108">Každý zdroj trasování v <xref:System.Diagnostics> modelu trasování může mít několik posluchačů trasování, které určují, kde a jak jsou data sledována.</span><span class="sxs-lookup"><span data-stu-id="50104-108">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="50104-109">Typ naslouchacího procesu definuje formát, ve kterém jsou data trasování protokolována.</span><span class="sxs-lookup"><span data-stu-id="50104-109">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="50104-110">Následující ukázka kódu ukazuje, jak přidat naslouchací proces do konfigurace.</span><span class="sxs-lookup"><span data-stu-id="50104-110">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="50104-111">Před použitím tohoto naslouchacího procesu musí být spuštěná relace trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="50104-111">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="50104-112">Tuto relaci lze spustit pomocí Logman.exe nebo Tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="50104-112">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="50104-113">V této ukázce je obsažen SetupETW.bat soubor, takže můžete nastavit relaci trasování ETW spolu se souborem CleanupETW.bat pro ukončení relace a dokončení souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="50104-113">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="50104-114">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="50104-114">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="50104-115">Další informace o těchto nástrojích najdete v tématu.<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="50104-115">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="50104-116">Při použití ETWTraceListener se trasování zaznamenávají do binárních souborů. ETL.</span><span class="sxs-lookup"><span data-stu-id="50104-116">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="50104-117">Když je zapnuté trasování ServiceModel, všechna vygenerovaná trasování se zobrazí ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="50104-117">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="50104-118">K zobrazení souborů protokolu. ETL a. svclog použijte [Nástroj Prohlížeč trasování služby (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="50104-118">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="50104-119">Prohlížeč vytvoří ucelený pohled na systém, který umožňuje trasovat zprávu z jejího zdroje do jejího cíle a bodu spotřeby.</span><span class="sxs-lookup"><span data-stu-id="50104-119">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="50104-120">Naslouchací proces trasování ETW podporuje cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="50104-120">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="50104-121">Tuto funkci povolíte tak, že přejdete na **Start**, **spustíte** a zadáte `cmd` příkaz a spustíte konzolu příkazů.</span><span class="sxs-lookup"><span data-stu-id="50104-121">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="50104-122">V následujícím příkazu nahraďte `<logfilename>` parametr názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="50104-122">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="50104-123">`-f`Přepínače a `-max` jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="50104-123">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="50104-124">Určují binární cyklický formát a maximální velikost protokolu až 000 MB v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="50104-124">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="50104-125">`-p`Přepínač slouží k určení poskytovatele trasování.</span><span class="sxs-lookup"><span data-stu-id="50104-125">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="50104-126">V našem příkladu `"{411a0819-c24b-428c-83e2-26b41091702e}"` je identifikátor GUID pro "Ukázkový poskytovatel XML ETW".</span><span class="sxs-lookup"><span data-stu-id="50104-126">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="50104-127">Chcete-li spustit relaci, zadejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="50104-127">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="50104-128">Po dokončení protokolování můžete zastavit relaci pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="50104-128">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="50104-129">Tento proces generuje binární cyklické protokoly, které můžete zpracovat s vámi zvoleným nástrojem, včetně [nástroje Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="50104-129">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="50104-130">Můžete si také projít ukázku [cyklického trasování](circular-tracing.md) , kde najdete další informace o alternativním naslouchacího procesu, který provede cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="50104-130">You can also review the [Circular Tracing](circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="50104-131">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="50104-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="50104-132">Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="50104-132">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="50104-133">Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="50104-133">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="50104-134">Chcete-li použít příkazy RegisterProvider.bat, SetupETW.bat a CleanupETW.bat, je nutné spustit pod účtem místního správce.</span><span class="sxs-lookup"><span data-stu-id="50104-134">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="50104-135">Pokud používáte systém Windows Vista nebo novější, musíte spustit také příkazový řádek se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="50104-135">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="50104-136">Provedete to tak, že kliknete pravým tlačítkem na ikonu příkazového řádku a potom kliknete na **Spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="50104-136">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="50104-137">Před spuštěním ukázky spusťte RegisterProvider.bat na klientovi a na serveru.</span><span class="sxs-lookup"><span data-stu-id="50104-137">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="50104-138">Tím se vytvoří výsledný soubor ETWTracingSampleLog. ETL, který vygeneruje trasování, které může číst prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="50104-138">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="50104-139">Tento soubor najdete ve složce C:\Logs..</span><span class="sxs-lookup"><span data-stu-id="50104-139">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="50104-140">Pokud tato složka neexistuje, je nutné ji vytvořit nebo nebudou vygenerována žádná trasování.</span><span class="sxs-lookup"><span data-stu-id="50104-140">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="50104-141">Pak na klientských a serverovém počítači spusťte SetupETW.bat a zahajte tak relaci trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="50104-141">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="50104-142">Soubor SetupETW.bat najdete ve složce CS\Client.</span><span class="sxs-lookup"><span data-stu-id="50104-142">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="50104-143">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="50104-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="50104-144">Po dokončení ukázky spusťte CleanupETW.bat, aby se dokončilo vytváření souboru ETWTracingSampleLog. ETL.</span><span class="sxs-lookup"><span data-stu-id="50104-144">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="50104-145">V prohlížeči trasování služby otevřete soubor ETWTracingSampleLog. ETL.</span><span class="sxs-lookup"><span data-stu-id="50104-145">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="50104-146">Zobrazí se výzva k uložení binárního naformátovaného souboru jako souboru. svclog.</span><span class="sxs-lookup"><span data-stu-id="50104-146">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="50104-147">Otevřete nově vytvořený soubor. svclog z prohlížeče trasování služby a zobrazte trasování ETW a ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="50104-147">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="50104-148">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="50104-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="50104-149">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="50104-149">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="50104-150">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="50104-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="50104-151">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="50104-151">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="50104-152">Viz také</span><span class="sxs-lookup"><span data-stu-id="50104-152">See also</span></span>

- <span data-ttu-id="50104-153">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="50104-153">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
