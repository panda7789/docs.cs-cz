---
title: Rozšíření trasování
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: a7231d340d2528a42c8cbb5294d812d52db92d54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183693"
---
# <a name="extending-tracing"></a><span data-ttu-id="17ee5-102">Rozšíření trasování</span><span class="sxs-lookup"><span data-stu-id="17ee5-102">Extending Tracing</span></span>
<span data-ttu-id="17ee5-103">Tato ukázka ukazuje, jak rozšířit windows komunikace Foundation (WCF) trasování funkce zápisem uživatelem definované trasování aktivit v kódu klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="17ee5-103">This sample demonstrates how to extend the Windows Communication Foundation (WCF) tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="17ee5-104">To umožňuje uživateli vytvářet aktivity trasování a skupiny trasování do logické jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="17ee5-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="17ee5-105">Je také možné korelovat aktivity prostřednictvím přenosů (v rámci stejného koncového bodu) a šíření (napříč koncovými body).</span><span class="sxs-lookup"><span data-stu-id="17ee5-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="17ee5-106">V této ukázce je povoleno trasování pro klienta i službu.</span><span class="sxs-lookup"><span data-stu-id="17ee5-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="17ee5-107">Další informace o povolení trasování v konfiguračních souborech klientů a služeb naleznete v [tématu Trasování a Protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="17ee5-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="17ee5-108">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="17ee5-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17ee5-109">Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="17ee5-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="17ee5-110">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="17ee5-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="17ee5-111">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="17ee5-111">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="17ee5-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="17ee5-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="17ee5-113">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="17ee5-113">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="17ee5-114">Trasování a šíření aktivit</span><span class="sxs-lookup"><span data-stu-id="17ee5-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="17ee5-115">Uživatelem definované trasování aktivit umožňuje uživateli vytvářet vlastní aktivity trasování k seskupení trasování do logických jednotek práce, korelovat aktivity prostřednictvím přenosů a šíření a shrábnout náklady na výkon trasování WCF (například náklady na místo na disku souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="17ee5-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="17ee5-116">Přidání vlastních zdrojů</span><span class="sxs-lookup"><span data-stu-id="17ee5-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="17ee5-117">Uživatelem definované trasování lze přidat do kódu klienta i služby.</span><span class="sxs-lookup"><span data-stu-id="17ee5-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="17ee5-118">Přidání zdrojů trasování do konfiguračních souborů klienta nebo služby umožňuje zaznamenat a zobrazit tyto vlastní trasování v [nástroji Service Trace Viewer (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)</span><span class="sxs-lookup"><span data-stu-id="17ee5-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="17ee5-119">Následující kód ukazuje, jak přidat uživatelem `ServerCalculatorTraceSource` definovaný zdroj trasování pojmenovaný do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="17ee5-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
  
### <a name="correlating-activities"></a><span data-ttu-id="17ee5-120">Korelační činnosti</span><span class="sxs-lookup"><span data-stu-id="17ee5-120">Correlating Activities</span></span>  
 <span data-ttu-id="17ee5-121">Chcete-li korelovat aktivity `propagateActivity` přímo mezi `true` koncovými `System.ServiceModel` body, musí být atribut nastaven na ve zdroji trasování.</span><span class="sxs-lookup"><span data-stu-id="17ee5-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="17ee5-122">Také chcete-li šířit trasování bez procházení wcf aktivity, sledování aktivity ServiceModel musí být vypnuto.</span><span class="sxs-lookup"><span data-stu-id="17ee5-122">Also, to propagate traces without going through WCF activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="17ee5-123">To lze vidět v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="17ee5-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17ee5-124">Vypnutí trasování aktivity ServiceModel není totéž jako s úroveň `switchValue` trasování, označené vlastností, vypnuto.</span><span class="sxs-lookup"><span data-stu-id="17ee5-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="17ee5-125">Snížení nákladů na výkon</span><span class="sxs-lookup"><span data-stu-id="17ee5-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="17ee5-126">Nastavení `ActivityTracing` vypnout `System.ServiceModel` ve zdroji trasování generuje trasovací soubor, který obsahuje pouze uživatelem definované trasování aktivity, bez jakékoli trasování aktivity ServiceModel zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="17ee5-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="17ee5-127">Výsledkem je soubor protokolu mnohem menší velikosti.</span><span class="sxs-lookup"><span data-stu-id="17ee5-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="17ee5-128">Však je ztracena možnost korelovat trasování zpracování WCF.</span><span class="sxs-lookup"><span data-stu-id="17ee5-128">However, the opportunity to correlate WCF processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="17ee5-129">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="17ee5-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="17ee5-130">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="17ee5-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="17ee5-131">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="17ee5-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="17ee5-132">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="17ee5-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17ee5-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="17ee5-133">See also</span></span>

- <span data-ttu-id="17ee5-134">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="17ee5-134">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
