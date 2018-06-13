---
title: Rozšíření trasování
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 59291b6a57ba602e5fea84dcd571a8d767b7cc04
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33806806"
---
# <a name="extending-tracing"></a><span data-ttu-id="435f3-102">Rozšíření trasování</span><span class="sxs-lookup"><span data-stu-id="435f3-102">Extending Tracing</span></span>
<span data-ttu-id="435f3-103">Tento příklad ukazuje, jak rozšířit funkci trasování Windows Communication Foundation (WCF) zápis trasování uživatelské aktivity v kódu klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="435f3-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="435f3-104">To umožňuje uživateli vytvořit trasování aktivity a seskupovat trasování do logické jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="435f3-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="435f3-105">Je také možné vazbu mezi aktivitami prostřednictvím přenosu (v rámci stejné koncového bodu) a šíření (v koncových bodů).</span><span class="sxs-lookup"><span data-stu-id="435f3-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="435f3-106">V této ukázce je povoleno trasování pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="435f3-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="435f3-107">Další informace o tom, jak povolit trasování v konfiguračních souborech klienta a služby najdete v tématu [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="435f3-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="435f3-108">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="435f3-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="435f3-109">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="435f3-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="435f3-110">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="435f3-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="435f3-111">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="435f3-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="435f3-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="435f3-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="435f3-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="435f3-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="435f3-114">Trasování a rozšíření aktivity</span><span class="sxs-lookup"><span data-stu-id="435f3-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="435f3-115">Uživatelem definované aktivity trasování umožňuje uživateli vytvořit své vlastní aktivity trasování pro trasování skupiny do logické jednotky práce, korelovat aktivity prostřednictvím přenosů a šíření a snížit náklady na výkon trasování WCF (například místo na disku náklady souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="435f3-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="435f3-116">Přidání vlastních zdrojů</span><span class="sxs-lookup"><span data-stu-id="435f3-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="435f3-117">Uživatelem definované trasování mohou být přidány do kódu klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="435f3-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="435f3-118">Přidání zdroje trasování konfiguračních souborů klienta služby Windows nebo povolit pro toto vlastní trasování zaznamenat a zobrazí v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="435f3-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="435f3-119">Následující kód ukazuje, jak přidat vlastní trasování zdroj s názvem `ServerCalculatorTraceSource` do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="435f3-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a><span data-ttu-id="435f3-120">Korelace aktivity</span><span class="sxs-lookup"><span data-stu-id="435f3-120">Correlating Activities</span></span>  
 <span data-ttu-id="435f3-121">Pro vazbu mezi aktivitami přímo v koncových bodů, `propagateActivity` musí být nastaven `true` v `System.ServiceModel` zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="435f3-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="435f3-122">Navíc k šíření trasování bez průchodu přes WCF aktivity, ServiceModel trasování aktivity musí být vypnutý.</span><span class="sxs-lookup"><span data-stu-id="435f3-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="435f3-123">To můžete vidět v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="435f3-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="435f3-124">Vypnutí trasování aktivity ServiceModel není stejně, jako když úroveň trasování odlišené `switchValue` , nastavena na vypnuto.</span><span class="sxs-lookup"><span data-stu-id="435f3-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="435f3-125">Lessening snížený výkon</span><span class="sxs-lookup"><span data-stu-id="435f3-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="435f3-126">Nastavení `ActivityTracing` vypnuto v `System.ServiceModel` zdroj trasování, vygeneruje soubor trasování, který obsahuje pouze uživatelské aktivity trasování, bez trasování aktivity ServiceModel zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="435f3-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="435f3-127">Výsledkem je mnohem menší velikost souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="435f3-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="435f3-128">Možnost ke korelaci WCF zpracování trasování je však ztraceny.</span><span class="sxs-lookup"><span data-stu-id="435f3-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="435f3-129">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="435f3-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="435f3-130">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="435f3-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="435f3-131">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="435f3-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="435f3-132">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="435f3-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="435f3-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="435f3-133">See Also</span></span>  
 [<span data-ttu-id="435f3-134">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="435f3-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
