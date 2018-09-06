---
title: Pokročilé zpracování chyb
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 72fb9885408759f5781501b548f81625d258d13c
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43873913"
---
# <a name="advanced-error-handling"></a><span data-ttu-id="e7560-102">Pokročilé zpracování chyb</span><span class="sxs-lookup"><span data-stu-id="e7560-102">Advanced Error Handling</span></span>
<span data-ttu-id="e7560-103">V této ukázce směrovací službou Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="e7560-103">This sample demonstrates the Windows Communication Foundation (WCF) routing service.</span></span> <span data-ttu-id="e7560-104">Směrovací služba je komponenta WCF, který umožňuje snadno do aplikace zahrnout směrovač založené na obsahu.</span><span class="sxs-lookup"><span data-stu-id="e7560-104">The routing service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="e7560-105">Tato ukázka předvádí, jak služba Směrování inteligentně obnoví z chyb, transakce a dalších složitější zasílání zpráv konceptů, jako jsou vícesměrové vysílání.</span><span class="sxs-lookup"><span data-stu-id="e7560-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e7560-106">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e7560-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e7560-107">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e7560-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e7560-108">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e7560-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e7560-109">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e7560-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="e7560-110">Ukázka podrobnosti</span><span class="sxs-lookup"><span data-stu-id="e7560-110">Sample Details</span></span>  
 <span data-ttu-id="e7560-111">V této ukázce směrovací služba je nakonfigurovaná pro čtení zprávu z fronty MSMQ a služby vícesměrového vysílání tuto zprávu do dvou seznamů, front.</span><span class="sxs-lookup"><span data-stu-id="e7560-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="e7560-112">Jeden seznam se používá pro fronty služby a jiné se používá pro fronty protokolování.</span><span class="sxs-lookup"><span data-stu-id="e7560-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="e7560-113">Proto, že ve výchozím nastavení, MSMQ vazby, který služba Směrování nakonfigurované na použití podporuje použití transakcí, směrovací služba zajišťuje, že je zpráva transakční a alespoň jednu frontu v každém seznamu přijatých před odesílajících sestavy do vstupní fronty ( `InQ`), který byl úspěšně směrovat zprávy.</span><span class="sxs-lookup"><span data-stu-id="e7560-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="e7560-114">Proto v případě, kdy nejsou k dispozici obě služby front nebo obě z fronty protokolování, směrovací službou hlásí, že zprávu nejde směrovat, a vstupní fronty by provedlo určitou akci.</span><span class="sxs-lookup"><span data-stu-id="e7560-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="e7560-115">Tato akce se skládá z přesun zprávy do fronty nedoručených zpráv systému.</span><span class="sxs-lookup"><span data-stu-id="e7560-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="e7560-116">Pro fungování této ukázky</span><span class="sxs-lookup"><span data-stu-id="e7560-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="e7560-117">Nainstalujte službu MSMQ před spuštěním této ukázky.</span><span class="sxs-lookup"><span data-stu-id="e7560-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="e7560-118">Pokud služba MSMQ nainstalovaná není, vrátí se zprávou výjimky při spuštění ukázky.</span><span class="sxs-lookup"><span data-stu-id="e7560-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="e7560-119">Najdete pokyny k instalaci služby MSMQ v [instalace řízení front zpráv (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).</span><span class="sxs-lookup"><span data-stu-id="e7560-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="e7560-120">Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AdvancedErrorHandling.sln.</span><span class="sxs-lookup"><span data-stu-id="e7560-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="e7560-121">Stisknutím klávesy **F5** nebo **CTRL + SHIFT + B** v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e7560-121">Press **F5** or **CTRL+SHIFT+B** in Visual Studio.</span></span>  
  
    1.  <span data-ttu-id="e7560-122">Pokud vytvoříte aplikaci pomocí kombinace kláves CTRL + SHIFT + B, je nutné spustit aplikaci na. / RoutingService/bin/debug/RoutingService.exe.</span><span class="sxs-lookup"><span data-stu-id="e7560-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="e7560-123">V okně konzoly stiskněte klávesu ENTER pro spuštění klienta.</span><span class="sxs-lookup"><span data-stu-id="e7560-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="e7560-124">Klient odešle různé statistické údaje o front pro každý případ.</span><span class="sxs-lookup"><span data-stu-id="e7560-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="e7560-125">Následuje výstupu vráceného pro případ 1 (bez chyb).</span><span class="sxs-lookup"><span data-stu-id="e7560-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="e7560-126">Následuje výstupu vráceného pro případ 3 (primární služby a protokolování chyb fronty).</span><span class="sxs-lookup"><span data-stu-id="e7560-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="e7560-127">Následuje výstupu vráceného pro případ 4 (primární služba fronty a frontu selhání primárního a záložního protokolování).</span><span class="sxs-lookup"><span data-stu-id="e7560-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="e7560-128">Následuje výstupu vráceného pro případ 2 (Chyba fronty primární služby).</span><span class="sxs-lookup"><span data-stu-id="e7560-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="e7560-129">Konfigurovat pomocí kódu nebo souboru App.config</span><span class="sxs-lookup"><span data-stu-id="e7560-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="e7560-130">Ukázka lodí umožňují definovat chování ve směrovači použít soubor App.config.</span><span class="sxs-lookup"><span data-stu-id="e7560-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="e7560-131">Můžete také změnit název souboru RoutingService\App.config na jiný tak, aby nebyl rozpoznán a změňte hodnotu `configDriven` pole RoutingService\Program.cs k `false` použití konfigurace definované v kódu.</span><span class="sxs-lookup"><span data-stu-id="e7560-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="e7560-132">Některé z metod má za následek stejné chování směrovače.</span><span class="sxs-lookup"><span data-stu-id="e7560-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="e7560-133">Scénář</span><span class="sxs-lookup"><span data-stu-id="e7560-133">Scenario</span></span>  
 <span data-ttu-id="e7560-134">Tento příklad ukazuje, že služba směrování můžete zpracovat možnosti zasílání zpráv, jako je například transakce kontextu přijetí a, můžete využít tyto možnosti jako součást správné zpracování chybových scénářů.</span><span class="sxs-lookup"><span data-stu-id="e7560-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="e7560-135">Reálné scénáře</span><span class="sxs-lookup"><span data-stu-id="e7560-135">Real World Scenario</span></span>  
 <span data-ttu-id="e7560-136">Contoso chce využívat transakční obdrží prostřednictvím službě Směrování a ujistěte se, že všechny nezbytné služby dostávat informace i během chybové stavy.</span><span class="sxs-lookup"><span data-stu-id="e7560-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="e7560-137">Kromě toho co by rádi chyby zpracovávat správně a automaticky a selhání, aby oznámený v případě, že zpráva se doručit, i když se používá logiku zpracování chyb.</span><span class="sxs-lookup"><span data-stu-id="e7560-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="e7560-138">Pro tento účel konfigurace služby směrování služby převzít služby při selhání ke konkrétním koncovým bodům podle očekávání a směrovací služba zpracovává chybové situace, což zahrnuje vytváření, dokončení a vrácení zpět nebo přerušením transakce přijímání kontextů jako nezbytné.</span><span class="sxs-lookup"><span data-stu-id="e7560-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e7560-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="e7560-139">See Also</span></span>  
 [<span data-ttu-id="e7560-140">Hostování AppFabric a ukázky trvalosti</span><span class="sxs-lookup"><span data-stu-id="e7560-140">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
