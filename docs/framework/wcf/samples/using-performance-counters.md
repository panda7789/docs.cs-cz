---
title: Použití čítačů výkonu
ms.date: 03/30/2017
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
ms.openlocfilehash: 2c5042d497a09984a6f6c398a943b443ee9aafb9
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59302852"
---
# <a name="using-performance-counters"></a><span data-ttu-id="3e4f0-102">Použití čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="3e4f0-102">Using Performance Counters</span></span>
<span data-ttu-id="3e4f0-103">Tato ukázka předvádí, jak získat přístup k čítače výkonu Windows Communication Foundation (WCF) a jak vytvořit uživatelsky definovaným výkonem čítače.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-103">This sample demonstrates how to access Windows Communication Foundation (WCF) performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="3e4f0-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3e4f0-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e4f0-105">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3e4f0-106">V této ukázce, klient volá čtyři metody `ICalculator` služby.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="3e4f0-107">Klient i nadále to provést, dokud je přerušeno uživatelem.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="3e4f0-108">Služba zůstane beze změny.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="3e4f0-109">V části Diagnostika souboru Web.config pro službu, jsou povoleny čítače výkonu, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="3e4f0-110">Tato úloha je možné provést pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="3e4f0-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="3e4f0-111">Když jsou povoleny čítače výkonu, celou sadu čítače výkonu WCF je povolen pro službu.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-111">When performance counters are enabled, the entire suite of WCF performance counters is enabled for the service.</span></span> <span data-ttu-id="3e4f0-112">Rozhraní .NET Framework automaticky udržuje data o výkonu na třech úrovních: `ServiceModelService`, `ServiceModelEndpoint` a `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="3e4f0-113">Každá z těchto úrovní obsahuje čítače výkonu, jako je například "Volání", "Volání za sekundu" a "Zabezpečení volání nemáte oprávnění".</span><span class="sxs-lookup"><span data-stu-id="3e4f0-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3e4f0-114">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="3e4f0-114">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3e4f0-115">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e4f0-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3e4f0-116">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e4f0-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3e4f0-117">Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3e4f0-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="3e4f0-118">Chcete-li zobrazit údaje o výkonu</span><span class="sxs-lookup"><span data-stu-id="3e4f0-118">To view performance data</span></span>  
  
1. <span data-ttu-id="3e4f0-119">Spustit nástroj Sledování výkonu kliknutím **Start**, **spuštění...** , zadejte `perfmon` a klikněte na tlačítko **OK,** nebo v Ovládacích panelech vyberte **nástroje pro správu** a dvakrát klikněte na panel **výkonu**.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e4f0-120">Nelze přidat čítače, dokud vzorový kód je spuštěný.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-120">You cannot add counters until the sample code is running.</span></span>  
  
2. <span data-ttu-id="3e4f0-121">Odeberte čítačů výkonu, které jsou uvedeny tak, že je vyberete a stisknutím klávesy Delete.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3. <span data-ttu-id="3e4f0-122">Přidání čítačů WCF kliknutím pravým tlačítkem v podokně grafu a výběr **přidat čítače**.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-122">Add WCF counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="3e4f0-123">V **přidat čítače** dialogu **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 nebo ServiceModelService 3.0.0.0** v objektu výkonu rozevírací seznam pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="3e4f0-124">Vyberte čítače, které chcete zobrazit v seznamu.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="3e4f0-125">Pokud nejsou žádné WCF služby spuštěné v počítači nejsou žádné čítače výkonu WCF pro službu.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-125">There are no WCF performance counters for a service if there are no WCF services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="3e4f0-126">Použití editoru konfigurace pro povolení čítačů</span><span class="sxs-lookup"><span data-stu-id="3e4f0-126">To use the Configuration Editor to enable counters</span></span>  
  
1. <span data-ttu-id="3e4f0-127">Spusťte instanci SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2. <span data-ttu-id="3e4f0-128">V nabídce Soubor klikněte na tlačítko **otevřít** a potom klikněte na tlačítko **konfiguračního souboru...** .</span><span class="sxs-lookup"><span data-stu-id="3e4f0-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3. <span data-ttu-id="3e4f0-129">Přejděte do složky služby ukázkovou aplikaci a otevřete soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4. <span data-ttu-id="3e4f0-130">Klikněte na tlačítko **diagnostiky** ve stromové struktuře konfigurace.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5. <span data-ttu-id="3e4f0-131">Přepnout **čítač výkonu** v **diagnostiky** okno k zobrazení "Vše".</span><span class="sxs-lookup"><span data-stu-id="3e4f0-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6. <span data-ttu-id="3e4f0-132">Konfigurační soubor uložte a ukončete editor.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3e4f0-133">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="3e4f0-134">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="3e4f0-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="3e4f0-135">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3e4f0-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="3e4f0-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="3e4f0-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3e4f0-137">See also</span></span>

- [<span data-ttu-id="3e4f0-138">Ukázky AppFabric monitorování</span><span class="sxs-lookup"><span data-stu-id="3e4f0-138">AppFabric Monitoring Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193959)
