---
title: "Hello World se směrovací službou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6a03f3eeab6ce30c011a6f67c64cc3997130c895
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="b3406-102">Hello World se směrovací službou</span><span class="sxs-lookup"><span data-stu-id="b3406-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="b3406-103">Tento příklad ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="b3406-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Routing Service.</span></span> <span data-ttu-id="b3406-104">Služba směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komponenty, která usnadňuje směrovač na základě obsahu do aplikace zahrnout.</span><span class="sxs-lookup"><span data-stu-id="b3406-104">The Routing Service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="b3406-105">Tato ukázka přizpůsobuje standardní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázka kalkulačku na komunikaci pomocí služby směrování.</span><span class="sxs-lookup"><span data-stu-id="b3406-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="b3406-106">V této ukázce kalkulačky klient je nakonfigurován pro odesílání zpráv pro koncový bod vystavené směrovači.</span><span class="sxs-lookup"><span data-stu-id="b3406-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="b3406-107">Směrovací služby je nakonfigurován tak, aby přijímal všechny zprávy do něj odeslané a předávat je koncový bod, který odpovídá službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="b3406-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="b3406-108">Proto jsou zpráv odeslaných z klienta přijatých směrovači a přesměrovala ke službě skutečné kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="b3406-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="b3406-109">Zprávy ze služby kalkulačky jsou odesílány zpět na směrovač, který je pak předá zpět do klienta kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="b3406-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="b3406-110">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="b3406-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="b3406-111">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="b3406-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open HelloRoutingService.sln.</span></span>  
  
2.  <span data-ttu-id="b3406-112">Stisknutím klávesy F5 nebo CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="b3406-112">Press F5 or CTRL+SHIFT+B.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="b3406-113">Pokud stisknete klávesu F5, kalkulačky klienta se automaticky spustí.</span><span class="sxs-lookup"><span data-stu-id="b3406-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="b3406-114">Pokud stisknete klávesu CTRL + SHIFT + B (sestavení), musíte spustit následující aplikace sami.</span><span class="sxs-lookup"><span data-stu-id="b3406-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>  
    >   
    >  1.  <span data-ttu-id="b3406-115">Klient kalkulačky (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="b3406-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>  
    > 2.  <span data-ttu-id="b3406-116">Službu kalkulačky (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="b3406-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>  
    > 3.  <span data-ttu-id="b3406-117">Směrovací služba provádí (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="b3406-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>  
  
3.  <span data-ttu-id="b3406-118">Stiskněte klávesu ENTER a spusťte službu klienta.</span><span class="sxs-lookup"><span data-stu-id="b3406-118">Press ENTER to start the client.</span></span>  
  
     <span data-ttu-id="b3406-119">Byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="b3406-119">You should see the following output:</span></span>  
  
     <span data-ttu-id="b3406-120">Add(100,15.99) = 115.99</span><span class="sxs-lookup"><span data-stu-id="b3406-120">Add(100,15.99) = 115.99</span></span>  
  
     <span data-ttu-id="b3406-121">SUBTRACT(145,76.54) = 68.46</span><span class="sxs-lookup"><span data-stu-id="b3406-121">Subtract(145,76.54) = 68.46</span></span>  
  
     <span data-ttu-id="b3406-122">MULTIPLY(9,81.25) = 731.25</span><span class="sxs-lookup"><span data-stu-id="b3406-122">Multiply(9,81.25) = 731.25</span></span>  
  
     <span data-ttu-id="b3406-123">Divide(22,7) = 3.14285714285714</span><span class="sxs-lookup"><span data-stu-id="b3406-123">Divide(22,7) = 3.14285714285714</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="b3406-124">Konfigurovat pomocí kódu nebo App.Config</span><span class="sxs-lookup"><span data-stu-id="b3406-124">Configurable via Code or App.Config</span></span>  
 <span data-ttu-id="b3406-125">Ukázka lodě, umožňují použít soubor App.config k definování chování směrovače.</span><span class="sxs-lookup"><span data-stu-id="b3406-125">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="b3406-126">Můžete taky změnit název souboru App.config na jinou tak, aby nebyla rozpoznána a zrušte komentář u volání metody ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="b3406-126">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="b3406-127">Buď metoda výsledkem stejné chování z směrovači.</span><span class="sxs-lookup"><span data-stu-id="b3406-127">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="b3406-128">Scénář</span><span class="sxs-lookup"><span data-stu-id="b3406-128">Scenario</span></span>  
 <span data-ttu-id="b3406-129">Tento příklad znázorňuje směrovač, který funguje jako základní zprávy odeslané.</span><span class="sxs-lookup"><span data-stu-id="b3406-129">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="b3406-130">Směrovací služba funguje jako uzel transparentní proxy server nakonfigurovaný tak, aby předat zprávy přímo do předkonfigurované sadu cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="b3406-130">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="b3406-131">Scénář skutečných</span><span class="sxs-lookup"><span data-stu-id="b3406-131">Real World Scenario</span></span>  
 <span data-ttu-id="b3406-132">Contoso chce zvýšíte flexibilitu, který má v pojmenování, adresy, konfigurace a zabezpečení svých služeb.</span><span class="sxs-lookup"><span data-stu-id="b3406-132">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="b3406-133">K tomu, že umístit základní zprávy odeslané před jejich služby tak, aby fungoval jako veřejný koncový bod přístupných.</span><span class="sxs-lookup"><span data-stu-id="b3406-133">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="b3406-134">To umožňuje umístit další bezpečnostní před jejich skutečné služby, a usnadňují implementaci škálovat na více systémů verze služby nebo řešení později.</span><span class="sxs-lookup"><span data-stu-id="b3406-134">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b3406-135">Ukázky může být již nainstalován ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="b3406-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="b3406-136">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="b3406-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b3406-137">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="b3406-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b3406-138">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b3406-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="b3406-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3406-139">See Also</span></span>  
 [<span data-ttu-id="b3406-140">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="b3406-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
