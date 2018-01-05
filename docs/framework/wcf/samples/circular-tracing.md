---
title: "Cyklické sledování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5ff139f9-8806-47bc-8f33-47fe6c436b92
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4942e7e23b3cddd0f1c5bd3be8195ceeb190ca3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="circular-tracing"></a><span data-ttu-id="d10d2-102">Cyklické sledování</span><span class="sxs-lookup"><span data-stu-id="d10d2-102">Circular Tracing</span></span>
<span data-ttu-id="d10d2-103">Tento příklad znázorňuje implementaci naslouchací cyklický vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d10d2-103">This sample demonstrates the implementation of a circular buffer trace listener.</span></span> <span data-ttu-id="d10d2-104">Běžný scénář pro produkční služby je potřeba mít služby, které jsou k dispozici pro dlouhou dobu a povoleno na nízké úrovni protokolování trasování.</span><span class="sxs-lookup"><span data-stu-id="d10d2-104">A common scenario for production services is to have services that are available for long periods of time and to have trace logging enabled at a low level.</span></span> <span data-ttu-id="d10d2-105">Tyto služby využívat velké množství místa na disku.</span><span class="sxs-lookup"><span data-stu-id="d10d2-105">These services consume a lot of disk space.</span></span> <span data-ttu-id="d10d2-106">Při odstraňování problémů s služby, aby nejnovější data v protokolu trasování je relevantní pro řešení problému.</span><span class="sxs-lookup"><span data-stu-id="d10d2-106">When troubleshooting a service, the most recent data in the trace log is relevant to solving a problem.</span></span> <span data-ttu-id="d10d2-107">Tento příklad znázorňuje implementaci ve kterém jsou uchovány pouze nejnovější trasování na disku až konfigurovat množství dat naslouchací cyklický vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="d10d2-107">This sample demonstrates an implementation of a circular buffer trace listener in which only the most recent traces are kept on disk up to a configurable amount of data.</span></span> <span data-ttu-id="d10d2-108">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) i vlastní trasování naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="d10d2-108">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and includes a custom tracing listener.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d10d2-109">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="d10d2-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d10d2-110">Tato ukázka se předpokládá, že jste obeznámeni s [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázkové a přečetli v dokumentaci k [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="d10d2-110">This sample assumes that you are familiar with the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample and have read the documentation provided for the [Tracing and Message Logging](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md) sample.</span></span>  
  
## <a name="circular-buffer-trace-listener"></a><span data-ttu-id="d10d2-111">Naslouchací proces trasování cyklické vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="d10d2-111">Circular Buffer Trace Listener</span></span>  
 <span data-ttu-id="d10d2-112">Koncept za implementace naslouchací proces trasování cyklické vyrovnávací paměti je mít dva soubory, které může každý ukládat až polovinu data protokolu celkový požadované trasování.</span><span class="sxs-lookup"><span data-stu-id="d10d2-112">The concept behind the implementation of the Circular Buffer Trace Listener is to have two files that can each store up to half of the total desired trace log data.</span></span> <span data-ttu-id="d10d2-113">Naslouchací proces vytvoří jeden soubor a zapíše do tohoto souboru, dokud nebude dosaženo limitu polovinu velikost dat, na který bod přepíná na druhý soubor.</span><span class="sxs-lookup"><span data-stu-id="d10d2-113">The listener creates one file and writes to that file until it reaches the limit of half of the data size, at which point it switches to a second file.</span></span> <span data-ttu-id="d10d2-114">Když se dosáhne naslouchací proces limit pro druhý soubor - přepíše první soubor se nová trasování.</span><span class="sxs-lookup"><span data-stu-id="d10d2-114">When the listener reaches the limit for the second file - it overwrites the first file with new traces.</span></span>  
  
 <span data-ttu-id="d10d2-115">Tato naslouchací proces je odvozena z `XmlWriteTraceListener` a umožňuje prohlížení s protokoly [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span><span class="sxs-lookup"><span data-stu-id="d10d2-115">This listener derives from the `XmlWriteTraceListener` and allows the logs to be viewed with the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="d10d2-116">Při pokusu o zobrazení protokolů, dva soubory protokolů můžete snadno rekombinované oba soubory protokolu otevřením současně v nástroji prohlížeče trasování služeb.</span><span class="sxs-lookup"><span data-stu-id="d10d2-116">When attempting to view the logs, the two log files can be easily recombined by opening both of the log files at the same time in the Service Trace Viewer tool.</span></span> <span data-ttu-id="d10d2-117">Nástroj prohlížeče trasování služeb automaticky postará řazení trasování tak, aby byly uvedeny ve správném pořadí.</span><span class="sxs-lookup"><span data-stu-id="d10d2-117">The Service Trace Viewer tool automatically takes care of sorting the traces so that they appear in the correct order.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="d10d2-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="d10d2-118">Configuration</span></span>  
 <span data-ttu-id="d10d2-119">Službu lze nakonfigurovat k využívání cyklické vyrovnávací paměti trasování modulu naslouchání přidáním následujícího kódu pro naslouchací proces a zdrojové elementy.</span><span class="sxs-lookup"><span data-stu-id="d10d2-119">A service can be configured to use the Circular Buffer Trace Listener by adding the following code for a listener and source elements.</span></span> <span data-ttu-id="d10d2-120">Maximální velikost je určený nastavením `maxFileSizeKB` atribut v konfiguraci naslouchacího procesu cyklické trasování.</span><span class="sxs-lookup"><span data-stu-id="d10d2-120">The max file size is specified by setting the `maxFileSizeKB` attribute in the circular trace listener's configuration.</span></span> <span data-ttu-id="d10d2-121">Tento postup je znázorněn v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d10d2-121">This is demonstrated in the following code.</span></span>  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d10d2-122">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="d10d2-122">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d10d2-123">Ujistěte se, kterou jste udělali [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d10d2-123">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d10d2-124">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d10d2-124">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d10d2-125">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d10d2-125">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d10d2-126">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="d10d2-126">The samples may already be installed on your computer.</span></span> <span data-ttu-id="d10d2-127">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="d10d2-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d10d2-128">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="d10d2-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d10d2-129">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="d10d2-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\CircularTracing`  
  
## <a name="see-also"></a><span data-ttu-id="d10d2-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d10d2-130">See Also</span></span>  
 [<span data-ttu-id="d10d2-131">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="d10d2-131">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
