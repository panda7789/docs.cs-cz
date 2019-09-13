---
title: Seskupování zpráv zařazených do fronty v relaci
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 995697e618ff5d56a719efc5d69b97583733d980
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2019
ms.locfileid: "70892735"
---
# <a name="grouping-queued-messages-in-a-session"></a><span data-ttu-id="7fa7a-102">Seskupování zpráv zařazených do fronty v relaci</span><span class="sxs-lookup"><span data-stu-id="7fa7a-102">Grouping Queued Messages in a Session</span></span>
<span data-ttu-id="7fa7a-103">Windows Communication Foundation (WCF) poskytuje relaci, která umožňuje seskupit sadu souvisejících zpráv pro zpracování v rámci jedné přijímající aplikace.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-103">Windows Communication Foundation (WCF) provides a session that allows you to group a set of related messages together for processing by a single receiving application.</span></span> <span data-ttu-id="7fa7a-104">Zprávy, které jsou součástí relace, musí být součástí stejné transakce.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-104">Messages that are part of a session must be part of the same transaction.</span></span> <span data-ttu-id="7fa7a-105">Vzhledem k tomu, že všechny zprávy jsou součástí stejné transakce, v případě, že se jedna zpráva nedokáže zpracovat, vrátí se celá relace zpátky.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-105">Because all messages are part of the same transaction, if one message fails to be processed the entire session is rolled back.</span></span> <span data-ttu-id="7fa7a-106">Relace mají podobné chování s ohledem na fronty nedoručených zpráv a poškozené fronty.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-106">Sessions have similar behaviors with regard to dead-letter queues and poison queues.</span></span> <span data-ttu-id="7fa7a-107">Vlastnost Time to Live (TTL) nastavená u vazby ve frontě konfigurovaná pro relace je použita pro relaci jako celek.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-107">The Time to Live (TTL) property set on a queued binding configured for sessions is applied to the session as a whole.</span></span> <span data-ttu-id="7fa7a-108">Pokud se do vypršení hodnoty TTL odešlou jenom některé zprávy v relaci, bude celá relace umístěná ve frontě nedoručených zpráv.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-108">If only some of the messages in the session are sent before the TTL expires, the entire session is placed in the dead-letter queue.</span></span> <span data-ttu-id="7fa7a-109">Podobně platí, že když se zprávy v relaci neodesílají do aplikace z fronty aplikace, celá relace se umístí do fronty poškození (Pokud je dostupná).</span><span class="sxs-lookup"><span data-stu-id="7fa7a-109">Similarly, when messages in a session fail to be sent to an application from the application queue, the entire session is placed in the poison queue (if available).</span></span>  
  
## <a name="message-grouping-example"></a><span data-ttu-id="7fa7a-110">Příklad seskupování zpráv</span><span class="sxs-lookup"><span data-stu-id="7fa7a-110">Message Grouping Example</span></span>  
 <span data-ttu-id="7fa7a-111">Jeden příklad, kde je seskupování zpráv užitečné, je při implementaci aplikace pro zpracování objednávek jako služby WCF.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-111">One example where grouping messages is helpful is when implementing an order-processing application as a WCF service.</span></span> <span data-ttu-id="7fa7a-112">Například klient odešle objednávku do této aplikace, která obsahuje několik položek.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-112">For instance, a client submits an order to this application that contains a number of items.</span></span> <span data-ttu-id="7fa7a-113">Pro každou položku klient provede volání služby, což vede k odeslání samostatné zprávy.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-113">For each item, the client makes a call to the service, which results in a separate message being sent.</span></span> <span data-ttu-id="7fa7a-114">Je možné, aby mohl získat první položku a server B přijmout druhou položku.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-114">It is possible for serve A to receive the first item, and server B to receive the second item.</span></span> <span data-ttu-id="7fa7a-115">Pokaždé, když se přidá položka, Server zpracovává tuto položku, aby vyhledal příslušné pořadí a přidal do něj položku, která je vysoce neefektivní.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-115">Each time an item is added, the server processing that item has to find the appropriate order and add the item to it, which is highly inefficient.</span></span> <span data-ttu-id="7fa7a-116">Pořád se to netýká pouze jednoho serveru, který zpracovává všechny požadavky, protože server musí sledovat všechny aktuálně zpracovávané objednávky a určit, do které z nich patří nová položka.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-116">You still run into such inefficiencies with only a single server handling all requests, because the server must keep track of all orders currently being processed and determine which one the new item belongs to.</span></span> <span data-ttu-id="7fa7a-117">Seskupení všech požadavků pro jednu objednávku značně zjednodušuje implementaci takové aplikace.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-117">Grouping all requests for a single order greatly simplifies implementation of such an application.</span></span> <span data-ttu-id="7fa7a-118">Klientská aplikace pošle všechny položky v relaci jediným pořadím, takže když služba zpracuje objednávku, zpracuje celou relaci najednou.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-118">The client application sends all items for a single order in a session, so when the service processes the order, it processes the entire session at once.</span></span> \  
  
