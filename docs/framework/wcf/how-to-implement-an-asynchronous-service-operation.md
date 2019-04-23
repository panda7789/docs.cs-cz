---
title: 'Postupy: Implementace asynchronní operace služby'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
ms.openlocfilehash: 603ee57475b3e7b1af607d49050e3276fd3082d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59298653"
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="2f82e-102">Postupy: Implementace asynchronní operace služby</span><span class="sxs-lookup"><span data-stu-id="2f82e-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="2f82e-103">V aplikacích Windows Communication Foundation (WCF) operace služby lze provést synchronní nebo asynchronní bez diktování klientovi jejich volání.</span><span class="sxs-lookup"><span data-stu-id="2f82e-103">In Windows Communication Foundation (WCF) applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="2f82e-104">Například operace asynchronní služby je možné volat synchronně, a operace synchronní služby může být volána asynchronně.</span><span class="sxs-lookup"><span data-stu-id="2f82e-104">For example, asynchronous service operations can be called synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="2f82e-105">Příklad, který ukazuje, jak volat operace asynchronně v klientské aplikaci, najdete v části [jak: Asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="2f82e-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> <span data-ttu-id="2f82e-106">Další informace o synchronní a asynchronní operace, najdete v části [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md) a [synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="2f82e-106">For more information about synchronous and asynchronous operations, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) and [Synchronous and Asynchronous Operations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="2f82e-107">Toto téma popisuje základní struktura operace asynchronní služby, není kompletní kód.</span><span class="sxs-lookup"><span data-stu-id="2f82e-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="2f82e-108">Úplný příklad stranách klienta i služby, najdete v části [asynchronní](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="2f82e-108">For a complete example of both the service and client sides, see [Asynchronous](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms751505(v=vs.100)).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="2f82e-109">Implementace operace služby asynchronně</span><span class="sxs-lookup"><span data-stu-id="2f82e-109">Implement a service operation asynchronously</span></span>  
  
1. <span data-ttu-id="2f82e-110">V servisní smlouvě deklaraci páru asynchronní metoda podle pokynů návrhu asynchronních rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2f82e-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="2f82e-111">`Begin` Metoda přijímá parametr, objekt zpětného volání a stavu objektu a vrátí <xref:System.IAsyncResult?displayProperty=nameWithType> a odpovídající `End` metodu, která přebírá <xref:System.IAsyncResult?displayProperty=nameWithType> a vrátí návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2f82e-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="2f82e-112">Další informace o asynchronní volání najdete v tématu [Asynchronous Programming Patterns návrhu](https://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="2f82e-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](https://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2. <span data-ttu-id="2f82e-113">Mark `Begin` metody, které odpovídá páru asynchronní metody s <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atribut a nastavit <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="2f82e-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="2f82e-114">Například následující kód provede kroky 1 a 2.</span><span class="sxs-lookup"><span data-stu-id="2f82e-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3. <span data-ttu-id="2f82e-115">Implementace `Begin/End` dvojice metody ve třídě služby podle pokynů asynchronní návrh.</span><span class="sxs-lookup"><span data-stu-id="2f82e-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="2f82e-116">Například následující příklad kódu ukazuje implementaci, ve kterém je napsán řetězec do konzoly v obou `Begin` a `End` části operace asynchronní služby a návratová hodnota `End` operace vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="2f82e-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="2f82e-117">Příklad úplného kódu naleznete v části příklad.</span><span class="sxs-lookup"><span data-stu-id="2f82e-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="2f82e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f82e-118">Example</span></span>  
 <span data-ttu-id="2f82e-119">Následující příklady ukazují kód:</span><span class="sxs-lookup"><span data-stu-id="2f82e-119">The following code examples show:</span></span>  
  
1. <span data-ttu-id="2f82e-120">Rozhraní kontraktu služby se:</span><span class="sxs-lookup"><span data-stu-id="2f82e-120">A service contract interface with:</span></span>  
  
    1.  <span data-ttu-id="2f82e-121">Synchronního `SampleMethod` operace.</span><span class="sxs-lookup"><span data-stu-id="2f82e-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2.  <span data-ttu-id="2f82e-122">Asynchronní `BeginSampleMethod` operace.</span><span class="sxs-lookup"><span data-stu-id="2f82e-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3.  <span data-ttu-id="2f82e-123">Asynchronní `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` pár operace.</span><span class="sxs-lookup"><span data-stu-id="2f82e-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2. <span data-ttu-id="2f82e-124">Implementace služby pomocí <xref:System.IAsyncResult?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="2f82e-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2f82e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f82e-125">See also</span></span>

- [<span data-ttu-id="2f82e-126">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="2f82e-126">Designing Service Contracts</span></span>](../../../docs/framework/wcf/designing-service-contracts.md)
- [<span data-ttu-id="2f82e-127">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="2f82e-127">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
