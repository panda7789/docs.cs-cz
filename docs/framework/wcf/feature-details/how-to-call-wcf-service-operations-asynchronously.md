---
title: 'Postupy: Asynchronní volání operací služby WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 400ed8e5ee8b236e9d0f843f27b7c2112ec28861
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601254"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="20ff0-102">Postupy: Asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="20ff0-102">How to: Call WCF Service Operations Asynchronously</span></span>

<span data-ttu-id="20ff0-103">Tento článek popisuje, jak může klient přistupovat k operaci služby asynchronně.</span><span class="sxs-lookup"><span data-stu-id="20ff0-103">This article covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="20ff0-104">Služba v tomto článku implementuje `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="20ff0-104">The service in this article implements the `ICalculator` interface.</span></span> <span data-ttu-id="20ff0-105">Klient může volat operace v tomto rozhraní asynchronně pomocí asynchronního modelu volání založeného na událostech.</span><span class="sxs-lookup"><span data-stu-id="20ff0-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="20ff0-106">(Další informace o asynchronním volání modelu založeném na událostech naleznete v tématu [vícevláknové programování s asynchronním vzorem založeným na událostech](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span><span class="sxs-lookup"><span data-stu-id="20ff0-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)).</span></span> <span data-ttu-id="20ff0-107">Příklad, který ukazuje, jak implementovat asynchronní operace ve službě, naleznete v tématu [How to: Implementing a Asynchronous Service](../how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="20ff0-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="20ff0-108">Další informace o synchronních a asynchronních operacích naleznete v tématu [synchronní a asynchronní operace](../synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="20ff0-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20ff0-109">Asynchronní volající model řízený událostmi není podporován při použití <xref:System.ServiceModel.ChannelFactory%601> .</span><span class="sxs-lookup"><span data-stu-id="20ff0-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="20ff0-110">Informace o tom, jak provádět asynchronní volání pomocí <xref:System.ServiceModel.ChannelFactory%601> , naleznete v tématu [How to: asynchronní volání operací pomocí objektu pro vytváření kanálů](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="20ff0-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="20ff0-111">Postup</span><span class="sxs-lookup"><span data-stu-id="20ff0-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="20ff0-112">Asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="20ff0-112">To call WCF service operations asynchronously</span></span>  
  
1. <span data-ttu-id="20ff0-113">Spusťte nástroj Nástroj pro dodané [metadata (Svcutil. exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) pomocí `/async` `/tcv:Version35` možností a příkazu společně, jak je znázorněno v následujícím příkazu.</span><span class="sxs-lookup"><span data-stu-id="20ff0-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="20ff0-114">Vygeneruje se kromě synchronních a standardních asynchronních operací založených na delegátech Třída klienta WCF, která obsahuje:</span><span class="sxs-lookup"><span data-stu-id="20ff0-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    - <span data-ttu-id="20ff0-115">Dvě `operationName` > `Async` operace <pro použití s přístupem k asynchronnímu volání založenému na událostech.</span><span class="sxs-lookup"><span data-stu-id="20ff0-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="20ff0-116">Například:</span><span class="sxs-lookup"><span data-stu-id="20ff0-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <span data-ttu-id="20ff0-117">Operace dokončila události <formuláře `operationName` > `Completed` pro použití s přístupem k asynchronnímu volání založenému na událostech.</span><span class="sxs-lookup"><span data-stu-id="20ff0-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="20ff0-118">Například:</span><span class="sxs-lookup"><span data-stu-id="20ff0-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <span data-ttu-id="20ff0-119"><xref:System.EventArgs?displayProperty=nameWithType>typy pro každou operaci (<formuláře `operationName` > `CompletedEventArgs` ) pro použití s přístupem k asynchronnímu volání založenému na událostech.</span><span class="sxs-lookup"><span data-stu-id="20ff0-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="20ff0-120">Například:</span><span class="sxs-lookup"><span data-stu-id="20ff0-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. <span data-ttu-id="20ff0-121">V volající aplikaci vytvořte metodu zpětného volání, která bude volána po dokončení asynchronní operace, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="20ff0-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. <span data-ttu-id="20ff0-122">Před voláním operace použijte nový obecný <xref:System.EventHandler%601?displayProperty=nameWithType> typ <`operationName` > `EventArgs` pro přidání metody obslužné rutiny (vytvořené v předchozím kroku) do `operationName` > `Completed` události <.</span><span class="sxs-lookup"><span data-stu-id="20ff0-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="20ff0-123">Pak zavolejte metodu <`operationName` > `Async` .</span><span class="sxs-lookup"><span data-stu-id="20ff0-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="20ff0-124">Například:</span><span class="sxs-lookup"><span data-stu-id="20ff0-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="20ff0-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="20ff0-125">Example</span></span>  
  
> [!NOTE]
> <span data-ttu-id="20ff0-126">Pokyny pro návrh pro stav asynchronního modelu založeného na událostech, pokud je vrácena více než jedna hodnota, jako vlastnost se vrátí jedna hodnota `Result` a ostatní jsou vráceny jako vlastnosti <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="20ff0-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="20ff0-127">Jedním z těchto výsledků je, že pokud klient Importuje metadata pomocí parametrů asynchronního příkazu založeného na událostech a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbytek je vlastnosti <xref:System.EventArgs> objektu. Pokud chcete jako vlastnost přijmout objekt zprávy `Result` a vracet hodnoty jako vlastnosti tohoto objektu, použijte `/messageContract` možnost Command.</span><span class="sxs-lookup"><span data-stu-id="20ff0-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="20ff0-128">Tím se vygeneruje podpis, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="20ff0-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="20ff0-129">Všechny interní návratové hodnoty jsou potom vlastnostmi objektu zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="20ff0-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="20ff0-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="20ff0-130">See also</span></span>

- [<span data-ttu-id="20ff0-131">Postupy: Implementace operace asynchronní služby</span><span class="sxs-lookup"><span data-stu-id="20ff0-131">How to: Implement an Asynchronous Service Operation</span></span>](../how-to-implement-an-asynchronous-service-operation.md)