## <a name="procedures"></a><span data-ttu-id="7fa7a-119">Procedury</span><span class="sxs-lookup"><span data-stu-id="7fa7a-119">Procedures</span></span>  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a><span data-ttu-id="7fa7a-120">Nastavení kontraktu služby pro použití relací</span><span class="sxs-lookup"><span data-stu-id="7fa7a-120">To set up a service contract to use sessions</span></span>  
  
1. <span data-ttu-id="7fa7a-121">Definujte kontrakt služby, který vyžaduje relaci.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-121">Define a service contract that requires a session.</span></span> <span data-ttu-id="7fa7a-122">Provedete to <xref:System.ServiceModel.ServiceContractAttribute> pomocí atributu zadáním:</span><span class="sxs-lookup"><span data-stu-id="7fa7a-122">Do this with the <xref:System.ServiceModel.ServiceContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp
    SessionMode=SessionMode.Required  
    ```  
  
2. <span data-ttu-id="7fa7a-123">Označte operace v kontraktu jako jednosměrné, protože tyto metody nevrátí žádnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-123">Mark the operations in the contract as one-way, because these methods do not return anything.</span></span> <span data-ttu-id="7fa7a-124">To se provádí s <xref:System.ServiceModel.OperationContractAttribute> atributem zadáním:</span><span class="sxs-lookup"><span data-stu-id="7fa7a-124">This is done with the <xref:System.ServiceModel.OperationContractAttribute> attribute by specifying:</span></span>  
  
    ```csharp  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3. <span data-ttu-id="7fa7a-125">Implementujte kontrakt služby a zadejte <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode>. <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="7fa7a-125">Implement the service contract and specify an <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode> of <xref:System.ServiceModel.InstanceContextMode.PerSession?displayProperty=nameWithType>.</span></span> <span data-ttu-id="7fa7a-126">Tato služba vytvoří instanci služby pouze jednou pro každou relaci.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-126">This instantiates the service only once for each session.</span></span>  
  
    ```csharp  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4. <span data-ttu-id="7fa7a-127">Každá operace služby vyžaduje transakci.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-127">Each service operation requires a transaction.</span></span> <span data-ttu-id="7fa7a-128">Tuto <xref:System.ServiceModel.OperationBehaviorAttribute> vlastnost zadejte s atributem.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-128">Specify this with the <xref:System.ServiceModel.OperationBehaviorAttribute> attribute.</span></span> <span data-ttu-id="7fa7a-129">Operace, která dokončí transakci, by měla <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> být `true`také nastavena na.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-129">The operation that completes the transaction should also set <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionAutoComplete> to `true`.</span></span>  
  
    ```csharp  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5. <span data-ttu-id="7fa7a-130">Nakonfigurujte koncový bod, který používá vazbu poskytovanou `NetMsmqBinding` systémem.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-130">Configure an endpoint that uses the system-provided `NetMsmqBinding` binding.</span></span>  
  
