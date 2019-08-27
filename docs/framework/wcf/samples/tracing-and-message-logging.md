---
title: Trasování a protokolování zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: a58541b7d50d83d1e39d7c9dd9c58be4111ec494
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70038738"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="970b6-102">Trasování a protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="970b6-102">Tracing and Message Logging</span></span>
<span data-ttu-id="970b6-103">Tato ukázka demonstruje, jak povolit trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="970b6-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="970b6-104">Výsledné trasování a protokoly zpráv se zobrazují pomocí [nástroje Service Trace Viewer (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="970b6-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="970b6-105">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="970b6-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="970b6-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="970b6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="970b6-107">Trasování</span><span class="sxs-lookup"><span data-stu-id="970b6-107">Tracing</span></span>  
 <span data-ttu-id="970b6-108">Windows Communication Foundation (WCF) používá mechanismus trasování definovaný v <xref:System.Diagnostics> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="970b6-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="970b6-109">V tomto trasovacím modelu jsou data trasování vytvořena pomocí zdrojů trasování, které aplikace implementuje.</span><span class="sxs-lookup"><span data-stu-id="970b6-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="970b6-110">Jednotlivé zdroje jsou označeny názvem.</span><span class="sxs-lookup"><span data-stu-id="970b6-110">Each source is identified by a name.</span></span> <span data-ttu-id="970b6-111">Trasovat příjemce: Vytvoření posluchačů trasování pro zdroje trasování, pro které chtějí získat informace.</span><span class="sxs-lookup"><span data-stu-id="970b6-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="970b6-112">Chcete-li přijímat data trasování, je nutné vytvořit naslouchací proces pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="970b6-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="970b6-113">V rámci služby WCF to můžete udělat přidáním následujícího kódu do konfiguračního souboru služby nebo klienta nastavením zdroje `switchValue`trasování modelu služby:</span><span class="sxs-lookup"><span data-stu-id="970b6-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 <span data-ttu-id="970b6-114">Další informace o zdrojích trasování naleznete v části zdroj trasování v tématu [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="970b6-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="970b6-115">Trasování aktivit a šíření</span><span class="sxs-lookup"><span data-stu-id="970b6-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="970b6-116">Povolení a `propagateActivity` nastavení`true` ve`system.ServiceModel` zdrojích trasování pro klienta i službu poskytují korelaci trasování v rámci logických jednotek zpracování (aktivity) napříč aktivitami v rámci koncových bodů ( `ActivityTracing` prostřednictvím přenosů aktivit) a napříč aktivitami zahrnujícími více koncových bodů (prostřednictvím šíření ID aktivity).</span><span class="sxs-lookup"><span data-stu-id="970b6-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="970b6-117">Tyto tři mechanismy (aktivity, přenosy a šíření) vám mohou pomoci najít hlavní příčinu chyby rychleji pomocí nástroje Prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="970b6-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="970b6-118">Další informace najdete v tématu [použití prohlížeče trasování služby pro zobrazení korelačních trasování a odstraňování potíží](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="970b6-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="970b6-119">Je možné roztáhnout trasování, které poskytuje ServiceModel, vytvořením trasování aktivity definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="970b6-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="970b6-120">Trasování uživatelsky definované aktivity umožňuje uživateli vytvářet aktivity trasování pro:</span><span class="sxs-lookup"><span data-stu-id="970b6-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="970b6-121">Seskupí trasování do logických pracovních jednotek.</span><span class="sxs-lookup"><span data-stu-id="970b6-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="970b6-122">Korelujte aktivity prostřednictvím přenosů a šíření.</span><span class="sxs-lookup"><span data-stu-id="970b6-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="970b6-123">Snížit náklady na výkon trasování WCF (například náklady na místo na disku souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="970b6-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="970b6-124">Další informace o uživatelsky definovaném trasování aktivit najdete v ukázce [rozšíření trasování](../../../../docs/framework/wcf/samples/extending-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="970b6-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="970b6-125">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="970b6-125">Message Logging</span></span>  
 <span data-ttu-id="970b6-126">Protokolování zpráv lze povolit v klientech i službě jakékoli aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="970b6-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="970b6-127">Chcete-li povolit protokolování zpráv, musíte do klienta nebo služby přidat následující kód:</span><span class="sxs-lookup"><span data-stu-id="970b6-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="970b6-128">Při záznamu zprávy je typ trasování závislý na tom, zda je sledován v klientovi nebo na serveru.</span><span class="sxs-lookup"><span data-stu-id="970b6-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="970b6-129">Například zpráva "Přidat", která je odeslána klientovi, je sledována pod kategorií "TransportWrite" na klientovi, zatímco stejná zpráva je sledována pod kategorií "TransportRead" ve službě.</span><span class="sxs-lookup"><span data-stu-id="970b6-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="970b6-130">Nakonfigurujte naslouchací proces trasování přidáním následujícího kódu do <xref:System.Diagnostics> oddílu souboru App. config klienta nebo souboru Web. config služby.</span><span class="sxs-lookup"><span data-stu-id="970b6-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 <span data-ttu-id="970b6-131">Zprávy jsou protokolovány ve formátu XML v cílovém adresáři zadaném v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="970b6-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="970b6-132">Trasovací soubory se nevytvoří bez prvotního vytvoření adresáře protokolu.</span><span class="sxs-lookup"><span data-stu-id="970b6-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="970b6-133">Ujistěte se, že adresář C:\logs\ existuje, nebo zadejte alternativní adresář protokolování v konfiguraci naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="970b6-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="970b6-134">Další informace najdete v úvodních pokynech k nastavení na konci tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="970b6-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="970b6-135">Další informace o protokolování zpráv najdete v tématu [Konfigurace protokolování zpráv](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="970b6-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="970b6-136">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="970b6-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="970b6-137">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="970b6-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="970b6-138">Před spuštěním ukázky trasování a protokolování zpráv vytvořte adresář C:\logs\, ve kterém bude služba zapisovat soubory. svclog do.</span><span class="sxs-lookup"><span data-stu-id="970b6-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="970b6-139">Název tohoto adresáře je definovaný v konfiguračním souboru jako cesta pro trasování a zprávy, které se mají protokolovat a které je možné změnit.</span><span class="sxs-lookup"><span data-stu-id="970b6-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="970b6-140">Udělte síťové službě uživatele přístup pro zápis do adresáře Logs.</span><span class="sxs-lookup"><span data-stu-id="970b6-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="970b6-141">Pokud chcete vytvořit C#edici, C++nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="970b6-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="970b6-142">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="970b6-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="970b6-143">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="970b6-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="970b6-144">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="970b6-144">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="970b6-145">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="970b6-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="970b6-146">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="970b6-146">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="970b6-147">Viz také:</span><span class="sxs-lookup"><span data-stu-id="970b6-147">See also</span></span>

- [<span data-ttu-id="970b6-148">Trasování</span><span class="sxs-lookup"><span data-stu-id="970b6-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [<span data-ttu-id="970b6-149">Ukázky monitorování technologie AppFabric</span><span class="sxs-lookup"><span data-stu-id="970b6-149">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
