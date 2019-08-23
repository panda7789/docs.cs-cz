---
title: 'Postupy: Asynchronní volání operací služby WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 2d075bfebf7b5cbd2b2ce031a1c3855a925405a2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964031"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="6b721-102">Postupy: Asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="6b721-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="6b721-103">Toto téma popisuje, jak může klient přistupovat k operaci služby asynchronně.</span><span class="sxs-lookup"><span data-stu-id="6b721-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="6b721-104">Služba v tomto tématu implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6b721-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="6b721-105">Klient může volat operace v tomto rozhraní asynchronně pomocí asynchronního modelu volání založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="6b721-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="6b721-106">(Další informace o asynchronním volání modelu založeném na událostech naleznete v tématu [vícevláknové programování s asynchronním vzorem založeným](https://go.microsoft.com/fwlink/?LinkId=248184)na událostech).</span><span class="sxs-lookup"><span data-stu-id="6b721-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="6b721-107">Příklad, který ukazuje, jak provést asynchronní implementaci operace ve službě, naleznete v tématu [How to: Implementujte asynchronní operaci](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)služby.</span><span class="sxs-lookup"><span data-stu-id="6b721-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="6b721-108">Další informace o synchronních a asynchronních operacích naleznete v tématu [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6b721-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b721-109">Asynchronní volající model řízený událostmi není podporován při použití <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="6b721-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="6b721-110">Informace o tom <xref:System.ServiceModel.ChannelFactory%601>, jak provádět asynchronní volání pomocí, [naleznete v tématu How to: Asynchronní volání operací pomocí objektu pro vytváření](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)kanálů.</span><span class="sxs-lookup"><span data-stu-id="6b721-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="6b721-111">Postup</span><span class="sxs-lookup"><span data-stu-id="6b721-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="6b721-112">Asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="6b721-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="6b721-113">Spusťte nástroj Nástroj pro dodané [metadata (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) pomocí `/async` možností a `/tcv:Version35` příkazu společně, jak je znázorněno v následujícím příkazu.</span><span class="sxs-lookup"><span data-stu-id="6b721-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="6b721-114">Vygeneruje se kromě synchronních a standardních asynchronních operací založených na delegátech Třída klienta WCF, která obsahuje:</span><span class="sxs-lookup"><span data-stu-id="6b721-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="6b721-115">Dvě operace`operationName` <>propoužitís přístupemkasynchronnímuvolánízaloženémunaudálostech.`Async`</span><span class="sxs-lookup"><span data-stu-id="6b721-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="6b721-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6b721-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="6b721-117">Operace dokončila události <`operationName` > `Completed` formuláře pro použití s přístupem k asynchronnímu volání založenému na událostech.</span><span class="sxs-lookup"><span data-stu-id="6b721-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="6b721-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6b721-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="6b721-119"><xref:System.EventArgs?displayProperty=nameWithType>typy pro každou operaci (<`operationName`>`CompletedEventArgs`formuláře) pro použití s přístupem k asynchronnímu volání založenému na událostech.</span><span class="sxs-lookup"><span data-stu-id="6b721-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="6b721-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6b721-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="6b721-121">V volající aplikaci vytvořte metodu zpětného volání, která bude volána po dokončení asynchronní operace, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="6b721-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="6b721-122">Před <xref:System.EventHandler%601?displayProperty=nameWithType> voláním operace použijte nový obecný typ <`operationName` > `EventArgs` pro přidání metody obslužné rutiny (vytvořené v předchozím kroku) do události <`operationName`. > `Completed`</span><span class="sxs-lookup"><span data-stu-id="6b721-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="6b721-123">Pak zavolejte metodu <`operationName`. > `Async`</span><span class="sxs-lookup"><span data-stu-id="6b721-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="6b721-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6b721-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="6b721-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b721-125">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6b721-126">Pokyny pro návrh pro stav asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, jako `Result` vlastnost se vrátí jedna hodnota a ostatní jsou vráceny jako vlastnosti <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="6b721-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="6b721-127">Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu `Result` jako vlastnost a zbytek je <xref:System.EventArgs> vlastnosti objektu Pokud chcete jako `Result` vlastnost přijmout objekt zprávy a vracet hodnoty jako vlastnosti tohoto objektu, `/messageContract` použijte možnost Command.</span><span class="sxs-lookup"><span data-stu-id="6b721-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="6b721-128">Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="6b721-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="6b721-129">Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6b721-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="6b721-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b721-130">See also</span></span>

- [<span data-ttu-id="6b721-131">Postupy: Implementace asynchronní operace služby</span><span class="sxs-lookup"><span data-stu-id="6b721-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
