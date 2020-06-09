---
title: Použití čítačů výkonu
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 0b63cdc145ff8806c26b255500bcb2a132e9ef9f
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596497"
---
# <a name="using-performance-counters"></a><span data-ttu-id="91609-102">Použití čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="91609-102">Using Performance Counters</span></span>
<span data-ttu-id="91609-103">Tato ukázka předvádí, jak získat přístup k čítačům výkonu služby Windows Communication Foundation (WCF) a jak vytvořit uživatelsky definované čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="91609-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="91609-104">Tato ukázka je založena na [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="91609-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91609-105">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="91609-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="91609-106">V této ukázce klient volá čtyři metody `ICalculator` služby.</span><span class="sxs-lookup"><span data-stu-id="91609-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="91609-107">Klient to bude pokračovat, dokud ho uživatel nepřerušil.</span><span class="sxs-lookup"><span data-stu-id="91609-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="91609-108">Služba zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="91609-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="91609-109">Čítače výkonu jsou povoleny v části Diagnostika v souboru Web. config pro službu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="91609-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="91609-110">Tuto úlohu lze provést také pomocí [nástroje Configuration Editor (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="91609-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="91609-111">Pokud jsou povoleny čítače výkonu, je pro službu povolena celá sada čítačů výkonu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="91609-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="91609-112">.NET Framework automaticky udržuje údaje o výkonu na třech úrovních: `ServiceModelService` `ServiceModelEndpoint` a `ServiceModelOperation` .</span><span class="sxs-lookup"><span data-stu-id="91609-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="91609-113">Každá z těchto úrovní má čítače výkonu, jako jsou volání "hovory", "hovory za sekundu" a "volání zabezpečení nejsou autorizována".</span><span class="sxs-lookup"><span data-stu-id="91609-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="91609-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="91609-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="91609-115">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="91609-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="91609-116">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="91609-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="91609-117">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="91609-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="91609-118">Zobrazení údajů o výkonu</span><span class="sxs-lookup"><span data-stu-id="91609-118">To view performance data</span></span>  
  
1. <span data-ttu-id="91609-119">Spusťte nástroj sledování výkonu kliknutím na tlačítko **Start**, **Spustit...**, zadejte `perfmon` a klikněte na tlačítko **OK** nebo v Ovládacích panelech vyberte možnost **Nástroje pro správu** a dvakrát klikněte na položku **výkon**.</span><span class="sxs-lookup"><span data-stu-id="91609-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="91609-120">Čítače nelze přidat, dokud není spuštěn vzorový kód.</span><span class="sxs-lookup"><span data-stu-id="91609-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="91609-121">Odeberte čítače výkonu, které jsou uvedeny výběrem a stisknutím klávesy DELETE.</span><span class="sxs-lookup"><span data-stu-id="91609-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="91609-122">Přidejte čítače WCF kliknutím pravým tlačítkem myši na Podokno grafu a výběrem možnosti **Přidat čítače**.</span><span class="sxs-lookup"><span data-stu-id="91609-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="91609-123">V dialogovém okně **Přidat čítače** vyberte v rozevíracím seznamu objekt výkonu možnost **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 nebo ServiceModelService 3.0.0.0** .</span><span class="sxs-lookup"><span data-stu-id="91609-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="91609-124">V seznamu vyberte čítače, které chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="91609-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="91609-125">Nejsou-li v počítači žádné služby WCF spuštěné, neexistují žádné čítače výkonu WCF pro službu.</span><span class="sxs-lookup"><span data-stu-id="91609-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="91609-126">Použití editoru konfigurace k povolení čítačů</span><span class="sxs-lookup"><span data-stu-id="91609-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="91609-127">Otevřete instanci SvcConfigEditor. exe.</span><span class="sxs-lookup"><span data-stu-id="91609-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="91609-128">V nabídce soubor klikněte na **otevřít** a pak klikněte na **konfigurační soubor...**.</span><span class="sxs-lookup"><span data-stu-id="91609-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="91609-129">Přejděte do složky služby ukázkové aplikace a otevřete soubor Web. config.</span><span class="sxs-lookup"><span data-stu-id="91609-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="91609-130">Ve stromové struktuře konfigurace klikněte na **Diagnostika** .</span><span class="sxs-lookup"><span data-stu-id="91609-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="91609-131">Přepnutím **čítače výkonu** v okně **diagnostiky** zobrazíte možnost vše.</span><span class="sxs-lookup"><span data-stu-id="91609-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="91609-132">Uložte konfigurační soubor a ukončete Editor.</span><span class="sxs-lookup"><span data-stu-id="91609-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="91609-133">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="91609-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="91609-134">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="91609-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="91609-135">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="91609-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="91609-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="91609-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="91609-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="91609-137">See also</span></span>

- <span data-ttu-id="91609-138">[Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="91609-138">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
