---
title: Rozšíření trasování
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: e61265210640d2b801ad55b9dc5a357cc4f161a7
ms.sourcegitcommit: 7370aa8203b6036cea1520021b5511d0fd994574
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/02/2020
ms.locfileid: "82728398"
---
# <a name="extend-tracing"></a><span data-ttu-id="b4647-102">Rozšiřování trasování</span><span class="sxs-lookup"><span data-stu-id="b4647-102">Extend tracing</span></span>

<span data-ttu-id="b4647-103">Tato ukázka demonstruje, jak lze rozšířenou funkci trasování Windows Communication Foundation (WCF) pomocí zápisu uživatelsky definovaných trasování aktivit v kódu klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b4647-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="b4647-104">Zápis uživatelsky definovaných trasování aktivit umožňuje uživateli vytvářet aktivity trasování a seskupovat trasování do logických jednotek práce.</span><span class="sxs-lookup"><span data-stu-id="b4647-104">Writing user-defined activity traces allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="b4647-105">Je také možné korelovat aktivity prostřednictvím přenosů (v rámci stejného koncového bodu) a šíření (mezi koncovými body).</span><span class="sxs-lookup"><span data-stu-id="b4647-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="b4647-106">V této ukázce je povoleno trasování pro klienta i službu.</span><span class="sxs-lookup"><span data-stu-id="b4647-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="b4647-107">Další informace o tom, jak povolit trasování v konfiguračních souborech klienta a služby, najdete v tématu [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="b4647-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="b4647-108">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b4647-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4647-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b4647-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b4647-110">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="b4647-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b4647-111">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b4647-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b4647-112">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="b4647-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4647-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b4647-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="b4647-114">Trasování a šíření aktivit</span><span class="sxs-lookup"><span data-stu-id="b4647-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="b4647-115">Uživatelsky definované trasování aktivit umožňuje uživateli vytvořit vlastní aktivity trasování pro seskupení trasování do logických pracovních jednotek, sladit aktivity prostřednictvím přenosů a šíření a snížit náklady na výkon trasování WCF (například náklady na místo na disku v souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="b4647-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="add-custom-sources"></a><span data-ttu-id="b4647-116">Přidat vlastní zdroje</span><span class="sxs-lookup"><span data-stu-id="b4647-116">Add custom sources</span></span>  
 <span data-ttu-id="b4647-117">Uživatelsky definované trasování lze přidat do kódu klienta i služby.</span><span class="sxs-lookup"><span data-stu-id="b4647-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="b4647-118">Přidání zdrojů trasování do konfiguračních souborů klienta nebo služby umožňuje zaznamenávat a zobrazovat tato vlastní trasování v [nástroji pro prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b4647-118">Adding trace sources to the client or service configuration files allows for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="b4647-119">Následující kód ukazuje, jak přidat zdroj trasování definovaný uživatelem s názvem `ServerCalculatorTraceSource` do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="b4647-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
</system.diagnostics>
....
```  
  
### <a name="correlate-activities"></a><span data-ttu-id="b4647-120">Korelace aktivit</span><span class="sxs-lookup"><span data-stu-id="b4647-120">Correlate activities</span></span>  
 <span data-ttu-id="b4647-121">Aby bylo možné korelovat aktivity přímo napříč koncovými `propagateActivity` body, musí být atribut `true` nastaven na `System.ServiceModel` hodnotu ve zdroji trasování.</span><span class="sxs-lookup"><span data-stu-id="b4647-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="b4647-122">Aby bylo možné rozšířit trasování bez průchodu aktivitami WCF, musí být trasování aktivity ServiceModel vypnuto.</span><span class="sxs-lookup"><span data-stu-id="b4647-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="b4647-123">To lze vidět v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="b4647-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b4647-124">Vypnutí trasování aktivity ServiceModel není stejné jako úroveň trasování, která je označena `switchValue` vlastností, nastavena na hodnotu OFF.</span><span class="sxs-lookup"><span data-stu-id="b4647-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessen-performance-cost"></a><span data-ttu-id="b4647-125">Snížit náklady na výkon</span><span class="sxs-lookup"><span data-stu-id="b4647-125">Lessen performance cost</span></span>  
 <span data-ttu-id="b4647-126">Nastavením `ActivityTracing` na hodnotu Vypnuto ve `System.ServiceModel` zdroji trasování dojde k vygenerování trasovacího souboru, který obsahuje pouze trasování aktivity definované uživatelem, aniž by bylo zahrnuto trasování aktivity ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="b4647-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="b4647-127">Vyloučení trasování aktivit ServiceModel má za následek mnohem menší soubor protokolu.</span><span class="sxs-lookup"><span data-stu-id="b4647-127">Excluding ServiceModel activity traces results in a much smaller log file.</span></span> <span data-ttu-id="b4647-128">Je však ztracena možnost korelace trasování zpracování WCF.</span><span class="sxs-lookup"><span data-stu-id="b4647-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
## <a name="set-up-build-and-run-the-sample"></a><span data-ttu-id="b4647-129">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b4647-129">Set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b4647-130">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4647-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b4647-131">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4647-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b4647-132">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b4647-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4647-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4647-133">See also</span></span>

- <span data-ttu-id="b4647-134">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="b4647-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
