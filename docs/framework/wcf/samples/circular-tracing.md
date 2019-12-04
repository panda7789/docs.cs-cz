---
title: Cyklické sledování
ms.date: 03/30/2017
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
ms.openlocfilehash: b0778a25c75ae48c2215625f40b08a1e3815ba81
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716010"
---
# <a name="circular-tracing"></a><span data-ttu-id="3be4d-102">Cyklické sledování</span><span class="sxs-lookup"><span data-stu-id="3be4d-102">Circular Tracing</span></span>

<span data-ttu-id="3be4d-103">Tato ukázka demonstruje implementaci cyklického naslouchacího procesu trasování vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3be4d-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="3be4d-104">Běžným scénářem provozního provozu je, že služby jsou dostupné po dlouhou dobu a mají povolené protokolování trasování na nízké úrovni.</span><span class="sxs-lookup"><span data-stu-id="3be4d-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="3be4d-105">Tyto služby spotřebují spoustu místa na disku.</span><span class="sxs-lookup"><span data-stu-id="3be4d-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="3be4d-106">Při řešení potíží se službou jsou nejnovější data v protokolu trasování relevantní pro řešení problému.</span><span class="sxs-lookup"><span data-stu-id="3be4d-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="3be4d-107">Tato ukázka předvádí implementaci cyklického naslouchacího procesu trasování vyrovnávací paměti, ve kterém jsou uchovávána pouze nejnovější trasování na disku až do konfigurovatelného množství dat.</span><span class="sxs-lookup"><span data-stu-id="3be4d-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="3be4d-108">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) a obsahuje vlastní naslouchací proces trasování.</span><span class="sxs-lookup"><span data-stu-id="3be4d-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>

> [!NOTE]
> <span data-ttu-id="3be4d-109">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3be4d-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="3be4d-110">V této ukázce se předpokládá, že jste obeznámeni s ukázkou [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) a přečetli jste si dokumentaci k ukázce [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) .</span><span class="sxs-lookup"><span data-stu-id="3be4d-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>

## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="3be4d-111">Cyklická naslouchací proces trasování vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="3be4d-111">Circular Buffer Trace Listener</span></span>

<span data-ttu-id="3be4d-112">Koncept za implementaci cyklického naslouchacího procesu trasování vyrovnávací paměti má dva soubory, které mohou každý z nich uchovávat až polovinu celkových požadovaných dat protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="3be4d-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="3be4d-113">Naslouchací proces vytvoří jeden soubor a zapíše jej do tohoto souboru, dokud nedosáhne limitu poloviny velikosti dat, při které se přepne na druhý soubor.</span><span class="sxs-lookup"><span data-stu-id="3be4d-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="3be4d-114">Když naslouchací proces dosáhne limitu pro druhý soubor – přepíše první soubor novými trasováními.</span><span class="sxs-lookup"><span data-stu-id="3be4d-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>

<span data-ttu-id="3be4d-115">Tento naslouchací proces je odvozen z `XmlWriteTraceListener` a umožňuje zobrazení protokolů pomocí [Nástroje pro prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3be4d-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="3be4d-116">Při pokusu o zobrazení protokolů se tyto dva soubory protokolu dají snadno kombinovat otevřením obou souborů protokolu současně v nástroji Service Trace Viewer.</span><span class="sxs-lookup"><span data-stu-id="3be4d-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="3be4d-117">Nástroj Prohlížeč trasování služby automaticky postará o řazení trasování, aby se zobrazila ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="3be4d-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>

## <a name="configuration"></a><span data-ttu-id="3be4d-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="3be4d-118">Configuration</span></span>

<span data-ttu-id="3be4d-119">Službu lze nakonfigurovat tak, aby používala cyklické naslouchací proces trasování vyrovnávací paměti přidáním následujícího kódu pro naslouchací proces a zdrojové prvky.</span><span class="sxs-lookup"><span data-stu-id="3be4d-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="3be4d-120">Maximální velikost souboru je určena nastavením atributu `maxFileSizeKB` v konfiguraci cyklického naslouchacího procesu trasování.</span><span class="sxs-lookup"><span data-stu-id="3be4d-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="3be4d-121">To je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3be4d-121">This is demonstrated in the following code.</span></span>

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

#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3be4d-122">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3be4d-122">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="3be4d-123">Ujistěte se, že jste provedli [jednorázovou proceduru nastavení Windows Communication Foundation ukázek](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3be4d-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="3be4d-124">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3be4d-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="3be4d-125">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3be4d-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3be4d-126">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="3be4d-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3be4d-127">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3be4d-127">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="3be4d-128">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="3be4d-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3be4d-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3be4d-129">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`

## <a name="see-also"></a><span data-ttu-id="3be4d-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3be4d-130">See also</span></span>

- [<span data-ttu-id="3be4d-131">Ukázky monitorování technologie AppFabric</span><span class="sxs-lookup"><span data-stu-id="3be4d-131">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
