---
title: "Použití čítačů výkonu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a787af-1876-473c-a48d-f52b51e28a3f
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 84cbbf83c240ae11099e2c9646150c810a437e71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-performance-counters"></a><span data-ttu-id="7061f-102">Použití čítačů výkonu</span><span class="sxs-lookup"><span data-stu-id="7061f-102">Using Performance Counters</span></span>
<span data-ttu-id="7061f-103">Tento příklad znázorňuje způsob pro přístup k [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] čítače výkonu a jak vytvořit uživateli definované čítače.</span><span class="sxs-lookup"><span data-stu-id="7061f-103">This sample demonstrates how to access [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] performance counters and how to create user-defined performance counters.</span></span> <span data-ttu-id="7061f-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="7061f-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7061f-105">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="7061f-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7061f-106">V této ukázce klienta volá čtyři metody `ICalculator` služby.</span><span class="sxs-lookup"><span data-stu-id="7061f-106">In this sample, the client calls the four methods of the `ICalculator` service.</span></span> <span data-ttu-id="7061f-107">Klient i nadále to provést, dokud přerušení uživatelem.</span><span class="sxs-lookup"><span data-stu-id="7061f-107">The client continues to do this until it is interrupted by the user.</span></span> <span data-ttu-id="7061f-108">Služba zůstává beze změny.</span><span class="sxs-lookup"><span data-stu-id="7061f-108">The service remains unchanged.</span></span>  
  
 <span data-ttu-id="7061f-109">V části Diagnostika souboru Web.config pro službu, jsou povoleny čítače výkonu, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7061f-109">Performance counters are enabled in the diagnostics section of the Web.config file for the service, as shown in the following sample configuration.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics performanceCounters="All" />   
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="7061f-110">Tuto úlohu lze provést pomocí [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7061f-110">This task can also be done using the [Configuration Editor Tool (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md).</span></span>  
  
 <span data-ttu-id="7061f-111">Když jsou povoleny čítače výkonu, celá sada [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] čítače výkonu je povolen pro službu.</span><span class="sxs-lookup"><span data-stu-id="7061f-111">When performance counters are enabled, the entire suite of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters is enabled for the service.</span></span> <span data-ttu-id="7061f-112">Rozhraní .NET Framework automaticky udržuje údaje o výkonu na třech úrovních: `ServiceModelService`, `ServiceModelEndpoint` a `ServiceModelOperation`.</span><span class="sxs-lookup"><span data-stu-id="7061f-112">The .NET Framework automatically maintains performance data at three levels: `ServiceModelService`, `ServiceModelEndpoint` and `ServiceModelOperation`.</span></span> <span data-ttu-id="7061f-113">Každý z těchto úrovní má čítače výkonu, jako je například "Volání", "Volání za sekundu" a "Zabezpečení volání není oprávněn".</span><span class="sxs-lookup"><span data-stu-id="7061f-113">Each of these levels has performance counters such as "Calls", "Calls per Second", and "Security Calls Not Authorized".</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7061f-114">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="7061f-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7061f-115">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7061f-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7061f-116">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7061f-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="7061f-117">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="7061f-117">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-view-performance-data"></a><span data-ttu-id="7061f-118">Zobrazení dat výkonu</span><span class="sxs-lookup"><span data-stu-id="7061f-118">To view performance data</span></span>  
  
1.  <span data-ttu-id="7061f-119">Spusťte nástroj Sledování výkonu kliknutím **spustit**, **spustit...** , zadejte `perfmon` a klikněte na tlačítko **OK,** nebo z ovládacích panelů, vyberte **nástroje pro správu** a dvakrát klikněte na **výkonu**.</span><span class="sxs-lookup"><span data-stu-id="7061f-119">Start the Performance Monitor Tool by clicking **Start**, **Run…**, enter `perfmon` and click **OK,** or from Control Panel, select **Administrative Tools** and double-click **Performance**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7061f-120">Čítače nelze přidat, dokud ukázkový kód běží.</span><span class="sxs-lookup"><span data-stu-id="7061f-120">You cannot add counters until the sample code is running.</span></span>  
  
2.  <span data-ttu-id="7061f-121">Odeberte čítače výkonu, které jsou uvedeny tak, že je vyberete a stisknutím klávesy Delete.</span><span class="sxs-lookup"><span data-stu-id="7061f-121">Remove the performance counters that are listed by selecting them and pressing the Delete key.</span></span>  
  
3.  <span data-ttu-id="7061f-122">Přidat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] čítače tak, že kliknete pravým tlačítkem v podokně grafu a výběr **přidat čítače**.</span><span class="sxs-lookup"><span data-stu-id="7061f-122">Add [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] counters by right-clicking the graph pane and selecting **Add Counters**.</span></span> <span data-ttu-id="7061f-123">V **přidat čítače** dialogové okno, vyberte **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0 nebo ServiceModelService 3.0.0.0** v objektu výkonu rozevírací seznam.</span><span class="sxs-lookup"><span data-stu-id="7061f-123">In the **Add Counters** dialog box, select **ServiceModelOperation 3.0.0.0, ServiceModelEndpoint 3.0.0.0, or ServiceModelService 3.0.0.0** in the Performance object drop down list box.</span></span> <span data-ttu-id="7061f-124">Vyberte čítače, které chcete zobrazit v seznamu.</span><span class="sxs-lookup"><span data-stu-id="7061f-124">Select the counters you want to view from the list.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7061f-125">Neexistují žádné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] čítače výkonu pro službu, pokud nejsou žádné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby spuštěné v počítači.</span><span class="sxs-lookup"><span data-stu-id="7061f-125">There are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] performance counters for a service if there are no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] services running on the computer.</span></span>  
  
