---
title: "Pokročilé zpracování chyb"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7771b9a4d5a6c0fb4349894afd348e9dece27fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-error-handling"></a><span data-ttu-id="624a2-102">Pokročilé zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="624a2-102">Advanced Error Handling</span></span>
<span data-ttu-id="624a2-103">Tento příklad ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směrování služby.</span><span class="sxs-lookup"><span data-stu-id="624a2-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="624a2-104">Služba směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komponenty, která usnadňuje do aplikace zahrnout směrovač podle obsahu.</span><span class="sxs-lookup"><span data-stu-id="624a2-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="624a2-105">Tento příklad ukazuje, jak službu Směrování inteligentně zotavení z chyb, s použitím transakce a jiné složitější zasílání zpráv koncepty, jako je například vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="624a2-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="624a2-106">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="624a2-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="624a2-107">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="624a2-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="624a2-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="624a2-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="624a2-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="624a2-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="624a2-110">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="624a2-110">Sample Details</span></span>  
 <span data-ttu-id="624a2-111">V této ukázce je nakonfigurovaná služba Směrování ke čtení zprávy ze služby MSMQ fronty a vícesměrové vysílání tuto zprávu na dva seznamy front.</span><span class="sxs-lookup"><span data-stu-id="624a2-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="624a2-112">Jeden seznam se používá pro fronty služby service a jiné pro protokolování fronty.</span><span class="sxs-lookup"><span data-stu-id="624a2-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="624a2-113">Protože ve výchozím nastavení, MSMQ vazby, který služba Směrování nakonfigurován na použití podporuje použití transakcí, vytvoří se, že je zpráva transakcí a přijaté podle alespoň jedna fronta v každém seznamu před zprávy (příchozí fronty směrovací službou `InQ`), byl úspěšně směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="624a2-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="624a2-114">Proto v případě, kde je k dispozici obě fronty služby service nebo obě fronty protokolování, službu Směrování sestav, že není možné směrovat zprávy a vstupní fronty by měl určitou akci.</span><span class="sxs-lookup"><span data-stu-id="624a2-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="624a2-115">Tato akce se skládá z přesunu zprávy do fronty nedoručených zpráv systému.</span><span class="sxs-lookup"><span data-stu-id="624a2-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="624a2-116">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="624a2-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="624a2-117">Nainstalujte službu MSMQ před spuštěním této ukázce.</span><span class="sxs-lookup"><span data-stu-id="624a2-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="624a2-118">Pokud služby MSMQ není nainstalovaná, vrátí se zprávou výjimky při spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="624a2-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="624a2-119">Pokyny k instalaci služby MSMQ lze najít na [instalaci řízení front zpráv (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span><span class="sxs-lookup"><span data-stu-id="624a2-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="624a2-120">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AdvancedErrorHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="624a2-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="624a2-121">Stiskněte klávesu **F5** nebo **CTRL + SHIFT + B** v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="624a2-121">Press **F5** or **CTRL+SHIFT+B** in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="624a2-122">Pokud vytvoříte aplikaci s CTRL + SHIFT + B, je nutné spustit aplikaci na. / RoutingService/bin/debug/RoutingService.exe.</span><span class="sxs-lookup"><span data-stu-id="624a2-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="624a2-123">V okně konzoly stiskněte klávesu ENTER pro spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="624a2-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="624a2-124">Klient se vrátí různé statistické údaje o fronty pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="624a2-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="624a2-125">Zde je výstup pro případ 1 (žádný počet selhání).</span><span class="sxs-lookup"><span data-stu-id="624a2-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="624a2-126">Zde je výstup pro případ 3 (primární služby a protokolování chyb fronty).</span><span class="sxs-lookup"><span data-stu-id="624a2-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="624a2-127">Zde je výstup pro případ 4 (primární služba fronty a fronty selhání primární a záložní protokolování).</span><span class="sxs-lookup"><span data-stu-id="624a2-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="624a2-128">Zde je výstup pro případ 2 (Chyba primární služba fronty).</span><span class="sxs-lookup"><span data-stu-id="624a2-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="624a2-129">Konfigurovat pomocí kódu nebo App.config</span><span class="sxs-lookup"><span data-stu-id="624a2-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="624a2-130">Ukázka lodě, umožňují použít soubor App.config k definování chování směrovače.</span><span class="sxs-lookup"><span data-stu-id="624a2-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="624a2-131">Můžete také změnit název souboru RoutingService\App.config na jinou tak, aby nebyla rozpoznána a změňte hodnotu `configDriven` pole RoutingService\Program.cs k `false` používat konfigurace definované v kódu.</span><span class="sxs-lookup"><span data-stu-id="624a2-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="624a2-132">Buď metoda výsledkem stejné chování z směrovači.</span><span class="sxs-lookup"><span data-stu-id="624a2-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="624a2-133">Scénář</span><span class="sxs-lookup"><span data-stu-id="624a2-133">Scenario</span></span>  
 <span data-ttu-id="624a2-134">Tento příklad znázorňuje, můžete službu Směrování zpracování rozšířené možnosti zasílání zpráv, jako je například transakce a přijímat kontextu a že ji můžete využít tyto možnosti jako součást správně zpracování chyby scénáře.</span><span class="sxs-lookup"><span data-stu-id="624a2-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="624a2-135">Scénář skutečných</span><span class="sxs-lookup"><span data-stu-id="624a2-135">Real World Scenario</span></span>  
 <span data-ttu-id="624a2-136">Contoso chce využívat transakční obdrží prostřednictvím směrování služby pro zajištění informace i během chybové stavy všechny nezbytné služby.</span><span class="sxs-lookup"><span data-stu-id="624a2-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="624a2-137">Kromě toho se mu správně a automaticky zpracovávat chyby a selhání, aby byly hlášené v případě, že zprávu nedoručitelných, i když využité zpracování logiky chyb.</span><span class="sxs-lookup"><span data-stu-id="624a2-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="624a2-138">Pro tento účel je potřeba nakonfigurovat službu směrování k převzetí služeb při selhání ke konkrétním koncovým bodům podle očekávání a služba Směrování zpracovává situacích chyby, který zahrnuje vytváření, dokončení a vrácení zpět nebo ruší se transakce a příjem kontextů jako nezbytné.</span><span class="sxs-lookup"><span data-stu-id="624a2-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="624a2-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="624a2-139">See Also</span></span>  
 [<span data-ttu-id="624a2-140">Ukázky trvalosti a hostování AppFabric</span><span class="sxs-lookup"><span data-stu-id="624a2-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
