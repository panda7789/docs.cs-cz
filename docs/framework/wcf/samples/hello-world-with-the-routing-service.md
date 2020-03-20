---
title: Hello World se směrovací službou
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 86a2981e8b861da9d5ccf0a34fe037f3ef419aab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183637"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="c6f6b-102">Hello World se směrovací službou</span><span class="sxs-lookup"><span data-stu-id="c6f6b-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="c6f6b-103">Tato ukázka ukazuje službu směrování WCF (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="c6f6b-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="c6f6b-104">Služba Směrování je součást WCF, která usnadňuje zahrnutí směrovače založeného na obsahu do aplikace.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="c6f6b-105">Tento příklad přizpůsobí standardní WCF ukázka kalkulačky komunikovat pomocí služby směrování.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="c6f6b-106">V této ukázce je klient kalkulačky nakonfigurován tak, aby odesílá zprávy do koncového bodu vystaveného směrovačem.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="c6f6b-107">Služba směrování je nakonfigurována tak, aby přijímala všechny zprávy, které jí byly odeslány, a přeposílala je do koncového bodu, který odpovídá službě Kalkulačka.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="c6f6b-108">Tak zprávy odeslané od klienta jsou přijímány routerem a přesměrovány na skutečnou službu Kalkulačka.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="c6f6b-109">Zprávy ze služby Kalkulačka jsou odesílány zpět na router, který je zase předá zpět klientovi Kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="c6f6b-110">Chcete-li použít tento vzorek</span><span class="sxs-lookup"><span data-stu-id="c6f6b-110">To use this sample</span></span>

1. <span data-ttu-id="c6f6b-111">Pomocí Visual Studia 2012 otevřete HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="c6f6b-112">Stiskněte klávesu F5 nebo CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="c6f6b-113">Pokud stisknete klávesu F5, klient kalkulačky se automaticky spustí.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="c6f6b-114">Pokud stisknete kombinaci kláves CTRL+SHIFT+B (sestavení), musíte začít sledovat aplikace sami.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="c6f6b-115">Klient kalkulačky (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="c6f6b-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="c6f6b-116">Kalkulačka služby (./CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="c6f6b-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="c6f6b-117">Služba směrování (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="c6f6b-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="c6f6b-118">Stisknutím klávesy ENTER spusťte klienta.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="c6f6b-119">Měl by se zobrazit následující výstup:</span><span class="sxs-lookup"><span data-stu-id="c6f6b-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="c6f6b-120">Konfigurovatelné pomocí kódu nebo App.Config</span><span class="sxs-lookup"><span data-stu-id="c6f6b-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="c6f6b-121">Ukázkové informace jsou konfigurované tak, aby k definování chování směrovače používaly soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="c6f6b-122">Můžete také změnit název souboru App.config na něco jiného tak, aby nebyl rozpoznán a odkomentovat volání metody ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="c6f6b-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="c6f6b-123">Obě metody má za následek stejné chování ze směrovače.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="c6f6b-124">Scénář</span><span class="sxs-lookup"><span data-stu-id="c6f6b-124">Scenario</span></span>
 <span data-ttu-id="c6f6b-125">Tato ukázka ukazuje směrovač, který funguje jako základní čerpadlo zpráv.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="c6f6b-126">Služba směrování funguje jako transparentní uzel proxy nakonfigurovaný tak, aby předával zprávy přímo předem nakonfigurované sadě cílových koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="c6f6b-127">Scénář reálného světa</span><span class="sxs-lookup"><span data-stu-id="c6f6b-127">Real World Scenario</span></span>
 <span data-ttu-id="c6f6b-128">Společnost Contoso chce zvýšit flexibilitu, kterou má při pojmenovávání, adresování, konfiguraci a zabezpečení svých služeb.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="c6f6b-129">Chcete-li to provést, umístí základní čerpadlo zpráv před své služby, aby působily jako veřejný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="c6f6b-130">To jim umožňuje umístit další zabezpečení před jejich skutečné služby a usnadnit implementaci škálovaných řešení nebo služby správy verzí později.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c6f6b-131">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="c6f6b-132">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="c6f6b-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c6f6b-134">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="c6f6b-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="c6f6b-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="c6f6b-135">See also</span></span>

- <span data-ttu-id="c6f6b-136">[Ukázky hostování a perzistence appfabric](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c6f6b-136">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
