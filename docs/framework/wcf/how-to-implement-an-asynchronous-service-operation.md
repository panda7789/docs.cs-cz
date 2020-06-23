---
title: 'Postupy: Implementace operace asynchronní služby'
description: Přečtěte si o struktuře asynchronní operace služby v WFC. Operace služby se dá implementovat asynchronně nebo synchronně.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 5f890bd5124e2353cecee37d163b7f2c65b87fde
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244618"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="b6880-104">Postupy: Implementace operace asynchronní služby</span><span class="sxs-lookup"><span data-stu-id="b6880-104">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="b6880-105">V aplikacích Windows Communication Foundation (WCF) může být operace služby implementována asynchronně nebo synchronně bez diktování klienta, jak ho volat.</span><span class="sxs-lookup"><span data-stu-id="b6880-105">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="b6880-106">Například asynchronní operace služby mohou být volány synchronně a synchronní operace služby mohou být volány asynchronně.</span><span class="sxs-lookup"><span data-stu-id="b6880-106">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="b6880-107">Příklad, který ukazuje asynchronní volání operace v klientské aplikaci, naleznete v tématu [How to: Asynchronous volání Operations Service](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="b6880-107">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="b6880-108">Další informace o synchronních a asynchronních operacích najdete v tématu [Navrhování kontraktů služeb](designing-service-contracts.md) a [synchronních a asynchronních operací](synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b6880-108">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="b6880-109">Toto téma popisuje základní strukturu operace asynchronní služby, kód není úplný.</span><span class="sxs-lookup"><span data-stu-id="b6880-109">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="b6880-110">Úplný příklad na stranách služby a klienta najdete v tématu [asynchronní](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="b6880-110">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="b6880-111">Asynchronní implementace operace služby</span><span class="sxs-lookup"><span data-stu-id="b6880-111">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="b6880-112">V kontraktu služby deklarujte dvojici asynchronních metod podle pokynů pro asynchronní návrh .NET.</span><span class="sxs-lookup"><span data-stu-id="b6880-112">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="b6880-113">`Begin`Metoda přebírá parametr, objekt zpětného volání a objekt stavu a vrací a <xref:System.IAsyncResult?displayProperty=nameWithType> odpovídající `End` metodu, která přebírá <xref:System.IAsyncResult?displayProperty=nameWithType> a vrací vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="b6880-113">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="b6880-114">Další informace o asynchronních voláních naleznete v tématu [asynchronní programování vzory návrhu](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="b6880-114">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
2. <span data-ttu-id="b6880-115">Označte `Begin` metodu dvojice asynchronních metod s <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atributem a nastavte <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> vlastnost na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="b6880-115">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="b6880-116">Například následující kód provádí kroky 1 a 2.</span><span class="sxs-lookup"><span data-stu-id="b6880-116">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="b6880-117">Implementujte `Begin/End` dvojici metod ve třídě služby podle pokynů pro asynchronní návrh.</span><span class="sxs-lookup"><span data-stu-id="b6880-117">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="b6880-118">Například následující příklad kódu ukazuje implementaci, ve které je řetězec zapsán do konzoly v `Begin` částech a v rámci `End` asynchronní operace služby a návratovou hodnotou `End` operace je vrácen klientovi.</span><span class="sxs-lookup"><span data-stu-id="b6880-118">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="b6880-119">Úplný příklad kódu naleznete v části příklad.</span><span class="sxs-lookup"><span data-stu-id="b6880-119">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="b6880-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6880-120">Example</span></span>  
 <span data-ttu-id="b6880-121">Následující příklady kódu ukazují:</span><span class="sxs-lookup"><span data-stu-id="b6880-121">The following code examples show:</span></span>  
  
1. <span data-ttu-id="b6880-122">Rozhraní kontraktu služby s:</span><span class="sxs-lookup"><span data-stu-id="b6880-122">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="b6880-123">Synchronní `SampleMethod` operace.</span><span class="sxs-lookup"><span data-stu-id="b6880-123">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="b6880-124">Asynchronní `BeginSampleMethod` operace.</span><span class="sxs-lookup"><span data-stu-id="b6880-124">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="b6880-125">Dvojice asynchronních `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` operací.</span><span class="sxs-lookup"><span data-stu-id="b6880-125">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="b6880-126">Implementace služby pomocí <xref:System.IAsyncResult?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="b6880-126">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="b6880-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="b6880-127">See also</span></span>

- [<span data-ttu-id="b6880-128">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="b6880-128">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="b6880-129">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="b6880-129">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
