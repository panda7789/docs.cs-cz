---
title: Dynamická rekonfigurace
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 36b548ee47ed9165743bbfb1eaab5cf3bbe82bd2
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="a9387-102">Dynamická rekonfigurace</span><span class="sxs-lookup"><span data-stu-id="a9387-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="a9387-103">Tento příklad ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směrování služby.</span><span class="sxs-lookup"><span data-stu-id="a9387-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="a9387-104">Služba směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komponenty, která usnadňuje do aplikace zahrnout směrovač podle obsahu.</span><span class="sxs-lookup"><span data-stu-id="a9387-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="a9387-105">Tato ukázka přizpůsobuje standardní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázka kalkulačku komunikovat pomocí služby směrování.</span><span class="sxs-lookup"><span data-stu-id="a9387-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="a9387-106">Tento příklad ukazuje, jak službu směrování můžete dynamicky překonfigurovat za běhu.</span><span class="sxs-lookup"><span data-stu-id="a9387-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9387-107">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="a9387-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a9387-108">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a9387-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a9387-109">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a9387-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9387-110">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a9387-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="a9387-111">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="a9387-111">Sample Details</span></span>  
 <span data-ttu-id="a9387-112">Dynamicky znovu nakonfigurovat službu Směrování za běhu, aktivuje se tato ukázka časovače každých pět sekund, který vytvoří nový <xref:System.ServiceModel.Routing.RoutingConfiguration> objektu a použije ji.</span><span class="sxs-lookup"><span data-stu-id="a9387-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="a9387-113">Tato konfigurace odkazuje regulární koncový bod kalkulačky nebo zaokrouhlení kalkulačky koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a9387-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="a9387-114">Kalkulačky klientská aplikace má jeho zpráv vrácených z jedné služby nebo dalších, podle toho, která je nakonfigurovaná služba Směrování pro trasy, která má v daném čase.</span><span class="sxs-lookup"><span data-stu-id="a9387-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="a9387-115">Směrovací služba capabilitiy pro dynamická Rekonfigurace prostřednictvím vlastní chování se používá.</span><span class="sxs-lookup"><span data-stu-id="a9387-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="a9387-116">Toto vlastní chování připojí rozšíření služby, který obsahuje jednoduché vlákno časovač, který aktivuje každých pět sekund, což vede k zpětné volání pro `UpdateRules` metoda.</span><span class="sxs-lookup"><span data-stu-id="a9387-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="a9387-117">Tento zpětného volání vytvoří a použije se nová konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="a9387-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="a9387-118">V skutečné nasazení by tento zpětného volání dosáhnout pravděpodobně v důsledku jiný typ události, jako je například oznámení o události SQL nebo WS-Discovery oznámení.</span><span class="sxs-lookup"><span data-stu-id="a9387-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a9387-119">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a9387-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="a9387-120">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete DynamicReconfiguration.sln.</span><span class="sxs-lookup"><span data-stu-id="a9387-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="a9387-121">Chcete-li otevřít **Průzkumníku řešení**, vyberte **Průzkumníku řešení** z **zobrazení** nabídky.</span><span class="sxs-lookup"><span data-stu-id="a9387-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="a9387-122">Stiskněte klávesu **F5** nebo **CTRL + SHIFT + B** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a9387-122">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="a9387-123">Pokud byste chtěli automaticky spouštěné projekty potřebné při stisknutí volby **F5**, klikněte pravým tlačítkem na řešení a vyberte **vlastnosti**.</span><span class="sxs-lookup"><span data-stu-id="a9387-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="a9387-124">Vyberte **spouštěný projekt** pod uzlem **společných vlastností** v levém podokně.</span><span class="sxs-lookup"><span data-stu-id="a9387-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="a9387-125">Vyberte **více projektů po spuštění** přepínač a nastavte všechny projekty, které chcete mít **spustit** akce.</span><span class="sxs-lookup"><span data-stu-id="a9387-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="a9387-126">Pokud vytvoříte projekt pomocí **CTRL + SHIFT + B**, musíte spustit následující aplikace:</span><span class="sxs-lookup"><span data-stu-id="a9387-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="a9387-127">Klient kalkulačky (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="a9387-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="a9387-128">Službu kalkulačky (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="a9387-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="a9387-129">Směrovací služba provádí kalkulačky (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="a9387-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="a9387-130">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="a9387-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="a9387-131">V okně konzoly klienta kalkulačky stiskněte klávesu ENTER k spuštění klienta a volání operací služby kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a9387-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="a9387-132">Směrovací služba provádí směrování zpráv kalkulačky zaokrouhlení a regulární kalkulačky případně jako směrování změny konfigurace dynamicky každých pět sekund.</span><span class="sxs-lookup"><span data-stu-id="a9387-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="a9387-133">V závislosti na tom, ke kterému koncovému bodu službu Směrování je nakonfigurován pro odesílání zpráv do existují různé výstupy v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="a9387-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="a9387-134">Pokračujte stisknutím klávesy ENTER opakovaně přes více než pět sekund a sledovat změnu ve výsledcích ze služby.</span><span class="sxs-lookup"><span data-stu-id="a9387-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="a9387-135">Zde je, že výstup vrácena, pokud je služba směrovače je konfigurovaná pro směrování zpráv do služby zaokrouhlení kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a9387-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="a9387-136">Toto je výstup vrácena, pokud směrování služba je nakonfigurována pro směrování zpráv ke službě regulární kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a9387-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="a9387-137">Službu kalkulačky a službu kalkulačky zaokrouhlení také vytisknout protokolu operací vyvolat do svých příslušných konzoly windows.</span><span class="sxs-lookup"><span data-stu-id="a9387-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="a9387-138">V okně konzoly klienta typu "ukončit" a stiskněte klávesu ENTER ukončíte.</span><span class="sxs-lookup"><span data-stu-id="a9387-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="a9387-139">Stisknutím klávesy ENTER v oknech konzoly služby ukončení služby.</span><span class="sxs-lookup"><span data-stu-id="a9387-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="a9387-140">Scénář</span><span class="sxs-lookup"><span data-stu-id="a9387-140">Scenario</span></span>  
 <span data-ttu-id="a9387-141">Tento příklad znázorňuje směrovač, který funguje jako směrovač založená na obsahu umožňuje více typů nebo implementace služby mají být exponovány prostřednictvím jeden koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a9387-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="a9387-142">Scénář skutečných</span><span class="sxs-lookup"><span data-stu-id="a9387-142">Real World Scenario</span></span>  
 <span data-ttu-id="a9387-143">Contoso chce k virtualizaci všech svých služeb vystavit pouze jeden koncový bod veřejně přes která nabízejí přístup k několika různých typů služeb.</span><span class="sxs-lookup"><span data-stu-id="a9387-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="a9387-144">V takovém případě využívají službu směrování na základě obsahu směrování možnosti k určení, kde by měly být odeslány příchozí požadavky.</span><span class="sxs-lookup"><span data-stu-id="a9387-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9387-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="a9387-145">See Also</span></span>  
 [<span data-ttu-id="a9387-146">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="a9387-146">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
