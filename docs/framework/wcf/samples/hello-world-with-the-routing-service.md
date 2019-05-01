---
title: Hello World se směrovací službou
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 37d2eaffa1ca5a4cce27c4950d00987828a61196
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62006600"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="a0180-102">Hello World se směrovací službou</span><span class="sxs-lookup"><span data-stu-id="a0180-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="a0180-103">Tato ukázka předvádí, směrovací služba Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a0180-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="a0180-104">Směrovací služba je komponenta WCF, která umožňuje snadno do aplikace zahrnout směrovač založené na obsahu.</span><span class="sxs-lookup"><span data-stu-id="a0180-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="a0180-105">Tato ukázka se přizpůsobí standardní kalkulačky Ukázky WCF na komunikaci pomocí služby směrování.</span><span class="sxs-lookup"><span data-stu-id="a0180-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="a0180-106">V této ukázce je Kalkulačka klient nakonfigurovaný pro odesílání zpráv do koncového bodu určeného směrovače.</span><span class="sxs-lookup"><span data-stu-id="a0180-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="a0180-107">Směrovací služba je nakonfigurována tak, aby přijímal všechny zprávy odeslané do ní a předávají do koncového bodu, který odpovídá službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a0180-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="a0180-108">Proto jsou zpráv odeslaných z klienta přijatých směrovač a přesměrovala do aktuální Kalkulačka služby.</span><span class="sxs-lookup"><span data-stu-id="a0180-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="a0180-109">Zprávy ze služby Kalkulačka odesílají zpět do směrovač, který je zase předá zpět do klienta kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="a0180-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="a0180-110">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="a0180-110">To use this sample</span></span>

1. <span data-ttu-id="a0180-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="a0180-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="a0180-112">Stiskněte klávesu F5 nebo CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="a0180-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="a0180-113">Pokud stisknete klávesu F5, spustí se automaticky Kalkulačka klienta.</span><span class="sxs-lookup"><span data-stu-id="a0180-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="a0180-114">Pokud stisknete CTRL + SHIFT + B (sestavení), je nutné spustit následující aplikace sami.</span><span class="sxs-lookup"><span data-stu-id="a0180-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="a0180-115">Kalkulačka klienta (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="a0180-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="a0180-116">Kalkulačka služby (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="a0180-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="a0180-117">Služba směrování (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="a0180-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="a0180-118">Stisknutím klávesy ENTER klienta.</span><span class="sxs-lookup"><span data-stu-id="a0180-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="a0180-119">Byste měli vidět následující výstup:</span><span class="sxs-lookup"><span data-stu-id="a0180-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="a0180-120">Konfigurovat pomocí kódu nebo souboru App.Config</span><span class="sxs-lookup"><span data-stu-id="a0180-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="a0180-121">Ukázka lodí umožňují definovat chování ve směrovači použít soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="a0180-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="a0180-122">Můžete také změnit název souboru App.config na něco jiného, tak, aby nebyl rozpoznán a zrušte komentář u volání metod, které ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="a0180-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="a0180-123">Některé z metod má za následek stejné chování směrovače.</span><span class="sxs-lookup"><span data-stu-id="a0180-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="a0180-124">Scénář</span><span class="sxs-lookup"><span data-stu-id="a0180-124">Scenario</span></span>
 <span data-ttu-id="a0180-125">Tato ukázka předvádí, směrovač, který funguje jako základní zprávy odeslané.</span><span class="sxs-lookup"><span data-stu-id="a0180-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="a0180-126">Směrovací služba funguje jako uzel transparentní proxy server nakonfigurovaný tak, aby předávání zpráv přímo do předkonfigurovaného sadu cílové koncové body.</span><span class="sxs-lookup"><span data-stu-id="a0180-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="a0180-127">Reálné scénáře</span><span class="sxs-lookup"><span data-stu-id="a0180-127">Real World Scenario</span></span>
 <span data-ttu-id="a0180-128">Contoso chce zvýšit flexibilitu, které se má v pojmenování, adresy, konfigurace a zabezpečení svých služeb.</span><span class="sxs-lookup"><span data-stu-id="a0180-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="a0180-129">Provedete to tak, že umístit základní zprávy odeslané před jejich služby tak, aby fungoval jako veřejný internetový koncový bod.</span><span class="sxs-lookup"><span data-stu-id="a0180-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="a0180-130">To umožňuje umístit další zabezpečení před jejich skutečné služby a usnadňují implementace řešení nebo Správa verzí služby škálované později.</span><span class="sxs-lookup"><span data-stu-id="a0180-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="a0180-131">Vzorky mohou již být nainstalováno ve vašem počítači.</span><span class="sxs-lookup"><span data-stu-id="a0180-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a0180-132">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="a0180-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a0180-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="a0180-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a0180-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="a0180-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="a0180-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0180-135">See also</span></span>

- [<span data-ttu-id="a0180-136">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="a0180-136">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
