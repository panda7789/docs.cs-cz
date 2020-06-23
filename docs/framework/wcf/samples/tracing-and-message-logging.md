---
title: Trasování a protokolování zpráv
description: Naučte se používat nástroj pro prohlížení služby Service Trace Viewer (SvcTraceViewer.exe) k zobrazení trasování a protokolů zpráv pomocí této ukázky WFC.
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: bb49334252c2415223b0f8f5559a6dc838d175e3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246022"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="3a0ed-103">Trasování a protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="3a0ed-103">Tracing and Message Logging</span></span>
<span data-ttu-id="3a0ed-104">Tato ukázka demonstruje, jak povolit trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-104">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="3a0ed-105">Výsledné trasování a protokoly zpráv se zobrazují pomocí [nástroje Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3a0ed-105">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="3a0ed-106">Tato ukázka je založena na [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3a0ed-106">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a0ed-107">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="3a0ed-108">Trasování</span><span class="sxs-lookup"><span data-stu-id="3a0ed-108">Tracing</span></span>  
 <span data-ttu-id="3a0ed-109">Windows Communication Foundation (WCF) používá mechanismus trasování definovaný v <xref:System.Diagnostics> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-109">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="3a0ed-110">V tomto trasovacím modelu jsou data trasování vytvořena pomocí zdrojů trasování, které aplikace implementuje.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-110">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="3a0ed-111">Jednotlivé zdroje jsou označeny názvem.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-111">Each source is identified by a name.</span></span> <span data-ttu-id="3a0ed-112">Trasovat příjemce: Vytvoření posluchačů trasování pro zdroje trasování, pro které chtějí získat informace.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-112">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="3a0ed-113">Chcete-li přijímat data trasování, je nutné vytvořit naslouchací proces pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-113">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="3a0ed-114">V rámci služby WCF to můžete udělat přidáním následujícího kódu do konfiguračního souboru služby nebo klienta nastavením zdroje trasování modelu služby `switchValue` :</span><span class="sxs-lookup"><span data-stu-id="3a0ed-114">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="3a0ed-115">Další informace o zdrojích trasování naleznete v části zdroj trasování v tématu [Konfigurace trasování](../diagnostics/tracing/configuring-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="3a0ed-115">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="3a0ed-116">Trasování aktivit a šíření</span><span class="sxs-lookup"><span data-stu-id="3a0ed-116">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="3a0ed-117">`ActivityTracing`Povolení a `propagateActivity` nastavení `true` ve `system.ServiceModel` zdrojích trasování pro klienta i službu poskytují korelaci trasování v rámci logických jednotek zpracování (aktivity), napříč aktivitami v koncových bodech (prostřednictvím přenosů aktivit) a napříč aktivitami zahrnujícími více koncových bodů (prostřednictvím šíření ID aktivity).</span><span class="sxs-lookup"><span data-stu-id="3a0ed-117">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="3a0ed-118">Tyto tři mechanismy (aktivity, přenosy a šíření) vám mohou pomoci najít hlavní příčinu chyby rychleji pomocí nástroje Prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-118">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="3a0ed-119">Další informace najdete v tématu [použití prohlížeče trasování služby pro zobrazení korelačních trasování a odstraňování potíží](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="3a0ed-119">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="3a0ed-120">Je možné roztáhnout trasování, které poskytuje ServiceModel, vytvořením trasování aktivity definované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-120">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="3a0ed-121">Trasování uživatelsky definované aktivity umožňuje uživateli vytvářet aktivity trasování pro:</span><span class="sxs-lookup"><span data-stu-id="3a0ed-121">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="3a0ed-122">Seskupí trasování do logických pracovních jednotek.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-122">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="3a0ed-123">Korelujte aktivity prostřednictvím přenosů a šíření.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-123">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="3a0ed-124">Snížit náklady na výkon trasování WCF (například náklady na místo na disku souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="3a0ed-124">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="3a0ed-125">Další informace o uživatelsky definovaném trasování aktivit najdete v ukázce [rozšíření trasování](extending-tracing.md) .</span><span class="sxs-lookup"><span data-stu-id="3a0ed-125">For more information about user-defined activity trace, please see the [Extending Tracing](extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="3a0ed-126">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="3a0ed-126">Message Logging</span></span>  
 <span data-ttu-id="3a0ed-127">Protokolování zpráv lze povolit v klientech i službě jakékoli aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-127">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="3a0ed-128">Chcete-li povolit protokolování zpráv, musíte do klienta nebo služby přidat následující kód:</span><span class="sxs-lookup"><span data-stu-id="3a0ed-128">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="3a0ed-129">Při záznamu zprávy je typ trasování závislý na tom, zda je sledován v klientovi nebo na serveru.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-129">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="3a0ed-130">Například zpráva "Přidat", která je odeslána klientovi, je sledována pod kategorií "TransportWrite" na klientovi, zatímco stejná zpráva je sledována pod kategorií "TransportRead" ve službě.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-130">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="3a0ed-131">Nakonfigurujte naslouchací proces trasování přidáním následujícího kódu do <xref:System.Diagnostics> oddílu App.config souboru klienta nebo Web.config souboru služby:</span><span class="sxs-lookup"><span data-stu-id="3a0ed-131">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="3a0ed-132">Zprávy jsou protokolovány ve formátu XML v cílovém adresáři zadaném v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-132">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a0ed-133">Trasovací soubory se nevytvoří bez prvotního vytvoření adresáře protokolu.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-133">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="3a0ed-134">Ujistěte se, že adresář C:\logs\ existuje, nebo zadejte alternativní adresář protokolování v konfiguraci naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-134">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="3a0ed-135">Další informace najdete v úvodních pokynech k nastavení na konci tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-135">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="3a0ed-136">Další informace o protokolování zpráv najdete v tématu [Konfigurace protokolování zpráv](../diagnostics/configuring-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="3a0ed-136">For more information about message logging, see the [Configuring Message Logging](../diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3a0ed-137">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3a0ed-137">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3a0ed-138">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a0ed-138">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3a0ed-139">Před spuštěním ukázky trasování a protokolování zpráv vytvořte adresář C:\logs\, ve kterém bude služba zapisovat soubory. svclog do.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-139">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="3a0ed-140">Název tohoto adresáře je definovaný v konfiguračním souboru jako cesta pro trasování a zprávy, které se mají protokolovat a které je možné změnit.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-140">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="3a0ed-141">Udělte síťové službě uživatele přístup pro zápis do adresáře Logs.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-141">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="3a0ed-142">Chcete-li sestavit edici C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a0ed-142">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3a0ed-143">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3a0ed-143">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3a0ed-144">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-144">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3a0ed-145">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-145">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3a0ed-146">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3a0ed-147">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3a0ed-147">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="3a0ed-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="3a0ed-148">See also</span></span>

- [<span data-ttu-id="3a0ed-149">Trasování</span><span class="sxs-lookup"><span data-stu-id="3a0ed-149">Tracing</span></span>](../diagnostics/tracing/index.md)
- <span data-ttu-id="3a0ed-150">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3a0ed-150">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
