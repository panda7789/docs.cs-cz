---
title: Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: 07379a464e6635a3de10c08647dbc769a5885e4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183705"
---
# <a name="etw-tracing"></a><span data-ttu-id="64c3a-102">Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="64c3a-102">ETW Tracing</span></span>
<span data-ttu-id="64c3a-103">Tato ukázka ukazuje, jak implementovat trasování end-to-end (E2E) pomocí trasování `ETWTraceListener` událostí pro Windows (ETW) a který je k dispozici v této ukázce.</span><span class="sxs-lookup"><span data-stu-id="64c3a-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="64c3a-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a zahrnuje trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="64c3a-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64c3a-105">Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="64c3a-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="64c3a-106">Tato ukázka předpokládá, že jste obeznámeni s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="64c3a-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="64c3a-107">Každý zdroj trasování v modelu <xref:System.Diagnostics> trasování může mít více posluchačů trasování, které určují, kde a jak jsou data sledována.</span><span class="sxs-lookup"><span data-stu-id="64c3a-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="64c3a-108">Typ naslouchací proces definuje formát, ve kterém jsou protokolována data trasování.</span><span class="sxs-lookup"><span data-stu-id="64c3a-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="64c3a-109">Následující ukázka kódu ukazuje, jak přidat naslouchací proces do konfigurace.</span><span class="sxs-lookup"><span data-stu-id="64c3a-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="64c3a-110">Před použitím tohoto naslouchací proces eTW trace session musí být spuštěna.</span><span class="sxs-lookup"><span data-stu-id="64c3a-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="64c3a-111">Tuto relaci lze spustit pomocí logman.exe nebo Tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="64c3a-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="64c3a-112">Soubor SetupETW.bat je součástí této ukázky, takže můžete nastavit eTW trace session spolu se souborem CleanupETW.bat pro zavření relace a dokončení souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="64c3a-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="64c3a-113">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="64c3a-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="64c3a-114">Další informace o těchto nástrojích naleznete v tématu<https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="64c3a-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="64c3a-115">Při použití ETWTraceListener, trasování jsou protokolovány v binárních .etl soubory.</span><span class="sxs-lookup"><span data-stu-id="64c3a-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="64c3a-116">Se zapnutou trasování ServiceModel se zobrazí všechna vygenerovaná trasování ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="64c3a-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="64c3a-117">Nástroj [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) slouží k prohlížení souborů protokolu .etl a .svclog.</span><span class="sxs-lookup"><span data-stu-id="64c3a-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="64c3a-118">Prohlížeč vytvoří komplexní zobrazení systému, které umožňuje sledovat zprávu ze zdroje do cílového místa a místa spotřeby.</span><span class="sxs-lookup"><span data-stu-id="64c3a-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="64c3a-119">ETW naslouchací proces trasování podporuje cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="64c3a-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="64c3a-120">Chcete-li tuto funkci povolit, `cmd` přejděte na **úvodní**obrazovku , **Spustit** a zadejte spusťte příkazovou konzolu.</span><span class="sxs-lookup"><span data-stu-id="64c3a-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="64c3a-121">V následujícím příkazu `<logfilename>` nahraďte parametr názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="64c3a-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```console  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="64c3a-122">`-f` Přepínače `-max` a jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="64c3a-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="64c3a-123">Určují binární kruhový formát a maximální velikost protokolu 1000 MB.</span><span class="sxs-lookup"><span data-stu-id="64c3a-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="64c3a-124">Přepínač `-p` se používá k určení zprostředkovatele trasování.</span><span class="sxs-lookup"><span data-stu-id="64c3a-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="64c3a-125">V našem `"{411a0819-c24b-428c-83e2-26b41091702e}"` příkladu je identifikátor GUID pro "XML ETW ukázkový zprostředkovatel".</span><span class="sxs-lookup"><span data-stu-id="64c3a-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="64c3a-126">Chcete-li relaci spustit, zadejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="64c3a-126">To start the session, type in the following command.</span></span>  
  
```console  
logman start Wcf  
```  
  
 <span data-ttu-id="64c3a-127">Po dokončení protokolování můžete relaci zastavit pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="64c3a-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```console  
logman stop Wcf  
```  
  
 <span data-ttu-id="64c3a-128">Tento proces generuje binární cyklické protokoly, které můžete zpracovat pomocí zvoleného nástroje, včetně [nástroje Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="64c3a-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="64c3a-129">Můžete také zkontrolovat [cyklické trasování](../../../../docs/framework/wcf/samples/circular-tracing.md) ukázku pro více informací o alternativní naslouchací proces provádět cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="64c3a-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="64c3a-130">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="64c3a-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="64c3a-131">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="64c3a-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="64c3a-132">Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="64c3a-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="64c3a-133">Chcete-li použít příkazy RegisterProvider.bat, SetupETW.bat a CleanupETW.bat, musíte spustit pod účtem místního správce.</span><span class="sxs-lookup"><span data-stu-id="64c3a-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="64c3a-134">Pokud používáte systém Windows Vista nebo novější, je nutné spustit také příkazový řádek se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="64c3a-134">If you are using Windows Vista or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="64c3a-135">Chcete-li tak učinit, klepněte pravým tlačítkem myši na ikonu příkazového řádku a potom klepněte na příkaz **Spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="64c3a-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="64c3a-136">Před spuštěním ukázky spusťte RegisterProvider.bat na straně klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="64c3a-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="64c3a-137">Tím nastavíte výsledný soubor ETWTracingSampleLog.etl pro generování trasování, které lze číst prohlížečem trasování služby.</span><span class="sxs-lookup"><span data-stu-id="64c3a-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="64c3a-138">Tento soubor lze nalézt ve složce C:\logs.</span><span class="sxs-lookup"><span data-stu-id="64c3a-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="64c3a-139">Pokud tato složka neexistuje, musí být vytvořena nebo jsou generovány žádné stopy.</span><span class="sxs-lookup"><span data-stu-id="64c3a-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="64c3a-140">Potom spusťte SetupETW.bat na počítačích klienta a serveru zahájit relaci trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="64c3a-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="64c3a-141">Soubor SetupETW.bat naleznete ve složce CS\Client.</span><span class="sxs-lookup"><span data-stu-id="64c3a-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="64c3a-142">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="64c3a-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="64c3a-143">Po dokončení vzorku spusťte CleanupETW.bat k dokončení vytvoření souboru ETWTracingSampleLog.etl.</span><span class="sxs-lookup"><span data-stu-id="64c3a-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="64c3a-144">Otevřete soubor ETWTracingSampleLog.etl z prohlížeče trasování služby.</span><span class="sxs-lookup"><span data-stu-id="64c3a-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="64c3a-145">Budete vyzváni k uložení binárního formátovaného souboru jako souboru .svclog.</span><span class="sxs-lookup"><span data-stu-id="64c3a-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="64c3a-146">Otevřete nově vytvořený soubor .svclog z prohlížeče trasování služby a zobrazte trasování ETW a ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="64c3a-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="64c3a-147">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="64c3a-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="64c3a-148">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="64c3a-148">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="64c3a-149">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="64c3a-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="64c3a-150">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="64c3a-150">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="64c3a-151">Viz také</span><span class="sxs-lookup"><span data-stu-id="64c3a-151">See also</span></span>

- <span data-ttu-id="64c3a-152">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="64c3a-152">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
