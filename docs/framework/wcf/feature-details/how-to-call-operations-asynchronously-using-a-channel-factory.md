---
title: "Postupy: volání operací asynchronně pomocí postupu kanálu"
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
ms.assetid: cc17dd47-b9ad-451c-a362-e36e0aac7ba0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8e0ef2dbd52e6628e7b784c50d2ce29306216772
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-call-operations-asynchronously-using-a-channel-factory"></a><span data-ttu-id="d5479-102">Postupy: volání operací asynchronně pomocí postupu kanálu</span><span class="sxs-lookup"><span data-stu-id="d5479-102">How to: Call Operations Asynchronously Using a Channel Factory</span></span>
<span data-ttu-id="d5479-103">Toto téma popisuje, jak mít klient přístup operace služby asynchronně při použití <xref:System.ServiceModel.ChannelFactory%601>– na základě klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="d5479-103">This topic covers how a client can access a service operation asynchronously when using a <xref:System.ServiceModel.ChannelFactory%601>-based client application.</span></span> <span data-ttu-id="d5479-104">(Při použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> objekt k vyvolání služby můžete použít událostmi řízené asynchronní volání modelu.</span><span class="sxs-lookup"><span data-stu-id="d5479-104">(When using a <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> object to invoke a service you can use the event-driven asynchronous calling model.</span></span> <span data-ttu-id="d5479-105">Další informace najdete v tématu [postupy: asynchronní volání operací služby](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="d5479-105">For more information, see [How to: Call Service Operations Asynchronously](../../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="d5479-106">Další informace o na základě událostí asynchronní volání modelu najdete v tématu [vícevláknové programování s asynchronním vzorem na základě událostí](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span><span class="sxs-lookup"><span data-stu-id="d5479-106">For more information about the event-based asynchronous calling model, see [Multithreaded Programming with the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md).)</span></span>  
  
 <span data-ttu-id="d5479-107">Implementuje službu v tomto tématu `ICalculator` rozhraní.</span><span class="sxs-lookup"><span data-stu-id="d5479-107">The service in this topic implements the `ICalculator` interface.</span></span> <span data-ttu-id="d5479-108">Klient může asynchronní volání operací na tomto rozhraní, což znamená, že operace jako `Add` jsou rozdělit na dvě metody, `BeginAdd` a `EndAdd`, dřívějším, které zahájí volání a druhé z nich načte výsledek Po dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="d5479-108">The client can call the operations on this interface asynchronously, which means that operations like `Add` are split into two methods, `BeginAdd` and `EndAdd`, the former of which initiates the call and the latter of which retrieves the result when the operation completes.</span></span> <span data-ttu-id="d5479-109">Příklad způsobu implementace operace asynchronní ve službě, naleznete v části [postupy: implementace operace asynchronní služby](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span><span class="sxs-lookup"><span data-stu-id="d5479-109">For an example showing how to implement an operation asynchronously in a service, see [How to: Implement an Asynchronous Service Operation](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md).</span></span> <span data-ttu-id="d5479-110">Podrobnosti o synchronní a asynchronní operace najdete v tématu [synchronní a asynchronní operace](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="d5479-110">For details about synchronous and asynchronous operations, see [Synchronous and Asynchronous Operations](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span>  
  
## <a name="procedure"></a><span data-ttu-id="d5479-111">Postup</span><span class="sxs-lookup"><span data-stu-id="d5479-111">Procedure</span></span>  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a><span data-ttu-id="d5479-112">Chcete-li asynchronní volání operací služby WCF</span><span class="sxs-lookup"><span data-stu-id="d5479-112">To call WCF service operations asynchronously</span></span>  
  
1.  <span data-ttu-id="d5479-113">Spustit [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj s `/async` možnost, jak je znázorněno v následujícím příkazu.</span><span class="sxs-lookup"><span data-stu-id="d5479-113">Run the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) tool with the `/async` option as shown in the following command.</span></span>  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a  
    ```  
  
     <span data-ttu-id="d5479-114">Tím se vygeneruje na klienta asynchronní verzi kontrakt služby pro danou operaci.</span><span class="sxs-lookup"><span data-stu-id="d5479-114">This generates an asynchronous client version of the service contract for the operation.</span></span>  
  
2.  <span data-ttu-id="d5479-115">Vytvoření funkce zpětného volání, která se má volat při asynchronní operace se dokončila, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="d5479-115">Create a callback function to be called when the asynchronous operation is complete, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#2)]
     [!code-vb[C_How_To_CF_Async#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#2)]  
  
3.  <span data-ttu-id="d5479-116">Pro přístup k operaci služby asynchronně, vytvoření klienta a volání `Begin[Operation]` (například `BeginAdd`) a zadejte funkci zpětného volání, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="d5479-116">To access a service operation asynchronously, create the client and call the `Begin[Operation]` (for example, `BeginAdd`) and specify a callback function, as shown in the following sample code.</span></span>  
  
     [!code-csharp[C_How_To_CF_Async#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/client.cs#3)]
     [!code-vb[C_How_To_CF_Async#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/client.vb#3)]  
  
     <span data-ttu-id="d5479-117">Když funkce zpětného volání provede, klient volá `End<operation>` (například `EndAdd`) načíst výsledky.</span><span class="sxs-lookup"><span data-stu-id="d5479-117">When the callback function executes, the client calls `End<operation>` (for example, `EndAdd`) to retrieve the result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5479-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5479-118">Example</span></span>  
 <span data-ttu-id="d5479-119">Implementuje službu, která se používá s kód klienta, který se používá v předchozím postupu `ICalculator` rozhraní, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d5479-119">The service that is used with the client code that is used in the preceding procedure implements the `ICalculator` interface as shown in the following code.</span></span> <span data-ttu-id="d5479-120">Na straně služby `Add` a `Subtract` operace kontraktu jsou vyvolány synchronně pomocí [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] běh, i když předchozí kroky klienta se asynchronně vyvolá na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="d5479-120">On the service side, the `Add` and `Subtract` operations of the contract are invoked synchronously by the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] run time, even though the preceding client steps are invoked asynchronously on the client.</span></span> <span data-ttu-id="d5479-121">`Multiply` a `Divide` operací se používají k vyvolání službu asynchronně na straně služby, i když klient vyvolá je synchronně.</span><span class="sxs-lookup"><span data-stu-id="d5479-121">The `Multiply` and `Divide` operations are used to invoke the service asynchronously on the service side, even if the client invokes them synchronously.</span></span> <span data-ttu-id="d5479-122">Tento příklad nastaví <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="d5479-122">This example sets the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A> property to `true`.</span></span> <span data-ttu-id="d5479-123">Nastavení této vlastnosti v kombinaci s implementací [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronní vzor informuje běhu k vyvolání operace asynchronně.</span><span class="sxs-lookup"><span data-stu-id="d5479-123">This property setting, in combination with the implementation of the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] asynchronous pattern, tells the run time to invoke the operation asynchronously.</span></span>  
  
 [!code-csharp[C_How_To_CF_Async#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_how_to_cf_async/cs/service.cs#4)]
 [!code-vb[C_How_To_CF_Async#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_how_to_cf_async/vb/service.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d5479-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5479-124">See Also</span></span>  
 [<span data-ttu-id="d5479-125">Kontrakt služby: Ukázka asynchronního</span><span class="sxs-lookup"><span data-stu-id="d5479-125">Service Contract: Asynchronous Sample</span></span>](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7)
