---
title: Použití čítačů výkonu
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 8784b4a481b8313d370aad1d8f265dcb44ab3ed6
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="using-performance-counters"></a><span data-ttu-id="9aae6-102">Použití čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="9aae6-102">Using Performance Counters</span></span>
<span data-ttu-id="9aae6-103">Tento příklad znázorňuje, jak získat přístup k čítače výkonu systému Windows Communication Foundation (WCF) a postup vytvoření čítače výkonu definovaný uživatelem.</span><span class="sxs-lookup"><span data-stu-id="9aae6-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="9aae6-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9aae6-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9aae6-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="9aae6-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9aae6-106">V této ukázce klienta volá čtyři metody `ICalculator` služby.</span><span class="sxs-lookup"><span data-stu-id="9aae6-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="9aae6-107">Klient i nadále to provést, dokud přerušení uživatelem.</span><span class="sxs-lookup"><span data-stu-id="9aae6-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="9aae6-108">Služba zůstává beze změny.</span><span class="sxs-lookup"><span data-stu-id="9aae6-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="9aae6-109">V části Diagnostika souboru Web.config pro službu, jsou povoleny čítače výkonu, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9aae6-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="9aae6-110">Tuto úlohu lze provést pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="9aae6-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="9aae6-111">Když jsou povoleny čítače výkonu, povolí se celá sada čítače výkonu WCF pro službu.</span><span class="sxs-lookup"><span data-stu-id="9aae6-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="9aae6-112">Rozhraní .NET Framework automaticky udržuje údaje o výkonu na třech úrovních: `ServiceModelService`, `ServiceModelEndpoint` a `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="9aae6-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="9aae6-113">Každý z těchto úrovní má čítače výkonu, jako je například "Volání", "Volání za sekundu" a "Zabezpečení volání není oprávněn".</span><span class="sxs-lookup"><span data-stu-id="9aae6-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9aae6-114">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="9aae6-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9aae6-115">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9aae6-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9aae6-116">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9aae6-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9aae6-117">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="9aae6-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="9aae6-118">Zobrazení dat výkonu</span><span class="sxs-lookup"><span data-stu-id="9aae6-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="9aae6-119">Spusťte nástroj Sledování výkonu kliknutím **spustit**, **spustit...** , zadejte `perfmon` a klikněte na tlačítko **OK,** nebo z ovládacích panelů, vyberte **nástroje pro správu** a dvakrát klikněte na **výkonu**.</span><span class="sxs-lookup"><span data-stu-id="9aae6-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9aae6-120">Čítače nelze přidat, dokud ukázkový kód běží.</span><span class="sxs-lookup"><span data-stu-id="9aae6-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="9aae6-121">Odeberte čítače výkonu, které jsou uvedeny tak, že je vyberete a stisknutím klávesy Delete.</span><span class="sxs-lookup"><span data-stu-id="9aae6-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="9aae6-122">Přidání čítačů WCF tak, že kliknete pravým tlačítkem v podokně grafu a výběr **přidat čítače**.</span><span class="sxs-lookup"><span data-stu-id="9aae6-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="9aae6-123">V **přidat čítače** dialogové okno, vyberte **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 nebo ServiceModelService 3.0.0.0** v objektu výkonu rozevírací seznam.</span><span class="sxs-lookup"><span data-stu-id="9aae6-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="9aae6-124">Vyberte čítače, které chcete zobrazit v seznamu.</span><span class="sxs-lookup"><span data-stu-id="9aae6-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9aae6-125">Neexistují žádné čítače výkonu WCF pro služby, pokud neexistují žádné služby WCF na tomto počítači spuštěna.</span><span class="sxs-lookup"><span data-stu-id="9aae6-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="9aae6-126">Povolení čítačů pomocí editoru konfigurace</span><span class="sxs-lookup"><span data-stu-id="9aae6-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="9aae6-127">Otevřete instanci SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="9aae6-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="9aae6-128">V nabídce Soubor klikněte na tlačítko **otevřete** a pak klikněte na tlačítko **konfiguračního souboru...** .</span><span class="sxs-lookup"><span data-stu-id="9aae6-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="9aae6-129">Přejděte do složky služby ukázkovou aplikaci a otevřete soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="9aae6-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="9aae6-130">Klikněte na tlačítko **diagnostiky** ve stromové struktuře konfigurace.</span><span class="sxs-lookup"><span data-stu-id="9aae6-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="9aae6-131">Přepnutí **čítače výkonu** v **diagnostiky** okno a zobrazit všechny'.</span><span class="sxs-lookup"><span data-stu-id="9aae6-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="9aae6-132">Uložit konfigurační soubor a ukončete editor.</span><span class="sxs-lookup"><span data-stu-id="9aae6-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9aae6-133">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="9aae6-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9aae6-134">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="9aae6-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9aae6-135">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="9aae6-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9aae6-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="9aae6-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="9aae6-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="9aae6-137">See Also</span></span>  
 [<span data-ttu-id="9aae6-138">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="9aae6-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