### <a name="to-use-the-configuration-editor-to-enable-counters"></a><span data-ttu-id="7061f-126">Povolení čítačů pomocí editoru konfigurace</span><span class="sxs-lookup"><span data-stu-id="7061f-126">To use the Configuration Editor to enable counters</span></span>  
  
1.  <span data-ttu-id="7061f-127">Otevřete instanci SvcConfigEditor.exe.</span><span class="sxs-lookup"><span data-stu-id="7061f-127">Open an instance of the SvcConfigEditor.exe.</span></span>  
  
2.  <span data-ttu-id="7061f-128">V nabídce Soubor klikněte na tlačítko **otevřete** a pak klikněte na tlačítko **konfiguračního souboru...** .</span><span class="sxs-lookup"><span data-stu-id="7061f-128">On the File menu, click **Open** and then click **Config file…**.</span></span>  
  
3.  <span data-ttu-id="7061f-129">Přejděte do složky služby ukázkovou aplikaci a otevřete soubor Web.config.</span><span class="sxs-lookup"><span data-stu-id="7061f-129">Navigate to the sample application's service folder and open the Web.config file.</span></span>  
  
4.  <span data-ttu-id="7061f-130">Klikněte na tlačítko **diagnostiky** ve stromové struktuře konfigurace.</span><span class="sxs-lookup"><span data-stu-id="7061f-130">Click **Diagnostics** on the Configuration tree.</span></span>  
  
5.  <span data-ttu-id="7061f-131">Přepnutí **čítače výkonu** v **diagnostiky** okno a zobrazit všechny'.</span><span class="sxs-lookup"><span data-stu-id="7061f-131">Toggle **Performance Counter** in the **Diagnostics** window to show 'All'.</span></span>  
  
6.  <span data-ttu-id="7061f-132">Uložit konfigurační soubor a ukončete editor.</span><span class="sxs-lookup"><span data-stu-id="7061f-132">Save the configuration file and exit the editor.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7061f-133">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="7061f-133">The samples may already be installed on your computer.</span></span> <span data-ttu-id="7061f-134">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="7061f-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7061f-135">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="7061f-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7061f-136">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="7061f-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\PerfCounters`  
  
## <a name="see-also"></a><span data-ttu-id="7061f-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="7061f-137">See Also</span></span>  
 [<span data-ttu-id="7061f-138">Ukázky monitorování AppFabric</span><span class="sxs-lookup"><span data-stu-id="7061f-138">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
