---
title: "Postupy: Asynchronní volání operací služby WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 549510d4d2b2ae0ee031b1c5426e7e28ab902bcd
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="3471e-102">Postupy: Asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="3471e-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="3471e-103">Toto téma popisuje, jak mít klient přístup operace služby asynchronně.</span><span class="sxs-lookup"><span data-stu-id="3471e-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="3471e-104">Implementuje službu v tomto tématu `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3471e-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="3471e-105">Klienta můžete asynchronní volání operací na tomto rozhraní pomocí událostmi řízené asynchronní volání modelu.</span><span class="sxs-lookup"><span data-stu-id="3471e-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="3471e-106">(Další informace o na základě událostí asynchronní volání modelu najdete v tématu [vícevláknové programování s asynchronním vzorem na základě událostí](http://go.microsoft.com/fwlink/?LinkId=248184)).</span><span class="sxs-lookup"><span data-stu-id="3471e-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](http://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="3471e-107">Příklad, který ukazuje, jak implementovat asynchronní operace služby, naleznete v části [postupy: implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="3471e-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="3471e-108">Další informace o synchronní a asynchronní operace najdete v tématu [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="3471e-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3471e-109">Událostmi řízené asynchronní volání modelu není podporováno při použití <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="3471e-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="3471e-110">Informace o asynchronní volání pomocí <xref:System.ServiceModel.ChannelFactory%601>, najdete v části [postupy: volání operace asynchronně pomocí postupu kanálu](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="3471e-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="3471e-111">Postup</span><span class="sxs-lookup"><span data-stu-id="3471e-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="3471e-112">Chcete-li asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="3471e-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="3471e-113">Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj s oběma `/async` a `/tcv:Version35` společně příkaz Možnosti, jak je znázorněno v následujícím příkazu.</span><span class="sxs-lookup"><span data-stu-id="3471e-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="3471e-114">Tím se vygeneruje, kromě synchronní a standard na základě delegáta asynchronních operací, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třída klienta, který obsahuje:</span><span class="sxs-lookup"><span data-stu-id="3471e-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client class that contains:</span></span>  
  
    -   <span data-ttu-id="3471e-115">Dva <`operationName` > `Async` operací pro použití s na základě událostí asynchronní volání přístup.</span><span class="sxs-lookup"><span data-stu-id="3471e-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="3471e-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3471e-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   <span data-ttu-id="3471e-117">Operace byla dokončena události ve formátu <`operationName` > `Completed` pro použití s na základě událostí asynchronní volání přístup.</span><span class="sxs-lookup"><span data-stu-id="3471e-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="3471e-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3471e-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <span data-ttu-id="3471e-119"><xref:System.EventArgs?displayProperty=nameWithType>typy pro každou operaci (ve formátu <`operationName`>`CompletedEventArgs`) pro použití s na základě událostí asynchronní volání přístup.</span><span class="sxs-lookup"><span data-stu-id="3471e-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="3471e-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3471e-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  <span data-ttu-id="3471e-121">Ve volání aplikace vytvořte metody zpětného volání, která se má volat při asynchronní operace se dokončila, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="3471e-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  <span data-ttu-id="3471e-122">Před voláním operace, použijte nové obecného <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName` > `EventArgs` přidat metodu obslužné rutiny (vytvořený v předchozím kroku) do <`operationName` > `Completed` událostí.</span><span class="sxs-lookup"><span data-stu-id="3471e-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="3471e-123">Potom zavolejte <`operationName` > `Async` metoda.</span><span class="sxs-lookup"><span data-stu-id="3471e-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="3471e-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="3471e-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="3471e-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="3471e-125">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3471e-126">Podle pokynů návrhu pro asynchronní model na základě událostí stavu, že pokud je vrácen více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnost a jiné jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="3471e-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="3471e-127">Jeden výsledek tohoto objektu je, že pokud klient naimportuje metadata pomocí možností na základě událostí asynchronní příkaz a operaci vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu. Pokud chcete dostávat zprávy objektu jako `Result` vlastnost a mít vrácené hodnoty jako vlastnosti tohoto objektu, použijte `/messageContract` příkaz možnost.</span><span class="sxs-lookup"><span data-stu-id="3471e-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="3471e-128">Tím se vygeneruje podpisu, který vrátí zprávu odpovědi jako `Result` vlastnost <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="3471e-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="3471e-129">Všechny interní návratové hodnoty jsou pak vlastnosti objektu zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="3471e-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="3471e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="3471e-130">See Also</span></span>  
 [<span data-ttu-id="3471e-131">Postupy: implementace operace asynchronní služby</span><span class="sxs-lookup"><span data-stu-id="3471e-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
