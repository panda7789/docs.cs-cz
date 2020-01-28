---
title: Hello World se směrovací službou
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: ae0615c8cf2fa33f3bb363f77c0d06440b6afc13
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743719"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="2092e-102">Hello World se směrovací službou</span><span class="sxs-lookup"><span data-stu-id="2092e-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="2092e-103">Tato ukázka demonstruje směrovací službu Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="2092e-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="2092e-104">Směrovací služba je součást WCF, která usnadňuje zahrnutí směrovače založeného na obsahu do vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="2092e-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="2092e-105">Tato ukázka přizpůsobuje standardní ukázku kalkulačky WCF pro komunikaci pomocí směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="2092e-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="2092e-106">V této ukázce je klient kalkulačky nakonfigurovaný tak, aby odesílal zprávy na koncový bod vystavený směrovačem.</span><span class="sxs-lookup"><span data-stu-id="2092e-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="2092e-107">Směrovací služba je nakonfigurovaná tak, aby přijímala všechny odeslané zprávy, a přesměruje je do koncového bodu, který odpovídá službě kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="2092e-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="2092e-108">Tedy zprávy odesílané z klienta obdrží směrovač a znovu přesměrovány do skutečné služby kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="2092e-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="2092e-109">Zprávy ze služby kalkulačky se odesílají zpět do směrovače, který je zase předává do klienta kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="2092e-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="2092e-110">Použití této ukázky</span><span class="sxs-lookup"><span data-stu-id="2092e-110">To use this sample</span></span>

1. <span data-ttu-id="2092e-111">Pomocí sady Visual Studio 2012 otevřete HelloRoutingService. sln.</span><span class="sxs-lookup"><span data-stu-id="2092e-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="2092e-112">Stiskněte klávesu F5 nebo CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="2092e-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="2092e-113">Když stisknete klávesu F5, spustí se automaticky klient kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="2092e-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="2092e-114">Stisknete-li kombinaci kláves CTRL + SHIFT + B (sestavení), je nutné spustit následující aplikace sami.</span><span class="sxs-lookup"><span data-stu-id="2092e-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="2092e-115">Klient kalkulačky (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="2092e-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="2092e-116">Služba kalkulačky (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="2092e-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="2092e-117">Směrovací služba (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="2092e-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="2092e-118">Stisknutím klávesy ENTER spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="2092e-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="2092e-119">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="2092e-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="2092e-120">Konfigurovatelné prostřednictvím kódu nebo souboru App. config</span><span class="sxs-lookup"><span data-stu-id="2092e-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="2092e-121">Ukázková plavidla konfigurovaná pro použití souboru App. config k definování chování směrovače.</span><span class="sxs-lookup"><span data-stu-id="2092e-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="2092e-122">Můžete také změnit název souboru App. config na něco jiného, aby nebyl rozpoznán a odkomentovat volání metody ConfigureRouterViaCode ().</span><span class="sxs-lookup"><span data-stu-id="2092e-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="2092e-123">Kterákoli z metod má za následek stejné chování jako směrovač.</span><span class="sxs-lookup"><span data-stu-id="2092e-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="2092e-124">Scénář</span><span class="sxs-lookup"><span data-stu-id="2092e-124">Scenario</span></span>
 <span data-ttu-id="2092e-125">Tato ukázka demonstruje směrovač, který působí jako základní čerpadlo zpráv.</span><span class="sxs-lookup"><span data-stu-id="2092e-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="2092e-126">Směrovací služba funguje jako transparentní proxy uzel, který je nakonfigurován tak, aby předával zprávy přímo do předem nakonfigurované sady cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="2092e-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="2092e-127">Scénář reálného světa</span><span class="sxs-lookup"><span data-stu-id="2092e-127">Real World Scenario</span></span>
 <span data-ttu-id="2092e-128">Společnost Contoso chce zvýšit flexibilitu, kterou má při pojmenování, adresování, konfiguraci a zabezpečení svých služeb.</span><span class="sxs-lookup"><span data-stu-id="2092e-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="2092e-129">K tomu přistupují základní čerpadlo zpráv před svými službami, aby fungovaly jako veřejný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="2092e-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="2092e-130">Díky tomu mohou být před svými skutečnými službami zavedeny další zabezpečení a snadněji implementují škálovaná řešení nebo správu verzí služeb později.</span><span class="sxs-lookup"><span data-stu-id="2092e-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2092e-131">Ukázky již mohou být nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="2092e-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2092e-132">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="2092e-132">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="2092e-133">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples.</span><span class="sxs-lookup"><span data-stu-id="2092e-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2092e-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="2092e-134">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="2092e-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2092e-135">See also</span></span>

- <span data-ttu-id="2092e-136">[Hostování technologie AppFabric a ukázky trvalosti](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="2092e-136">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
