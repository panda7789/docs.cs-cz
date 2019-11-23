---
title: 'Postupy: Implementace operace asynchronní služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: b706ec49db123f33b3fc1ab0f420ed9a47e32f67
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320950"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="5d06c-102">Postupy: Implementace operace asynchronní služby</span><span class="sxs-lookup"><span data-stu-id="5d06c-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="5d06c-103">V aplikacích Windows Communication Foundation (WCF) může být operace služby implementována asynchronně nebo synchronně bez diktování klienta, jak ho volat.</span><span class="sxs-lookup"><span data-stu-id="5d06c-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="5d06c-104">Například asynchronní operace služby mohou být volány synchronně a synchronní operace služby mohou být volány asynchronně.</span><span class="sxs-lookup"><span data-stu-id="5d06c-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="5d06c-105">Příklad, který ukazuje asynchronní volání operace v klientské aplikaci, naleznete v tématu [How to: Asynchronous volání Operations Service](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="5d06c-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](./feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="5d06c-106">Další informace o synchronních a asynchronních operacích najdete v tématu [Navrhování kontraktů služeb](designing-service-contracts.md) a [synchronních a asynchronních operací](synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5d06c-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](designing-service-contracts.md) and [Synchronous and Asynchronous Operations](synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="5d06c-107">Toto téma popisuje základní strukturu operace asynchronní služby, kód není úplný.</span><span class="sxs-lookup"><span data-stu-id="5d06c-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="5d06c-108">Úplný příklad na stranách služby a klienta najdete v tématu [asynchronní](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="5d06c-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="5d06c-109">Asynchronní implementace operace služby</span><span class="sxs-lookup"><span data-stu-id="5d06c-109">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="5d06c-110">V kontraktu služby deklarujte dvojici asynchronních metod podle pokynů pro asynchronní návrh .NET.</span><span class="sxs-lookup"><span data-stu-id="5d06c-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="5d06c-111">Metoda `Begin` přebírá parametr, objekt zpětného volání a objekt stavu a vrací <xref:System.IAsyncResult?displayProperty=nameWithType> a odpovídající `End` metoda, která přebírá <xref:System.IAsyncResult?displayProperty=nameWithType> a vrací vrácenou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5d06c-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="5d06c-112">Další informace o asynchronních voláních naleznete v tématu [asynchronní programování vzory návrhu](https://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="5d06c-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2. <span data-ttu-id="5d06c-113">Označte metodu `Begin` dvojice asynchronních metod s atributem <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> a nastavte vlastnost <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> na `true`.</span><span class="sxs-lookup"><span data-stu-id="5d06c-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="5d06c-114">Například následující kód provádí kroky 1 a 2.</span><span class="sxs-lookup"><span data-stu-id="5d06c-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="5d06c-115">Implementujte dvojici metod `Begin/End` ve vaší třídě služby podle pokynů pro asynchronní návrh.</span><span class="sxs-lookup"><span data-stu-id="5d06c-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="5d06c-116">Například následující příklad kódu ukazuje implementaci, ve které je řetězec zapsán do konzoly v `Begin` i `End` částech asynchronní operace služby a návratovou hodnotou operace `End` je vrácena klientovi.</span><span class="sxs-lookup"><span data-stu-id="5d06c-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="5d06c-117">Úplný příklad kódu naleznete v části příklad.</span><span class="sxs-lookup"><span data-stu-id="5d06c-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="5d06c-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d06c-118">Example</span></span>  
 <span data-ttu-id="5d06c-119">Následující příklady kódu ukazují:</span><span class="sxs-lookup"><span data-stu-id="5d06c-119">The following code examples show:</span></span>  
  
1. <span data-ttu-id="5d06c-120">Rozhraní kontraktu služby s:</span><span class="sxs-lookup"><span data-stu-id="5d06c-120">A service contract interface with:</span></span>  
  
    1. <span data-ttu-id="5d06c-121">Synchronní operace `SampleMethod`.</span><span class="sxs-lookup"><span data-stu-id="5d06c-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2. <span data-ttu-id="5d06c-122">Asynchronní operace `BeginSampleMethod`.</span><span class="sxs-lookup"><span data-stu-id="5d06c-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3. <span data-ttu-id="5d06c-123">Asynchronní `BeginServiceAsyncMethod`/dvojici operací `EndServiceAsyncMethod`.</span><span class="sxs-lookup"><span data-stu-id="5d06c-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="5d06c-124">Implementace služby pomocí objektu <xref:System.IAsyncResult?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d06c-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="5d06c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5d06c-125">See also</span></span>

- [<span data-ttu-id="5d06c-126">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="5d06c-126">Designing Service Contracts</span></span>](designing-service-contracts.md)
- [<span data-ttu-id="5d06c-127">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="5d06c-127">Synchronous and Asynchronous Operations</span></span>](synchronous-and-asynchronous-operations.md)
