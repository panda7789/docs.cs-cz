---
title: Dynamická rekonfigurace
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: a147a1d6cf61001832661376363ecc850ecad309
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43741101"
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="767cd-102">Dynamická rekonfigurace</span><span class="sxs-lookup"><span data-stu-id="767cd-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="767cd-103">V této ukázce směrovací službou Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="767cd-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="767cd-104">Směrovací služba je komponenta WCF, který umožňuje snadno do aplikace zahrnout směrovač založené na obsahu.</span><span class="sxs-lookup"><span data-stu-id="767cd-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="767cd-105">Tato ukázka se přizpůsobí standardní kalkulačky Ukázky WCF na komunikaci pomocí směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="767cd-105">This sample adapts the standard WCF Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="767cd-106">Tato ukázka předvádí, jak služba směrování můžete dynamicky překonfigurovat za běhu.</span><span class="sxs-lookup"><span data-stu-id="767cd-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="767cd-107">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="767cd-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="767cd-108">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="767cd-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="767cd-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="767cd-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="767cd-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="767cd-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="767cd-111">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="767cd-111">Sample Details</span></span>  
 <span data-ttu-id="767cd-112">Za běhu dynamicky rekonfigurovat směrovací službou, této ukázce aktivuje časovač každých pět sekund, který vytvoří nový <xref:System.ServiceModel.Routing.RoutingConfiguration> objektu a použije ho.</span><span class="sxs-lookup"><span data-stu-id="767cd-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="767cd-113">Tato konfigurace odkazuje běžným koncovým bodem Kalkulačka nebo koncový bod zaokrouhlení kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="767cd-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="767cd-114">Kalkulačka klientské aplikace má jeho zpráv vrácených z jedné služby nebo druhé, podle toho, která je nakonfigurovaná služba Směrování na trasy, která má v daném čase.</span><span class="sxs-lookup"><span data-stu-id="767cd-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="767cd-115">Směrovací služba capabilitiy pro dynamická Rekonfigurace prostřednictvím vlastního chování se používá.</span><span class="sxs-lookup"><span data-stu-id="767cd-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="767cd-116">Toto vlastní chování připojí rozšíření služby, který obsahuje jednoduché vláknu časovače, který se aktivuje každých pět sekund, což vede k zpětné volání, aby `UpdateRules` metody.</span><span class="sxs-lookup"><span data-stu-id="767cd-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="767cd-117">Toto zpětné volání vytvoří a použije novou konfiguraci směrování.</span><span class="sxs-lookup"><span data-stu-id="767cd-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="767cd-118">V skutečný nasazení by tato zpětné volání provedli pravděpodobně v důsledku jiného typu události, jako je například oznámení události SQL nebo WS-Discovery oznámení.</span><span class="sxs-lookup"><span data-stu-id="767cd-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="767cd-119">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="767cd-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="767cd-120">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete DynamicReconfiguration.sln.</span><span class="sxs-lookup"><span data-stu-id="767cd-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="767cd-121">Chcete-li otevřít **Průzkumníku řešení**vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="767cd-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="767cd-122">Stisknutím klávesy **F5** nebo **CTRL + SHIFT + B** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="767cd-122">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="767cd-123">Pokud chcete automaticky spouštět nezbytné projektů při stisknutí **F5**, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="767cd-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="767cd-124">Vyberte **spouštěný projekt** pod uzlem **společné vlastnosti** v levém podokně.</span><span class="sxs-lookup"><span data-stu-id="767cd-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="767cd-125">Vyberte **více projektů po spuštění** přepínač a nastavte všechny projekty, které mají mít **Start** akce.</span><span class="sxs-lookup"><span data-stu-id="767cd-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="767cd-126">Při sestavování projektu s **CTRL + SHIFT + B**, je nutné spustit v následujících aplikacích:</span><span class="sxs-lookup"><span data-stu-id="767cd-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="767cd-127">Kalkulačka klienta (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="767cd-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="767cd-128">Kalkulačka služby (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="767cd-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="767cd-129">Směrovací služba kalkulačky (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="767cd-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="767cd-130">Službu RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="767cd-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="767cd-131">V okně konzoly klienta kalkulačky stisknutím klávesy ENTER spustíte klienta a k volání operací služby kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="767cd-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="767cd-132">Směrovací služba provádí směrování zpráv ke kalkulačce zaokrouhlení a pravidelné Kalkulačka střídavě jako změny konfigurace směrování dynamicky každých pět sekund.</span><span class="sxs-lookup"><span data-stu-id="767cd-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="767cd-133">V závislosti na tom, ke kterému koncovému bodu směrovací služba je nakonfigurovaná k odesílání zpráv do existují jiné výstupy v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="767cd-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="767cd-134">Pokračujte stisknutím klávesy ENTER opakovaně přes více než pět sekund a sledovat změnu v hodnotě výsledky ze služby.</span><span class="sxs-lookup"><span data-stu-id="767cd-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="767cd-135">Zde je, že výstup vrátí, pokud směrovač služba je nakonfigurována pro směrování zpráv služby zaokrouhlení kalkulačku.</span><span class="sxs-lookup"><span data-stu-id="767cd-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="767cd-136">Zde je, že výstup vrátí, pokud směrovací služba je nakonfigurována pro směrování zpráv ke službě regulárních kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="767cd-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="767cd-137">Kalkulačka služba a služba zaokrouhlení Kalkulačka také vytisknout protokolu operací vyvolat a jejich odpovídajících konzoly windows.</span><span class="sxs-lookup"><span data-stu-id="767cd-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="767cd-138">V okně konzoly klienta typu "Ukončete" a stisknutím klávesy ENTER ukončete.</span><span class="sxs-lookup"><span data-stu-id="767cd-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="767cd-139">Stisknutím klávesy ENTER v oknech konzoly služby k ukončení služby.</span><span class="sxs-lookup"><span data-stu-id="767cd-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="767cd-140">Scénář</span><span class="sxs-lookup"><span data-stu-id="767cd-140">Scenario</span></span>  
 <span data-ttu-id="767cd-141">Tato ukázka předvádí, směrovač fungujícího jako směrovač založené na obsahu umožňuje více typů nebo implementaci služeb zpřístupní prostřednictvím jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="767cd-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="767cd-142">Reálné scénáře</span><span class="sxs-lookup"><span data-stu-id="767cd-142">Real World Scenario</span></span>  
 <span data-ttu-id="767cd-143">Contoso chce, aby se k virtualizaci všech svých služeb vystavit pouze jeden koncový bod veřejně přes který nabízejí přístup k více různých typů služeb.</span><span class="sxs-lookup"><span data-stu-id="767cd-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="767cd-144">V tomto případě využívat Služba směrování založené na obsahu směrování schopnosti určit, které by měla být odeslána příchozí požadavky.</span><span class="sxs-lookup"><span data-stu-id="767cd-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="767cd-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="767cd-145">See Also</span></span>  
 [<span data-ttu-id="767cd-146">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="767cd-146">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
