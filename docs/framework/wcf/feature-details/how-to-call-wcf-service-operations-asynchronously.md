---
title: 'Postupy: Asynchronní volání operací služby WCF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 90e00e4264ff808151c9e1c58fdaf290765620c8
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44511195"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="2647f-102">Postupy: Asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="2647f-102">How to: Call WCF Service Operations Asynchronously</span></span>
<span data-ttu-id="2647f-103">Toto téma popisuje, jak má přístup klient služby operace asynchronně.</span><span class="sxs-lookup"><span data-stu-id="2647f-103">This topic covers how a client can access a service operation asynchronously.</span></span> <span data-ttu-id="2647f-104">Implementuje služby v tomto tématu `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2647f-104">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="2647f-105">Klient může asynchronní volání operací na tomto rozhraní za použití založený na událostech asynchronní volání modelu.</span><span class="sxs-lookup"><span data-stu-id="2647f-105">The client can call the operations on this interface asynchronously by using the event-driven asynchronous calling model.</span></span> <span data-ttu-id="2647f-106">(Další informace o založený na událostech asynchronní volání modelu najdete v tématu [vícevláknové programování s asynchronní vzor založený na událostech](https://go.microsoft.com/fwlink/?LinkId=248184)).</span><span class="sxs-lookup"><span data-stu-id="2647f-106">(For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](https://go.microsoft.com/fwlink/?LinkId=248184)).</span></span> <span data-ttu-id="2647f-107">Příklad, který ukazuje, jak implementace operace asynchronní služby, najdete v části [postupy: implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="2647f-107">For an example that shows how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="2647f-108">Další informace o synchronní a asynchronní operace, najdete v části [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2647f-108">For more information about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2647f-109">Založený na událostech asynchronní volání modelu není podporováno při použití <xref:System.ServiceModel.ChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="2647f-109">The event-driven asynchronous calling model is not supported when using a <xref:System.ServiceModel.ChannelFactory%601>.</span></span> <span data-ttu-id="2647f-110">Informace o tom, že byla zahájena asynchronní volání pomocí <xref:System.ServiceModel.ChannelFactory%601>, naleznete v tématu [postupy: volání operace asynchronně pomocí objektu pro vytváření kanálů](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span><span class="sxs-lookup"><span data-stu-id="2647f-110">For information about making asynchronous calls using the <xref:System.ServiceModel.ChannelFactory%601>, see [How to: Call Operations Asynchronously Using a Channel Factory](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="2647f-111">Postup</span><span class="sxs-lookup"><span data-stu-id="2647f-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="2647f-112">Pro asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="2647f-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="2647f-113">Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj s oběma `/async` a `/tcv:Version35` možnosti příkazu společně, jak je znázorněno v následujícím příkazu.</span><span class="sxs-lookup"><span data-stu-id="2647f-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with both the `/async` and the `/tcv:Version35` command options together as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     <span data-ttu-id="2647f-114">Tím se vygeneruje, kromě synchronní a standardní delegáta asynchronních operací, třída klienta WCF, která obsahuje:</span><span class="sxs-lookup"><span data-stu-id="2647f-114">This generates, in addition to the synchronous and standard delegate-based asynchronous operations, a WCF client class that contains:</span></span>  
  
    -   <span data-ttu-id="2647f-115">Dva <`operationName` > `Async` operace pro použití s založený na událostech asynchronní volání přístup.</span><span class="sxs-lookup"><span data-stu-id="2647f-115">Two <`operationName`>`Async` operations for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="2647f-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2647f-116">For example:</span></span>  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   <span data-ttu-id="2647f-117">Operace se dokončila událostí ve formátu <`operationName` > `Completed` pro použití s založený na událostech asynchronní volání přístup.</span><span class="sxs-lookup"><span data-stu-id="2647f-117">Operation completed events of the form <`operationName`>`Completed` for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="2647f-118">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2647f-118">For example:</span></span>  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <span data-ttu-id="2647f-119"><xref:System.EventArgs?displayProperty=nameWithType> typy pro každou operaci (ve formátu <`operationName`>`CompletedEventArgs`) pro použití s založený na událostech asynchronní volání přístup.</span><span class="sxs-lookup"><span data-stu-id="2647f-119"><xref:System.EventArgs?displayProperty=nameWithType> types for each operation (of the form <`operationName`>`CompletedEventArgs`) for use with the event-based asynchronous calling approach.</span></span> <span data-ttu-id="2647f-120">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2647f-120">For example:</span></span>  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  <span data-ttu-id="2647f-121">Ve volání aplikace vytvořte metody zpětného volání se volá, když asynchronní operace nebude dokončena, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="2647f-121">In the calling application, create a callback method to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  <span data-ttu-id="2647f-122">Před voláním operace, používají nový obecný <xref:System.EventHandler%601?displayProperty=nameWithType> typu <`operationName` > `EventArgs` přidáte do metodu obslužné rutiny (vytvořený v předchozím kroku) <`operationName` > `Completed` událostí.</span><span class="sxs-lookup"><span data-stu-id="2647f-122">Prior to calling the operation, use a new generic <xref:System.EventHandler%601?displayProperty=nameWithType> of type <`operationName`>`EventArgs` to add the handler method (created in the preceding step) to the <`operationName`>`Completed` event.</span></span> <span data-ttu-id="2647f-123">Zavolejte <`operationName` > `Async` metody.</span><span class="sxs-lookup"><span data-stu-id="2647f-123">Then call the <`operationName`>`Async` method.</span></span> <span data-ttu-id="2647f-124">Příklad:</span><span class="sxs-lookup"><span data-stu-id="2647f-124">For example:</span></span>  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="2647f-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2647f-125">Example</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2647f-126">Pokyny návrhu pro asynchronní model založený na událostech stát, že pokud se vrátí více než jednu hodnotu, se vrátí jednu hodnotu jako `Result` vlastnosti a ostatní jsou vrácena jako vlastnosti na <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="2647f-126">The design guidelines for the event-based asynchronous model state that if more than one value is returned, one value is returned as the `Result` property and the others are returned as properties on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="2647f-127">Jeden výsledek tohoto je, že pokud klient naimportuje metadata pomocí možnosti založené na událostech asynchronního příkazu a operace vrátí více než jednu hodnotu, výchozí <xref:System.EventArgs> objekt vrátí jednu hodnotu jako `Result` vlastnost a zbývající jsou vlastnosti <xref:System.EventArgs> objektu. Pokud chcete přijímat zprávy objektu jako `Result` vlastnost a vrácené hodnoty jako vlastnosti objektu, použijte `/messageContract` možnost příkazu.</span><span class="sxs-lookup"><span data-stu-id="2647f-127">One result of this is that if a client imports metadata using the event-based asynchronous command options and the operation returns more than one value, the default <xref:System.EventArgs> object returns one value as the `Result` property and the remainder are properties of the <xref:System.EventArgs> object.If you want to receive the message object as the `Result` property and have the returned values as properties on that object, use the `/messageContract` command option.</span></span> <span data-ttu-id="2647f-128">Tím se vygeneruje podpis, který vrací zprávy s odpovědí jako `Result` vlastnost <xref:System.EventArgs> objektu.</span><span class="sxs-lookup"><span data-stu-id="2647f-128">This generates a signature that returns the response message as the `Result` property on the <xref:System.EventArgs> object.</span></span> <span data-ttu-id="2647f-129">Všechny interní vrácené hodnoty jsou pak vlastnosti objektu zprávu odpovědi.</span><span class="sxs-lookup"><span data-stu-id="2647f-129">All internal return values are then properties of the response message object.</span></span>  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a><span data-ttu-id="2647f-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2647f-130">See Also</span></span>  
 [<span data-ttu-id="2647f-131">Postupy: Implementace operace asynchronní služby</span><span class="sxs-lookup"><span data-stu-id="2647f-131">How to: Implement an Asynchronous Service Operation</span></span>](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
