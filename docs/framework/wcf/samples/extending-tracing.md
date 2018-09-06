---
title: Rozšíření trasování
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 02dfcc099883ed1d5e97b4f7b1a1f76d49b27a20
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740690"
---
# <a name="extending-tracing"></a><span data-ttu-id="9c15b-102">Rozšíření trasování</span><span class="sxs-lookup"><span data-stu-id="9c15b-102">Extending Tracing</span></span>
<span data-ttu-id="9c15b-103">Tato ukázka předvádí, jak rozšířit funkci trasování Windows Communication Foundation (WCF) zápisem aktivit uživatelem definované trasy v kódu klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="9c15b-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="9c15b-104">To umožňuje uživateli vytvořit trasování aktivity a seskupit trasování do logických jednotek práce.</span><span class="sxs-lookup"><span data-stu-id="9c15b-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="9c15b-105">Také je možné korelovat aktivity prostřednictvím převody (v rámci stejný koncový bod) a šíření (napříč koncovými body).</span><span class="sxs-lookup"><span data-stu-id="9c15b-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="9c15b-106">V této ukázce je povoleno trasování klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="9c15b-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="9c15b-107">Další informace o tom, jak povolit trasování v konfiguračních souborů klienta a služby, najdete v části [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="9c15b-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="9c15b-108">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9c15b-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c15b-109">Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9c15b-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c15b-110">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9c15b-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9c15b-111">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9c15b-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c15b-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9c15b-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c15b-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9c15b-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="9c15b-114">Trasování a šíření aktivity</span><span class="sxs-lookup"><span data-stu-id="9c15b-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="9c15b-115">Uživatelem definované aktivity trasování umožňuje uživateli vytvořit své vlastní aktivity trasování pro trasování skupiny do logických jednotek práce, korelovat aktivity prostřednictvím přenosů a šíření hodnoty a snížit náklady na trasování WCF (například místo na disku nákladů souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="9c15b-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="9c15b-116">Přidání vlastních zdrojů</span><span class="sxs-lookup"><span data-stu-id="9c15b-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="9c15b-117">Uživatelem definované trasy je přidat do kódu klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="9c15b-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="9c15b-118">Přidání zdroje trasování konfiguračních souborů klienta nebo služby umožňují vlastní trasování mají být zaznamenány a zobrazí v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9c15b-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="9c15b-119">Následující kód ukazuje, jak přidat zdroj uživatelem definované trasování s názvem `ServerCalculatorTraceSource` do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="9c15b-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
  
### <a name="correlating-activities"></a><span data-ttu-id="9c15b-120">Korelace aktivity</span><span class="sxs-lookup"><span data-stu-id="9c15b-120">Correlating Activities</span></span>  
 <span data-ttu-id="9c15b-121">Ke korelaci aktivit přímo napříč koncovými body, `propagateActivity` atribut musí být nastaven na `true` v `System.ServiceModel` zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="9c15b-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="9c15b-122">Navíc bez nutnosti kontaktovat WCF aktivity rozšíření trasování, ServiceModel trasování aktivity musí být vypnutý.</span><span class="sxs-lookup"><span data-stu-id="9c15b-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="9c15b-123">To můžete vidět v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="9c15b-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c15b-124">Vypnutí trasování aktivity ServiceModel není stejná jako úroveň trasování, udávají `switchValue` vlastnost, nastavena na hodnotu off.</span><span class="sxs-lookup"><span data-stu-id="9c15b-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="9c15b-125">Lessening snížení výkonu</span><span class="sxs-lookup"><span data-stu-id="9c15b-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="9c15b-126">Nastavení `ActivityTracing` vypnuté v `System.ServiceModel` zdroj trasování vygeneruje trasovací soubor, který obsahuje pouze uživatelské aktivity trasování, bez jakékoli ServiceModel trasování aktivity zahrnuta.</span><span class="sxs-lookup"><span data-stu-id="9c15b-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="9c15b-127">Výsledkem je mnohem menší velikosti souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="9c15b-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="9c15b-128">Však dojde ke ztrátě příležitosti ke korelaci zpracování trasování WCF.</span><span class="sxs-lookup"><span data-stu-id="9c15b-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9c15b-129">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="9c15b-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9c15b-130">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c15b-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9c15b-131">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c15b-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9c15b-132">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9c15b-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c15b-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c15b-133">See Also</span></span>  
 [<span data-ttu-id="9c15b-134">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="9c15b-134">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
