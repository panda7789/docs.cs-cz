---
title: Cyklické sledování
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: 1f6c5287e6a53ed26ee5c9ed477e08dafc512e3f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406179"
---
# <a name="circular-tracing"></a><span data-ttu-id="dd3b8-102">Cyklické sledování</span><span class="sxs-lookup"><span data-stu-id="dd3b8-102">Circular Tracing</span></span>
<span data-ttu-id="dd3b8-103">Tento příklad ukazuje implementaci naslouchací proces trasování cyklické vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="dd3b8-104">Běžný scénář pro produkční služby je potřeba mít služby, které jsou k dispozici pro dlouhou dobu a povoleno na nízké úrovni protokolování trasování.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="dd3b8-105">Tyto služby využívat velké množství místa na disku.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="dd3b8-106">Při odstraňování služby, nejnovější data v protokolech trasování je relevantní pro řešení problémů.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="dd3b8-107">Tento příklad ukazuje implementaci pro posluchače trasování cyklické vyrovnávací paměti, ve kterém jsou pouze nejnovější trasování uchovávat na disku, až po konfigurovatelnou data.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="dd3b8-108">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a obsahuje naslouchací proces trasování vlastní.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dd3b8-109">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="dd3b8-110">Tento příklad předpokládá, že máte zkušenosti s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázky a přečetl(a) v dokumentaci k [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) vzorku.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="dd3b8-111">Naslouchací proces trasování cyklické vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="dd3b8-111">Circular Buffer Trace Listener</span></span>  
 <span data-ttu-id="dd3b8-112">Koncept za implementaci naslouchací služby stopy cyklické vyrovnávací paměti je, aby dva soubory, které může každý ukládat až polovinu data protokolu celkové požadované trasování.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="dd3b8-113">Naslouchací proces vytvoří jeden soubor a zapíše do tohoto souboru, dokud nebude dosaženo limitu polovina velikosti dat, v tomto okamžiku přepne do druhého souboru.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="dd3b8-114">Naslouchací proces dosáhne limitu pro druhý soubor - přepíše první soubor s nová trasování.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>  
  
 <span data-ttu-id="dd3b8-115">Je odvozena z tohoto modulu pro naslouchání `XmlWriteTraceListener` a umožňuje na protokoly, kde se dají zobrazit [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="dd3b8-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="dd3b8-116">Při pokusu o zobrazení protokolů, dva soubory protokolů můžete snadno rekombinované tak, že otevřete oba soubory protokolu ve stejnou dobu v nástroji prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="dd3b8-117">Nástroj prohlížeče trasování služeb automaticky postará o řazení trasování tak, aby byly zobrazeny ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="dd3b8-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="dd3b8-118">Configuration</span></span>  
 <span data-ttu-id="dd3b8-119">Službu lze nastavit používat naslouchací služby stopy cyklické vyrovnávací paměti tak, že přidáte následující kód pro naslouchací proces a zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="dd3b8-120">Maximální velikost souboru je určený nastavením `maxFileSizeKB` atribut v konfiguraci naslouchacího procesu cyklické trasování.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="dd3b8-121">To je ukázáno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-121">This is demonstrated in the following code.</span></span>  
  
```xml  
<system.diagnostics>  
  <sources>  
    <source name="System.ServiceModel" switchValue="Information,ActivityTracing" propagateActivity="true">  
      <listeners>  
        <add name="CircularTraceListener" />  
      </listeners>  
    </source>  
  </sources>  
  <sharedListeners>  
    <add name="CircularTraceListener" type="Microsoft. Samples.ServiceModel.CircularTraceListener,CircularTraceListener"   
         initializeData="c:\logs\CircularTracing-service.svclog" maxFileSizeKB="100" />  
  </sharedListeners>  
  <trace autoflush="true" />  
</system.diagnostics>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="dd3b8-122">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="dd3b8-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="dd3b8-123">Ujistěte se, jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dd3b8-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="dd3b8-124">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dd3b8-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="dd3b8-125">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="dd3b8-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dd3b8-126">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="dd3b8-127">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="dd3b8-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="dd3b8-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="dd3b8-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="dd3b8-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a><span data-ttu-id="dd3b8-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd3b8-130">See Also</span></span>  
 [<span data-ttu-id="dd3b8-131">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="dd3b8-131">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