6. <span data-ttu-id="7fa7a-131">Vytvořte transakční frontu pomocí <xref:System.Messaging>.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-131">Create a transactional queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="7fa7a-132">Frontu můžete vytvořit také pomocí služby Řízení front zpráv (MSMQ) nebo konzoly MMC.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-132">You can also create the queue by using Message Queuing (MSMQ) or MMC.</span></span> <span data-ttu-id="7fa7a-133">Pokud tak učiníte, vytvořte transakční frontu.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-133">If you do, create a transactional queue.</span></span>  
  
7. <span data-ttu-id="7fa7a-134">Vytvořte hostitele služby pro službu pomocí nástroje <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-134">Create a service host for the service by using <xref:System.ServiceModel.ServiceHost>.</span></span>  
  
8. <span data-ttu-id="7fa7a-135">Otevřete hostitele služby, aby služba byla dostupná.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-135">Open the service host to make the service available.</span></span>  
  
9. <span data-ttu-id="7fa7a-136">Zavřete hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-136">Close the service host.</span></span>  
  
#### <a name="to-set-up-a-client"></a><span data-ttu-id="7fa7a-137">Nastavení klienta</span><span class="sxs-lookup"><span data-stu-id="7fa7a-137">To set up a client</span></span>  
  
1. <span data-ttu-id="7fa7a-138">Vytvořte obor transakce pro zápis do transakční fronty.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-138">Create a transaction scope to write to the transactional queue.</span></span>  
  
2. <span data-ttu-id="7fa7a-139">Vytvořte klienta WCF pomocí nástroje [Svcutil. exe (Nástroj pro metadata ServiceModel)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) .</span><span class="sxs-lookup"><span data-stu-id="7fa7a-139">Create the WCF client using the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool.</span></span>  
  
3. <span data-ttu-id="7fa7a-140">Umístěte objednávku.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-140">Place the order.</span></span>  
  
4. <span data-ttu-id="7fa7a-141">Zavřete klienta WCF.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-141">Close the WCF client.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7fa7a-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="7fa7a-142">Example</span></span>  
  
### <a name="description"></a><span data-ttu-id="7fa7a-143">Popis</span><span class="sxs-lookup"><span data-stu-id="7fa7a-143">Description</span></span>  
 <span data-ttu-id="7fa7a-144">Následující příklad poskytuje kód pro `IProcessOrder` službu a pro klienta, který používá tuto službu.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-144">The following example provides the code for the `IProcessOrder` service and for a client that uses this service.</span></span> <span data-ttu-id="7fa7a-145">Ukazuje, jak WCF používá relace ve frontě k zajištění chování seskupení.</span><span class="sxs-lookup"><span data-stu-id="7fa7a-145">It shows how WCF uses queued sessions to provide the grouping behavior.</span></span>  
  
### <a name="code-for-the-service"></a><span data-ttu-id="7fa7a-146">Kód pro službu</span><span class="sxs-lookup"><span data-stu-id="7fa7a-146">Code for the Service</span></span>  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  

### <a name="code-for-the-client"></a><span data-ttu-id="7fa7a-147">Kód pro klienta</span><span class="sxs-lookup"><span data-stu-id="7fa7a-147">Code for the Client</span></span>  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  

## <a name="see-also"></a><span data-ttu-id="7fa7a-148">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7fa7a-148">See also</span></span>

- [<span data-ttu-id="7fa7a-149">Relace a fronty</span><span class="sxs-lookup"><span data-stu-id="7fa7a-149">Sessions and Queues</span></span>](../../../../docs/framework/wcf/samples/sessions-and-queues.md)
- [<span data-ttu-id="7fa7a-150">Přehled front</span><span class="sxs-lookup"><span data-stu-id="7fa7a-150">Queues Overview</span></span>](../../../../docs/framework/wcf/feature-details/queues-overview.md)
