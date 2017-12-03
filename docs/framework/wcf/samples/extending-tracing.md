---
title: "Rozšíření trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09804e91b872e4daca929d9f9740d691d42b31c0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="extending-tracing"></a><span data-ttu-id="4741c-102">Rozšíření trasování</span><span class="sxs-lookup"><span data-stu-id="4741c-102">Extending Tracing</span></span>
<span data-ttu-id="4741c-103">Tento příklad ukazuje, jak rozšířit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] trasování funkce napsáním uživatelské aktivity trasování v kódu klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="4741c-103">This sample demonstrates how to extend the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] tracing feature by writing user-defined activity traces in client and service code.</span></span> <span data-ttu-id="4741c-104">To umožňuje uživateli vytvořit trasování aktivity a seskupovat trasování do logické jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="4741c-104">This allows the user to create trace activities and group traces into logical units of work.</span></span> <span data-ttu-id="4741c-105">Je také možné vazbu mezi aktivitami prostřednictvím přenosu (v rámci stejné koncového bodu) a šíření (v koncových bodů).</span><span class="sxs-lookup"><span data-stu-id="4741c-105">It is also possible to correlate activities through transfers (within the same endpoint) and propagation (across endpoints).</span></span> <span data-ttu-id="4741c-106">V této ukázce je povoleno trasování pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="4741c-106">In this sample, tracing is enabled for both the client and the service.</span></span> <span data-ttu-id="4741c-107">Další informace o tom, jak povolit trasování v konfiguračních souborech klienta a služby najdete v tématu [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span><span class="sxs-lookup"><span data-stu-id="4741c-107">For more information about how to enable tracing in client and service configuration files, see [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).</span></span>  
  
 <span data-ttu-id="4741c-108">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="4741c-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4741c-109">Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="4741c-109">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4741c-110">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="4741c-110">The samples may already be installed on your computer.</span></span> <span data-ttu-id="4741c-111">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="4741c-111">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4741c-112">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="4741c-112">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4741c-113">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="4741c-113">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a><span data-ttu-id="4741c-114">Trasování a rozšíření aktivity</span><span class="sxs-lookup"><span data-stu-id="4741c-114">Tracing and Activity Propagation</span></span>  
 <span data-ttu-id="4741c-115">Uživatelem definované aktivity trasování umožňuje uživateli vytvořit své vlastní aktivity trasování pro trasování skupiny do logické jednotky práce, correlate aktivit prostřednictvím přenosů a šíření a snížit náklady na výkon [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] trasování (například místo na disku souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="4741c-115">User-defined activity tracing allows the user to create their own trace activities to group traces into logical units of work, correlate activities through transfers and propagation, and lessen the performance cost of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tracing (for example, the disk space cost of a log file).</span></span>  
  
### <a name="adding-custom-sources"></a><span data-ttu-id="4741c-116">Přidání vlastních zdrojů</span><span class="sxs-lookup"><span data-stu-id="4741c-116">Adding Custom Sources</span></span>  
 <span data-ttu-id="4741c-117">Uživatelem definované trasování mohou být přidány do kódu klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="4741c-117">User-defined traces can be added to both client and service code.</span></span> <span data-ttu-id="4741c-118">Přidání zdroje trasování konfiguračních souborů klienta služby Windows nebo povolit pro toto vlastní trasování zaznamenat a zobrazí v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="4741c-118">Adding trace sources to the client or service configuration files allow for these custom traces to be recorded and displayed in the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="4741c-119">Následující kód ukazuje, jak přidat vlastní trasování zdroj s názvem `ServerCalculatorTraceSource` do konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="4741c-119">The following code shows how to add a user-defined trace source named `ServerCalculatorTraceSource` to the configuration file.</span></span>  
  
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
  
### <a name="correlating-activities"></a><span data-ttu-id="4741c-120">Korelace aktivity</span><span class="sxs-lookup"><span data-stu-id="4741c-120">Correlating Activities</span></span>  
 <span data-ttu-id="4741c-121">Pro vazbu mezi aktivitami přímo v koncových bodů, `propagateActivity` musí být nastaven `true` v `System.ServiceModel` zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="4741c-121">To correlate activities directly across endpoints, the `propagateActivity` attribute must be set to `true` in the `System.ServiceModel` trace source.</span></span> <span data-ttu-id="4741c-122">Navíc k šíření trasování bez průchodu přes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktivit, trasování ServiceModel aktivita musí být vypnutý.</span><span class="sxs-lookup"><span data-stu-id="4741c-122">Also, to propagate traces without going through [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activities, ServiceModel Activity Tracing must be turned off.</span></span> <span data-ttu-id="4741c-123">To můžete vidět v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="4741c-123">This can be seen in the following code example.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4741c-124">Vypnutí trasování aktivity ServiceModel není stejně, jako když úroveň trasování odlišené `switchValue` , nastavena na vypnuto.</span><span class="sxs-lookup"><span data-stu-id="4741c-124">Turning off ServiceModel Activity Tracing is not the same as having the trace level, denoted by the `switchValue` property, set to off.</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a><span data-ttu-id="4741c-125">Lessening snížený výkon</span><span class="sxs-lookup"><span data-stu-id="4741c-125">Lessening Performance Cost</span></span>  
 <span data-ttu-id="4741c-126">Nastavení `ActivityTracing` vypnuto v `System.ServiceModel` zdroj trasování, vygeneruje soubor trasování, který obsahuje pouze uživatelské aktivity trasování, bez trasování aktivity ServiceModel zahrnuty.</span><span class="sxs-lookup"><span data-stu-id="4741c-126">Setting `ActivityTracing` to off in the `System.ServiceModel` trace source generates a trace file that contains only user-defined activity traces, without any of the ServiceModel activity traces included.</span></span> <span data-ttu-id="4741c-127">Výsledkem je mnohem menší velikost souboru protokolu.</span><span class="sxs-lookup"><span data-stu-id="4741c-127">This results in a log file of much smaller size.</span></span> <span data-ttu-id="4741c-128">Však moci korelovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpracování trasování se ztratí.</span><span class="sxs-lookup"><span data-stu-id="4741c-128">However, the opportunity to correlate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] processing traces is lost.</span></span>  
  
##### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4741c-129">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="4741c-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4741c-130">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4741c-130">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4741c-131">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4741c-131">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4741c-132">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="4741c-132">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4741c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="4741c-133">See Also</span></span>  
 [<span data-ttu-id="4741c-134">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="4741c-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
