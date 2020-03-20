---
title: Použití čítačů výkonu
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 7ffd9f5de5efb4be22968958246839e804daf23d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143574"
---
# <a name="using-performance-counters"></a><span data-ttu-id="3d1cd-102">Použití čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="3d1cd-102">Using Performance Counters</span></span>
<span data-ttu-id="3d1cd-103">Tato ukázka ukazuje, jak získat přístup k čítačům výkonu WCF (Windows Communication Foundation) a jak vytvořit uživatelem definované čítače výkonu.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="3d1cd-104">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3d1cd-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d1cd-105">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3d1cd-106">V této ukázce klient volá `ICalculator` čtyři metody služby.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="3d1cd-107">Klient pokračuje v tomto, dokud je přerušen uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="3d1cd-108">Služba zůstane nezměněna.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="3d1cd-109">Čítače výkonu jsou povoleny v části diagnostika souboru Web.config pro službu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3d1cd-110">Tuto úlohu lze provést také pomocí [nástroje Editor konfigurace (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3d1cd-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="3d1cd-111">Pokud jsou povoleny čítače výkonu, je pro službu povolena celá sada čítačů výkonu WCF.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="3d1cd-112">Rozhraní .NET Framework automaticky udržuje údaje `ServiceModelService`o `ServiceModelEndpoint` `ServiceModelOperation`výkonu na třech úrovních: a .</span><span class="sxs-lookup"><span data-stu-id="3d1cd-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="3d1cd-113">Každá z těchto úrovní má čítače výkonu, například "Volání", "Volání za sekundu" a "Bezpečnostní volání nejsou autorizována".</span><span class="sxs-lookup"><span data-stu-id="3d1cd-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d1cd-114">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3d1cd-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3d1cd-115">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d1cd-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3d1cd-116">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d1cd-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3d1cd-117">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3d1cd-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="3d1cd-118">Zobrazení dat o výkonu</span><span class="sxs-lookup"><span data-stu-id="3d1cd-118">To view performance data</span></span>  
  
1. <span data-ttu-id="3d1cd-119">Spusťte nástroj sledování výkonu klepnutím na `perfmon` tlačítko **Start**, **Spustit...**, zadejte a klepněte na tlačítko **OK** nebo v ovládacím panelu vyberte nástroje **pro správu** a poklepejte na **položku Výkon**.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3d1cd-120">Nelze přidat čítače, dokud ukázkový kód je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="3d1cd-121">Odeberte čítače výkonu, které jsou uvedeny, tak, že je vyberete a stisknete klávesu Delete.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="3d1cd-122">Přidejte čítače WCF tak, že kliknete pravým tlačítkem myši na podokno grafu a vyberete **přidat čítače**.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="3d1cd-123">V dialogovém okně **Přidat čítače** vyberte v rozevíracím seznamu Objekt výkonu položku **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0 nebo ServiceModelService 3.0.0.0.**</span><span class="sxs-lookup"><span data-stu-id="3d1cd-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="3d1cd-124">Ze seznamu vyberte čítače, které chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="3d1cd-125">Neexistují žádné čítače výkonu WCF pro službu, pokud nejsou k dispozici žádné služby WCF spuštěné v počítači.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="3d1cd-126">Povolení čítačů pomocí Editoru konfigurace</span><span class="sxs-lookup"><span data-stu-id="3d1cd-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="3d1cd-127">Otevřete instanci souboru SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="3d1cd-128">V nabídce Soubor klepněte na tlačítko **Otevřít** a potom klepněte na **položku Konfigurační soubor...**.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="3d1cd-129">Přejděte do složky služby ukázkové aplikace a otevřete soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="3d1cd-130">Ve stromu Konfigurace klikněte na **Diagnostika.**</span><span class="sxs-lookup"><span data-stu-id="3d1cd-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="3d1cd-131">Přepnout **čítač výkonu** v okně **Diagnostika** zobrazíte vše.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="3d1cd-132">Uložte konfigurační soubor a ukončete editor.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3d1cd-133">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3d1cd-134">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-134">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3d1cd-135">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d1cd-136">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3d1cd-136">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="3d1cd-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d1cd-137">See also</span></span>

- <span data-ttu-id="3d1cd-138">[Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3d1cd-138">[AppFabric Monitoring Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))</span></span>
