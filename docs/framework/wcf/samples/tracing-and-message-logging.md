---
title: Trasování a protokolování zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9ffb7a99540b953fc93a22d2296caf86f294d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143821"
---
# <a name="tracing-and-message-logging"></a><span data-ttu-id="08013-102">Trasování a protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="08013-102">Tracing and Message Logging</span></span>
<span data-ttu-id="08013-103">Tato ukázka ukazuje, jak povolit trasování a protokolování zpráv.</span><span class="sxs-lookup"><span data-stu-id="08013-103">This sample demonstrates how to enable tracing and message logging.</span></span> <span data-ttu-id="08013-104">Výsledné trasování a protokoly zpráv jsou zobrazeny pomocí [nástroje Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="08013-104">The resulting traces and message logs are viewed using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="08013-105">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="08013-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08013-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="08013-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="tracing"></a><span data-ttu-id="08013-107">Trasování</span><span class="sxs-lookup"><span data-stu-id="08013-107">Tracing</span></span>  
 <span data-ttu-id="08013-108">Windows Communication Foundation (WCF) používá mechanismus <xref:System.Diagnostics> trasování definované v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="08013-108">Windows Communication Foundation (WCF) uses the tracing mechanism defined in the <xref:System.Diagnostics> namespace.</span></span> <span data-ttu-id="08013-109">V tomto modelu trasování trasovací data je vytvářena zdroje trasování, které aplikace implementují.</span><span class="sxs-lookup"><span data-stu-id="08013-109">In this tracing model, trace data is produced by trace sources that applications implement.</span></span> <span data-ttu-id="08013-110">Každý zdroj je identifikován názvem.</span><span class="sxs-lookup"><span data-stu-id="08013-110">Each source is identified by a name.</span></span> <span data-ttu-id="08013-111">Trace spotřebitelé vytvořit naslouchací procesy trasování pro zdroje trasování, pro které chtějí načíst informace.</span><span class="sxs-lookup"><span data-stu-id="08013-111">Trace consumers create trace listeners for the trace sources for which they want to retrieve information.</span></span> <span data-ttu-id="08013-112">Chcete-li přijímat data trasování, musíte vytvořit naslouchací proces pro zdroj trasování.</span><span class="sxs-lookup"><span data-stu-id="08013-112">To receive trace data, you must create a listener for the trace source.</span></span> <span data-ttu-id="08013-113">V WCF to lze provést přidáním následujícího kódu do konfiguračního souboru služby `switchValue`nebo klienta nastavením zdroje trasování modelu služby :</span><span class="sxs-lookup"><span data-stu-id="08013-113">In WCF, this can be done by adding the following code to either the service’s or client’s configuration file by setting the Service Model trace source `switchValue`:</span></span>  
  
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
  
 <span data-ttu-id="08013-114">Další informace o zdrojích trasování naleznete v části Zdroj trasování v tématu [Konfigurace trasování.](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)</span><span class="sxs-lookup"><span data-stu-id="08013-114">For more information about trace sources, see the Trace Source section in the [Configuring Tracing](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) topic.</span></span>  
  
## <a name="activity-tracing-and-propagation"></a><span data-ttu-id="08013-115">Sledování a šíření aktivit</span><span class="sxs-lookup"><span data-stu-id="08013-115">Activity Tracing and Propagation</span></span>  
 <span data-ttu-id="08013-116">Povolení `ActivityTracing` a `propagateActivity` nastavení `true` ve `system.ServiceModel` zdrojích trasování pro klienta i službu poskytují korelaci trasování v rámci logických jednotek zpracování (aktivity), napříč aktivitami v rámci koncových bodů (prostřednictvím přenosů aktivit) a napříč aktivitami zahrnujícími více koncových bodů (prostřednictvím šíření ID aktivity).</span><span class="sxs-lookup"><span data-stu-id="08013-116">Having `ActivityTracing` enabled and `propagateActivity` set to `true` in the `system.ServiceModel` trace sources for both the client and service provide correlation of traces within logical units of processing (activities), across activities within endpoints (through activity transfers), and across activities spanning multiple endpoints (through activity ID propagation).</span></span>  
  
 <span data-ttu-id="08013-117">Tyto tři mechanismy (aktivity, přenosy a šíření) vám mohou pomoci rychleji vyhledat hlavní příčinu chyby pomocí nástroje Prohlížeč trasování služby.</span><span class="sxs-lookup"><span data-stu-id="08013-117">These three mechanisms (activities, transfers, and propagation) can help you locate the root cause of an error more quickly using the Service Trace Viewer tool.</span></span> <span data-ttu-id="08013-118">Další informace naleznete [v tématu Použití prohlížeče trasování služby pro zobrazení korelovaných trasování a řešení potíží](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span><span class="sxs-lookup"><span data-stu-id="08013-118">For more information, see [Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).</span></span>  
  
 <span data-ttu-id="08013-119">Je možné rozšířit trasování, které je poskytováno ServiceModel vytvořením uživatelem definované trasování aktivity.</span><span class="sxs-lookup"><span data-stu-id="08013-119">It is possible to extend the tracing that is provided by the ServiceModel by creating user-defined activity traces.</span></span> <span data-ttu-id="08013-120">Uživatelem definované trasování aktivit umožňuje uživateli vytvářet aktivity trasování do:</span><span class="sxs-lookup"><span data-stu-id="08013-120">User-defined activity tracing allows the user to create trace activities to:</span></span>  
  
- <span data-ttu-id="08013-121">Seskupit trasování do logických jednotek práce.</span><span class="sxs-lookup"><span data-stu-id="08013-121">Group traces into logical units of work.</span></span>  
  
- <span data-ttu-id="08013-122">Korelovat aktivity prostřednictvím přenosů a šíření.</span><span class="sxs-lookup"><span data-stu-id="08013-122">Correlate activities through transfers and propagation.</span></span>  
  
- <span data-ttu-id="08013-123">Směřovat náklady na výkon trasování WCF (například náklady na místo na disku souboru protokolu).</span><span class="sxs-lookup"><span data-stu-id="08013-123">Lessen the performance cost of WCF tracing (for example, the disk space cost of a log file).</span></span>  
  
 <span data-ttu-id="08013-124">Další informace o trasování aktivity definované uživatelem naleznete v tématu [Rozšíření trasování](../../../../docs/framework/wcf/samples/extending-tracing.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="08013-124">For more information about user-defined activity trace, please see the [Extending Tracing](../../../../docs/framework/wcf/samples/extending-tracing.md) sample.</span></span>  
  
## <a name="message-logging"></a><span data-ttu-id="08013-125">Protokolování zpráv</span><span class="sxs-lookup"><span data-stu-id="08013-125">Message Logging</span></span>  
 <span data-ttu-id="08013-126">Protokolování zpráv lze povolit v klientovi i ve službě libovolné aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="08013-126">Message logging can be enabled both on the client and service of any WCF application.</span></span> <span data-ttu-id="08013-127">Chcete-li povolit protokolování zpráv, je nutné přidat do klienta nebo služby následující kód:</span><span class="sxs-lookup"><span data-stu-id="08013-127">To enable message logging, you must add the following code to either the client or service:</span></span>  
  
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
  
 <span data-ttu-id="08013-128">Při zaznamenání zprávy, typ trasování závisí na tom, zda je trasována na straně klienta nebo serveru.</span><span class="sxs-lookup"><span data-stu-id="08013-128">When a message is recorded, the trace type depends on whether it is being traced at the client or the server.</span></span> <span data-ttu-id="08013-129">Například zpráva "Přidat", která je odeslána klientovi je sledována v rámci kategorie "TransportWrite" na straně klienta, zatímco stejná zpráva je sledována v rámci kategorie "TransportRead" ve službě.</span><span class="sxs-lookup"><span data-stu-id="08013-129">For example, an "Add" message that is sent to a client is traced under the "TransportWrite" category at the client, whereas the same message is traced under the "TransportRead" category at the service.</span></span>  
  
 <span data-ttu-id="08013-130">Nakonfigurujte naslouchací proces trasování přidáním následujícího kódu do <xref:System.Diagnostics> části souboru App.config klienta nebo souboru Web.config služby:</span><span class="sxs-lookup"><span data-stu-id="08013-130">Configure the trace listener by adding the following code to the <xref:System.Diagnostics> section of the client's App.config file or the service's Web.config file:</span></span>  
  
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
  
 <span data-ttu-id="08013-131">Zprávy jsou protokolovány ve formátu XML v cílovém adresáři určeném v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="08013-131">Messages are logged in XML format in the target directory specified in the configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="08013-132">Trasovací soubory nejsou vytvořeny bez počátečního vytvoření adresáře protokolu.</span><span class="sxs-lookup"><span data-stu-id="08013-132">Trace files are not created without initially creating the log directory.</span></span> <span data-ttu-id="08013-133">Ujistěte se, že adresář C:\logs\ existuje, nebo zadejte alternativní adresář protokolování v konfiguraci naslouchacího procesu.</span><span class="sxs-lookup"><span data-stu-id="08013-133">Make sure that the directory C:\logs\ exists, or specify an alternate logging directory in the listener configuration.</span></span> <span data-ttu-id="08013-134">Další informace naleznete v pokynech k počátečnímu nastavení na konci tohoto dokumentu.</span><span class="sxs-lookup"><span data-stu-id="08013-134">See the initial setup instructions at the end of this document for more information.</span></span>  
  
 <span data-ttu-id="08013-135">Další informace o protokolování zpráv naleznete v tématu [Konfigurace protokolování zpráv.](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)</span><span class="sxs-lookup"><span data-stu-id="08013-135">For more information about message logging, see the [Configuring Message Logging](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) topic.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="08013-136">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="08013-136">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="08013-137">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08013-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="08013-138">Před spuštěním ukázky Trasování a Protokolování zpráv vytvořte adresář C:\logs\ pro službu, do které bude zapisovat soubory Svclog.</span><span class="sxs-lookup"><span data-stu-id="08013-138">Before running the Tracing and Message Logging sample, create the directory C:\logs\ for the service to write the .svclog files to.</span></span> <span data-ttu-id="08013-139">Název tohoto adresáře je definován v konfiguračním souboru jako cesta pro trasování a zprávy, které mají být zaznamenány a lze je změnit.</span><span class="sxs-lookup"><span data-stu-id="08013-139">The name of this directory is defined in the configuration file as the path for the traces and messages to be logged and can be changed.</span></span> <span data-ttu-id="08013-140">Poučte uživateli síťovou službu přístup k adresáři protokolů.</span><span class="sxs-lookup"><span data-stu-id="08013-140">Give the user Network Service write access to the logs directory.</span></span>  
  
3. <span data-ttu-id="08013-141">Chcete-li vytvořit c#, C++ nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08013-141">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="08013-142">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="08013-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="08013-143">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="08013-143">The samples may already be installed on your computer.</span></span> <span data-ttu-id="08013-144">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="08013-144">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="08013-145">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="08013-145">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="08013-146">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="08013-146">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a><span data-ttu-id="08013-147">Viz také</span><span class="sxs-lookup"><span data-stu-id="08013-147">See also</span></span>

- [<span data-ttu-id="08013-148">Trasování</span><span class="sxs-lookup"><span data-stu-id="08013-148">Tracing</span></span>](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- <span data-ttu-id="08013-149">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="08013-149">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
