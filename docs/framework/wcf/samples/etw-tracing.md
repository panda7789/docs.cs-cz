---
title: Trasování událostí pro Windows
ms.date: 03/30/2017
ms.assetid: ac99a063-e2d2-40cc-b659-d23c2f783f92
ms.openlocfilehash: a5c2f173978f514aa4627caa476a595d8d45d4f9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051920"
---
# <a name="etw-tracing"></a><span data-ttu-id="875c7-102">Trasování událostí pro Windows</span><span class="sxs-lookup"><span data-stu-id="875c7-102">ETW Tracing</span></span>
<span data-ttu-id="875c7-103">Tato ukázka předvádí, jak implementovat začátku do konce (E2E) trasování pomocí Event Tracing for Windows (ETW) a `ETWTraceListener` , který je součástí této ukázky.</span><span class="sxs-lookup"><span data-stu-id="875c7-103">This sample demonstrates how to implement End-to-End (E2E) tracing using Event Tracing for Windows (ETW) and the `ETWTraceListener` that is provided with this sample.</span></span> <span data-ttu-id="875c7-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a obsahuje trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="875c7-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes ETW tracing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="875c7-105">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="875c7-105">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="875c7-106">Tento příklad předpokládá, že máte zkušenosti s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="875c7-106">This sample assumes that you are familiar with [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="875c7-107">Každý zdroj trasování v <xref:System.Diagnostics> model trasování může mít několik naslouchacích procesů trasování, které určují, kde a jak se data trasovány.</span><span class="sxs-lookup"><span data-stu-id="875c7-107">Each trace source in the <xref:System.Diagnostics> tracing model can have multiple trace listeners that determine where and how the data is traced.</span></span> <span data-ttu-id="875c7-108">Typ naslouchacího procesu definuje formát, ve které se protokolují tato data trasování.</span><span class="sxs-lookup"><span data-stu-id="875c7-108">The type of listener defines the format in which trace data is logged.</span></span> <span data-ttu-id="875c7-109">Následující příklad kódu ukazuje, jak přidat naslouchací proces konfigurace.</span><span class="sxs-lookup"><span data-stu-id="875c7-109">The following code sample shows how to add the listener to configuration.</span></span>  
  
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
  
 <span data-ttu-id="875c7-110">Před použitím tohoto modulu pro naslouchání, musí se spustit relaci trasování ETW.</span><span class="sxs-lookup"><span data-stu-id="875c7-110">Before using this listener, an ETW Trace Session must be started.</span></span> <span data-ttu-id="875c7-111">Tato relace můžete spustit pomocí Logman.exe nebo Tracelog.exe.</span><span class="sxs-lookup"><span data-stu-id="875c7-111">This session can be started by using Logman.exe or Tracelog.exe.</span></span> <span data-ttu-id="875c7-112">SetupETW.bat souboru je zahrnuta v této ukázce tak, že můžete nastavit relaci sledování ETW spolu se souborem CleanupETW.bat pro zavření relace a dokončení souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="875c7-112">A SetupETW.bat file is included with this sample so that you can set up the ETW Trace Session along with a CleanupETW.bat file for closing the session and completing the log file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="875c7-113">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="875c7-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span> <span data-ttu-id="875c7-114">Další informace o těchto nástrojích najdete v tématu <https://go.microsoft.com/fwlink/?LinkId=56580></span><span class="sxs-lookup"><span data-stu-id="875c7-114">For more information about these tools, see <https://go.microsoft.com/fwlink/?LinkId=56580></span></span>  
  
 <span data-ttu-id="875c7-115">Při použití ETWTraceListener přihlášeni trasování .etl binární soubory.</span><span class="sxs-lookup"><span data-stu-id="875c7-115">When using the ETWTraceListener, traces are logged in binary .etl files.</span></span> <span data-ttu-id="875c7-116">S ServiceModel trasování zapnuté, všechna trasování vygenerovaný objeví ve stejném souboru.</span><span class="sxs-lookup"><span data-stu-id="875c7-116">With ServiceModel tracing turned on, all generated traces appear in the same file.</span></span> <span data-ttu-id="875c7-117">Použití [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) pro zobrazení ETL a .svclog souborů protokolů.</span><span class="sxs-lookup"><span data-stu-id="875c7-117">Use [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) for viewing .etl and .svclog log files.</span></span> <span data-ttu-id="875c7-118">V prohlížeči vytvoří pohledu začátku do konce systému, který umožňuje trasování zprávy z jeho zdroje do cíle a bod spotřeby.</span><span class="sxs-lookup"><span data-stu-id="875c7-118">The viewer creates an end-to-end view of the system that makes it possible to trace a message from its source to its destination and point of consumption.</span></span>  
  
 <span data-ttu-id="875c7-119">Naslouchací proces trasování ETW podporuje cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="875c7-119">The ETW Trace Listener supports circular logging.</span></span> <span data-ttu-id="875c7-120">Pokud chcete tuto funkci povolit, přejděte na **spustit**, **spustit** a typ `cmd` ke spuštění nástroje command console.</span><span class="sxs-lookup"><span data-stu-id="875c7-120">To enable this feature, go to **Start**, **Run** and type `cmd` to start a command console.</span></span> <span data-ttu-id="875c7-121">V následujícím příkazu nahraďte `<logfilename>` parametr s názvem souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="875c7-121">In the following command, replace the `<logfilename>` parameter with the name of your log file.</span></span>  
  
```  
logman create trace Wcf -o <logfilename> -p "{411a0819-c24b-428c-83e2-26b41091702e}" -f bincirc -max 1000  
```  
  
 <span data-ttu-id="875c7-122">`-f` a `-max` přepínače jsou volitelné.</span><span class="sxs-lookup"><span data-stu-id="875c7-122">The `-f` and `-max` switches are optional.</span></span> <span data-ttu-id="875c7-123">Určí cyklický binárních a maximální velikost protokolu 1000 MB v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="875c7-123">They specify the binary circular format and max log size of 1000MB respectively.</span></span> <span data-ttu-id="875c7-124">`-p` Přepínače se používá k určení zprostředkovatel trasování.</span><span class="sxs-lookup"><span data-stu-id="875c7-124">The `-p` switch is used to specify the trace provider.</span></span> <span data-ttu-id="875c7-125">V našem příkladu `"{411a0819-c24b-428c-83e2-26b41091702e}"` je identifikátor GUID pro "Zprostředkovateli ukázek trasování událostí pro Windows XML".</span><span class="sxs-lookup"><span data-stu-id="875c7-125">In our example, `"{411a0819-c24b-428c-83e2-26b41091702e}"` is the GUID for "XML ETW Sample Provider".</span></span>  
  
 <span data-ttu-id="875c7-126">Spustit relaci, zadejte následující příkaz.</span><span class="sxs-lookup"><span data-stu-id="875c7-126">To start the session, type in the following command.</span></span>  
  
```  
Logman start Wcf  
```  
  
 <span data-ttu-id="875c7-127">Po dokončení protokolování, můžete zastavit relaci pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="875c7-127">After you have finished logging, you can stop the session with the following command.</span></span>  
  
```  
Logman stop Wcf  
```  
  
 <span data-ttu-id="875c7-128">Tento proces vygeneruje binární cyklické protokoly, které můžete zpracovat nástroj podle vlastního výběru, včetně [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) nebo Tracerpt.</span><span class="sxs-lookup"><span data-stu-id="875c7-128">This process generates binary circular logs that you can process with your tool of choice, including [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) or Tracerpt.</span></span>  
  
 <span data-ttu-id="875c7-129">Můžete také zkontrolovat [cyklické trasování](../../../../docs/framework/wcf/samples/circular-tracing.md) ukázky pro další informace o alternativních naslouchací proces provádět cyklické protokolování.</span><span class="sxs-lookup"><span data-stu-id="875c7-129">You can also review the [Circular Tracing](../../../../docs/framework/wcf/samples/circular-tracing.md) sample for more information on an alternative listener to perform circular logging.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="875c7-130">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="875c7-130">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="875c7-131">Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="875c7-131">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="875c7-132">Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="875c7-132">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="875c7-133">Chcete-li použít příkazy RegisterProvider.bat, SetupETW.bat a CleanupETW.bat, musíte spustit pod účtem místního správce.</span><span class="sxs-lookup"><span data-stu-id="875c7-133">To use the RegisterProvider.bat, SetupETW.bat and CleanupETW.bat commands, you must run under a local administrator account.</span></span> <span data-ttu-id="875c7-134">Pokud používáte [!INCLUDE[wv](../../../../includes/wv-md.md)] nebo novější, musíte také spustit příkazový řádek se zvýšenými oprávněními.</span><span class="sxs-lookup"><span data-stu-id="875c7-134">If you are using [!INCLUDE[wv](../../../../includes/wv-md.md)] or later, you must also run the command prompt with elevated privileges.</span></span> <span data-ttu-id="875c7-135">Chcete-li tak učinit, klepněte pravým tlačítkem myši na ikonu příkazového řádku a potom klikněte na **spustit jako správce**.</span><span class="sxs-lookup"><span data-stu-id="875c7-135">To do so, right-click the command prompt icon, then click **Run as administrator**.</span></span>  
  
3. <span data-ttu-id="875c7-136">Před spuštěním ukázky, spusťte RegisterProvider.bat na klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="875c7-136">Before running the sample, run RegisterProvider.bat on the client and server.</span></span> <span data-ttu-id="875c7-137">Tím se nastaví výsledný soubor ETWTracingSampleLog.etl ke generování trasování, které lze číst pomocí prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="875c7-137">This sets up the resulting ETWTracingSampleLog.etl file to generate traces that can be read by the Service Trace Viewer.</span></span> <span data-ttu-id="875c7-138">Tento soubor najdete ve složce C:\logs.</span><span class="sxs-lookup"><span data-stu-id="875c7-138">This file can be found in the C:\logs folder.</span></span> <span data-ttu-id="875c7-139">Pokud tato složka neexistuje, je nutné vytvořit nebo jsou generovány žádné trasování.</span><span class="sxs-lookup"><span data-stu-id="875c7-139">If this folder does not exist, it must be created or no traces are generated.</span></span> <span data-ttu-id="875c7-140">Potom spusťte SetupETW.bat klientských a serverových počítačů zahájit relaci sledování ETW.</span><span class="sxs-lookup"><span data-stu-id="875c7-140">Then, run SetupETW.bat on the client and server computers to begin the ETW Trace Session.</span></span> <span data-ttu-id="875c7-141">SetupETW.bat soubor najdete ve složce CS\Client.</span><span class="sxs-lookup"><span data-stu-id="875c7-141">The SetupETW.bat file can be found under the CS\Client folder.</span></span>  
  
4. <span data-ttu-id="875c7-142">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="875c7-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
5. <span data-ttu-id="875c7-143">Po dokončení ukázku spusťte CleanupETW.bat k dokončení vytvoření ETWTracingSampleLog.etl souboru.</span><span class="sxs-lookup"><span data-stu-id="875c7-143">When the sample is completed, run CleanupETW.bat to complete the creation of the ETWTracingSampleLog.etl file.</span></span>  
  
6. <span data-ttu-id="875c7-144">Otevřete soubor ETWTracingSampleLog.etl z prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="875c7-144">Open the ETWTracingSampleLog.etl file from within the Service Trace Viewer.</span></span> <span data-ttu-id="875c7-145">Zobrazí se výzva k uložení binárního souboru formátovaný jako soubor .svclog.</span><span class="sxs-lookup"><span data-stu-id="875c7-145">You will be prompted to save the binary formatted file as a .svclog file.</span></span>  
  
7. <span data-ttu-id="875c7-146">Otevřete soubor nově vytvořený .svclog z prohlížeče trasování služeb k zobrazení trasování ETW a ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="875c7-146">Open the newly created .svclog file from within the Service Trace Viewer to view the ETW and ServiceModel traces.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="875c7-147">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="875c7-147">The samples may already be installed on your computer.</span></span> <span data-ttu-id="875c7-148">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="875c7-148">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="875c7-149">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="875c7-149">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="875c7-150">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="875c7-150">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\AnalyticTrace`  
  
## <a name="see-also"></a><span data-ttu-id="875c7-151">Viz také:</span><span class="sxs-lookup"><span data-stu-id="875c7-151">See also</span></span>

- [<span data-ttu-id="875c7-152">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="875c7-152">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
