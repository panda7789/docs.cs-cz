---
title: "Seskupování zpráv zařazených do fronty v relaci"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aba045456d61b5ad687f1030dca3c26b083cdb58
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="7a807-102">Seskupování zpráv zařazených do fronty v relaci</span><span class="sxs-lookup"><span data-stu-id="7a807-102">Grouping Queued Messages in a Session</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7a807-103">poskytuje relaci, která umožňuje seskupení sady souvisejících zpráv společně pro zpracování jedné přijímající aplikací.</span><span class="sxs-lookup"><span data-stu-id="7a807-103"> provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="7a807-104">Zprávy, které jsou součástí relace musí být součástí stejné transakci.</span><span class="sxs-lookup"><span data-stu-id="7a807-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="7a807-105">Vzhledem k tomu, že všechny zprávy jsou součástí stejné transakci, pokud se nepodaří jednu zprávu zpracovat celé relace je vrácena zpět.</span><span class="sxs-lookup"><span data-stu-id="7a807-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="7a807-106">Relace mají podobné chování s ohledem na fronty nedoručených zpráv a poškozených fronty.</span><span class="sxs-lookup"><span data-stu-id="7a807-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="7a807-107">Čas potřebný k Live (TTL) vlastnost nastavte u vazbu zařazených do fronty, nakonfigurované pro relace je použita v relaci jako celek.</span><span class="sxs-lookup"><span data-stu-id="7a807-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="7a807-108">Pokud jen některé zprávy v relaci se odesílají než hodnota TTL nevyprší, celé relace je umístěna do fronty nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="7a807-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="7a807-109">Podobně když zprávy v relaci se nepodařilo odeslat do aplikace z fronty aplikace, celé relace je umístěny v poškozených frontu (Pokud je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="7a807-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="7a807-110">Příklad seskupení zpráv</span><span class="sxs-lookup"><span data-stu-id="7a807-110">Message Grouping Example</span></span>  
 <span data-ttu-id="7a807-111">Jedním z příkladů kde seskupování zpráv je užitečné, je při implementaci pořadí zpracování aplikace jako [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.</span><span class="sxs-lookup"><span data-stu-id="7a807-111">One example where grouping messages is helpful is when implementing an order-processing application as a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service.</span></span> <span data-ttu-id="7a807-112">Například klient odešle pořadí do této aplikace, který obsahuje počet položek.</span><span class="sxs-lookup"><span data-stu-id="7a807-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="7a807-113">Pro každou položku klient zavolá službu, což vede k samostatné zprávy při odesílání.</span><span class="sxs-lookup"><span data-stu-id="7a807-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="7a807-114">Je možné, používat A přijímat první položka a server B, aby přijímal druhou položku.</span><span class="sxs-lookup"><span data-stu-id="7a807-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="7a807-115">Pokaždé, když je položka přidána, má server zpracování daná položka k vyhledání příslušné pořadí a přidejte položku, což je velmi neefektivní.</span><span class="sxs-lookup"><span data-stu-id="7a807-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="7a807-116">Pořád se spustit do takové umožňuje zvýšit efektivitu s pouze jedním serverem zpracování všech požadavků, protože server musí sledovat všechny objednávky právě zpracovávána a určení, která patří novou položku.</span><span class="sxs-lookup"><span data-stu-id="7a807-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="7a807-117">Seskupování všechny požadavky pro jednoduché řazení výrazně zjednodušuje implementace takové aplikace.</span><span class="sxs-lookup"><span data-stu-id="7a807-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="7a807-118">Klientská aplikace odešle pro jednoduché řazení všechny položky v relaci, takže Jakmile služba zpracovává pořadí, zpracuje celý relace najednou.</span><span class="sxs-lookup"><span data-stu-id="7a807-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="7a807-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="7a807-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="7a807-120">Nastavit kontraktu služby pro použití relací</span><span class="sxs-lookup"><span data-stu-id="7a807-120">To set up a service contract to use sessions</span></span>  
  
1.  <span data-ttu-id="7a807-121">Definování kontraktu služby, který vyžaduje relaci.</span><span class="sxs-lookup"><span data-stu-id="7a807-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="7a807-122">To provést pomocí <xref:System.ServiceModel.OperationContractAttribute> atribut a seznam zadáním:</span><span class="sxs-lookup"><span data-stu-id="7a807-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  <span data-ttu-id="7a807-123">Označte operace v kontraktu jako jednosměrné, protože tyto metody nic nevrátí.</span><span class="sxs-lookup"><span data-stu-id="7a807-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="7a807-124">To lze provést pomocí <xref:System.ServiceModel.OperationContractAttribute> atribut a seznam zadáním:</span><span class="sxs-lookup"><span data-stu-id="7a807-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  <span data-ttu-id="7a807-125">Implementace kontraktu služby a zadejte `InstanceContextMode` z `PerSession`.</span><span class="sxs-lookup"><span data-stu-id="7a807-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="7a807-126">To vytvoří služba jenom jednou pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="7a807-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  <span data-ttu-id="7a807-127">Každé operace služby vyžaduje transakce.</span><span class="sxs-lookup"><span data-stu-id="7a807-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="7a807-128">Zadejte o <xref:System.ServiceModel.OperationBehaviorAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="7a807-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="7a807-129">Nastavte také operaci, která se dokončí transakci `TransactionAutoComplete` k `true`.</span><span class="sxs-lookup"><span data-stu-id="7a807-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  <span data-ttu-id="7a807-130">Nakonfigurujte koncový bod, který používá zadaný systému `NetMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="7a807-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6.  <span data-ttu-id="7a807-131">Vytvoření transakční fronty pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="7a807-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="7a807-132">Fronty můžete vytvořit také pomocí služby Řízení front zpráv (MSMQ) nebo konzoly MMC.</span><span class="sxs-lookup"><span data-stu-id="7a807-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="7a807-133">Pokud vytvoříte, transakční fronty.</span><span class="sxs-lookup"><span data-stu-id="7a807-133">If you do, create a transactional queue.</span></span>  
  
7.  <span data-ttu-id="7a807-134">Vytvořit hostitele služby pro službu pomocí <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7a807-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8.  <span data-ttu-id="7a807-135">Otevření hostitele služby chcete zpřístupnit službu.</span><span class="sxs-lookup"><span data-stu-id="7a807-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="7a807-136">Zavřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="7a807-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="7a807-137">Nastavení klienta</span><span class="sxs-lookup"><span data-stu-id="7a807-137">To set up a client</span></span>  
  
1.  <span data-ttu-id="7a807-138">Vytvoření oboru transakce k zápisu do transakční fronty.</span><span class="sxs-lookup"><span data-stu-id="7a807-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2.  <span data-ttu-id="7a807-139">Vytvořte [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="7a807-139">Create the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3.  <span data-ttu-id="7a807-140">Místní pořadí.</span><span class="sxs-lookup"><span data-stu-id="7a807-140">Place the order.</span></span>  
  
4.  <span data-ttu-id="7a807-141">Zavřít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienta.</span><span class="sxs-lookup"><span data-stu-id="7a807-141">Close the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7a807-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="7a807-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7a807-143">Popis</span><span class="sxs-lookup"><span data-stu-id="7a807-143">Description</span></span>  
 <span data-ttu-id="7a807-144">Následující příklad obsahuje kód pro `IProcessOrder` služby a pro klienta, který tato služba používá.</span><span class="sxs-lookup"><span data-stu-id="7a807-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="7a807-145">Ukazuje, jak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá relací zajistit chování seskupení zařazených do fronty.</span><span class="sxs-lookup"><span data-stu-id="7a807-145">It shows how [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="7a807-146">Kód pro službu</span><span class="sxs-lookup"><span data-stu-id="7a807-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a><span data-ttu-id="7a807-147">Kód pro klienta</span><span class="sxs-lookup"><span data-stu-id="7a807-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="7a807-148">Viz také</span><span class="sxs-lookup"><span data-stu-id="7a807-148">See Also</span></span>  
 [<span data-ttu-id="7a807-149">Relace a fronty</span><span class="sxs-lookup"><span data-stu-id="7a807-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [<span data-ttu-id="7a807-150">Přehled front</span><span class="sxs-lookup"><span data-stu-id="7a807-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
