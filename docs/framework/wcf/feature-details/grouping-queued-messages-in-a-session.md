---
title: Seskupování zpráv zařazených do fronty v relaci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 260e8b38f110ffc2c2fdc5e2768db8c95fb01860
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564120"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="a5dd5-102">Seskupování zpráv zařazených do fronty v relaci</span><span class="sxs-lookup"><span data-stu-id="a5dd5-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="a5dd5-103">Windows Communication Foundation (WCF) poskytuje relaci, která umožňuje seskupit sadu souvisejících zpráv pro zpracování jedné přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="a5dd5-104">Zprávy, které jsou součástí relace musí být součástí stejné transakce.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="a5dd5-105">Protože všechny zprávy jsou součástí stejné transakce, pokud se nepodaří zpracovat celou relaci jednu zprávu se vrátí zpět.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="a5dd5-106">Relace mají podobné chování s ohledem na fronty nedoručených zpráv a nezpracovatelných fronty.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="a5dd5-107">Time to Live (TTL) nastavenou na vazbu s frontou nakonfigurované pro relace se použijí pro relaci jako celek.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="a5dd5-108">Pokud jen některé zprávy v relaci odeslány předtím, než hodnota TTL nevyprší, je umístěn celou relaci ve frontě nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="a5dd5-109">Podobně když dojde k selhání zprávy v relaci k odeslání do aplikace z fronty aplikace, celá relace nachází ve nezpracovatelných frontu (Pokud je k dispozici).</span><span class="sxs-lookup"><span data-stu-id="a5dd5-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="a5dd5-110">Ukázková zpráva seskupení</span><span class="sxs-lookup"><span data-stu-id="a5dd5-110">Message Grouping Example</span></span>  
 <span data-ttu-id="a5dd5-111">Jedním z příkladů kde seskupování zpráv je užitečné, je při implementaci zpracování objednávky aplikace jako služba WCF.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="a5dd5-112">Například klient odešle objednávku k této aplikaci, která obsahuje celou řadu položek.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="a5dd5-113">Pro každou položku klient zavolá službu, která vede samostatné odeslání zprávy.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="a5dd5-114">Je možné, používat A na první položku a server B pro příjem druhé položky.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="a5dd5-115">Pokaždé, když se přidá položka zpracování této položky na serveru má vyhledat správné místo v pořadí a do něj přidat položku, což je velmi neefektivní.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="a5dd5-116">Stále dochází k takové nedostatečnou s pouze jedním serverem zpracování všech požadavků, protože server musí udržovat přehled o všech objednávek, které se právě zpracovává a určit, která z nich se nová položka patří.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="a5dd5-117">Seskupení všech požadavků na jednu objednávku výrazně zjednodušuje provádění takové aplikace.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="a5dd5-118">Klientská aplikace odešle všechny položky na jednu objednávku v relaci, takže když službu objednávku zpracovává, zpracuje najednou celou relaci.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="a5dd5-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="a5dd5-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="a5dd5-120">K nastavení kontraktu služby pro použití relací</span><span class="sxs-lookup"><span data-stu-id="a5dd5-120">To set up a service contract to use sessions</span></span>  
  
1.  <span data-ttu-id="a5dd5-121">Definování kontraktu služby vyžadující relace.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="a5dd5-122">K tomu <xref:System.ServiceModel.OperationContractAttribute> atribut a zadáním:</span><span class="sxs-lookup"><span data-stu-id="a5dd5-122">Do this with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  <span data-ttu-id="a5dd5-123">Označte operace v kontraktu jako jednosměrná, protože tyto metody nic nevrátí.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="a5dd5-124">Používá se k tomu <xref:System.ServiceModel.OperationContractAttribute> atribut a zadáním:</span><span class="sxs-lookup"><span data-stu-id="a5dd5-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute and by specifying:</span></span>  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  <span data-ttu-id="a5dd5-125">Implementace kontraktu služby a zadejte `InstanceContextMode` z `PerSession`.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-125">Implement the service contract and specify an `InstanceContextMode` of `PerSession`.</span></span> <span data-ttu-id="a5dd5-126">To vytvoří instanci služby pouze jednou pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-126">This instantiates the service only once for each session.</span></span>  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  <span data-ttu-id="a5dd5-127">Každá služba operace vyžaduje transakci.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="a5dd5-128">S tuto verzi uveďte <xref:System.ServiceModel.OperationBehaviorAttribute> atribut.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="a5dd5-129">Tato operace provede transakce nastavte také `TransactionAutoComplete` k `true`.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-129">The operation that completes the transaction should also set `TransactionAutoComplete` to `true`.</span></span>  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  <span data-ttu-id="a5dd5-130">Konfigurace koncového bodu, který používá poskytovaných systémem `NetMsmqBinding` vazby.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6.  <span data-ttu-id="a5dd5-131">Vytvoření transakční fronty pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="a5dd5-132">Fronty můžete vytvořit také pomocí služby Řízení front zpráv (MSMQ) nebo konzoly MMC.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="a5dd5-133">Pokud tak učiníte, vytvoření transakční fronty.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-133">If you do, create a transactional queue.</span></span>  
  
7.  <span data-ttu-id="a5dd5-134">Vytvoření hostitele služby pro službu pomocí <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8.  <span data-ttu-id="a5dd5-135">Otevření hostitele služby, aby tato služba k dispozici.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="a5dd5-136">Zavřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="a5dd5-137">Nastavení klienta</span><span class="sxs-lookup"><span data-stu-id="a5dd5-137">To set up a client</span></span>  
  
1.  <span data-ttu-id="a5dd5-138">Vytvoření oboru transakce k zápisu transakční fronty.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2.  <span data-ttu-id="a5dd5-139">Vytvoření pomocí klienta WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3.  <span data-ttu-id="a5dd5-140">Objednávku.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-140">Place the order.</span></span>  
  
4.  <span data-ttu-id="a5dd5-141">Zavřete klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a5dd5-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5dd5-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="a5dd5-143">Popis</span><span class="sxs-lookup"><span data-stu-id="a5dd5-143">Description</span></span>  
 <span data-ttu-id="a5dd5-144">Následující příklad uvádí kód `IProcessOrder` služby a pro klienta, která využívá tuto službu.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="a5dd5-145">To ukazuje, jak WCF používá relace ve frontě poskytnout chování seskupení.</span><span class="sxs-lookup"><span data-stu-id="a5dd5-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="a5dd5-146">Kód služby</span><span class="sxs-lookup"><span data-stu-id="a5dd5-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a><span data-ttu-id="a5dd5-147">Kód pro klienta</span><span class="sxs-lookup"><span data-stu-id="a5dd5-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a><span data-ttu-id="a5dd5-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a5dd5-148">See also</span></span>
- [<span data-ttu-id="a5dd5-149">Relace a fronty</span><span class="sxs-lookup"><span data-stu-id="a5dd5-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="a5dd5-150">Přehled front</span><span class="sxs-lookup"><span data-stu-id="a5dd5-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
