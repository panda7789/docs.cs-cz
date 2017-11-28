---
title: "Postupy: Implementace operace asynchronní služby"
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
ms.assetid: 4e5d2ea5-d8f8-4712-bd18-ea3c5461702c
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 65cd45a2510aa43c3f0c58a7cbf78c13e47d821e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-an-asynchronous-service-operation"></a><span data-ttu-id="c39ae-102">Postupy: Implementace operace asynchronní služby</span><span class="sxs-lookup"><span data-stu-id="c39ae-102">How to: Implement an Asynchronous Service Operation</span></span>
<span data-ttu-id="c39ae-103">V [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] aplikace, služby operaci lze provést synchronně nebo asynchronně bez diktování klientovi jejich volání.</span><span class="sxs-lookup"><span data-stu-id="c39ae-103">In [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] applications, a service operation can be implemented asynchronously or synchronously without dictating to the client how to call it.</span></span> <span data-ttu-id="c39ae-104">Například operace asynchronní služby můžete volání synchronně, a operací synchronní služby je možné volat asynchronně.</span><span class="sxs-lookup"><span data-stu-id="c39ae-104">For example, asynchronous service operations can be calling synchronously, and synchronous service operations can be called asynchronously.</span></span> <span data-ttu-id="c39ae-105">Příklad, který ukazuje, jak asynchronní volání operace v aplikaci klienta, naleznete v části [postupy: asynchronní volání operací služby](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span><span class="sxs-lookup"><span data-stu-id="c39ae-105">For an example that shows how to call an operation asynchronously in a client application, see [How to: Call Service Operations Asynchronously](../../../docs/framework/wcf/feature-details/how-to-call-wcf-service-operations-asynchronously.md).</span></span> [!INCLUDE[crabout](../../../includes/crabout-md.md)]<span data-ttu-id="c39ae-106">synchronní a asynchronní operace, najdete v části [navrhování kontraktů služby](../../../docs/framework/wcf/designing-service-contracts.md) a [synchronní a asynchronní operace](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span><span class="sxs-lookup"><span data-stu-id="c39ae-106"> synchronous and asynchronous operations, see [Designing Service Contracts](../../../docs/framework/wcf/designing-service-contracts.md) and [Synchronous and Asynchronous Operations](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md).</span></span> <span data-ttu-id="c39ae-107">Toto téma popisuje základní strukturu operace asynchronní služby, kód není úplný.</span><span class="sxs-lookup"><span data-stu-id="c39ae-107">This topic describes the basic structure of an asynchronous service operation, the code is not complete.</span></span> <span data-ttu-id="c39ae-108">Kompletní příklad, jak si služba a klient strany najdete v části [asynchronního](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).</span><span class="sxs-lookup"><span data-stu-id="c39ae-108">For a complete example of both the service and client sides see [Asynchronous](http://msdn.microsoft.com/en-us/833db946-f511-4f64-a26f-2759a11217c7).</span></span>  
  
### <a name="implement-a-service-operation-asynchronously"></a><span data-ttu-id="c39ae-109">Asynchronně implementovat operaci služby</span><span class="sxs-lookup"><span data-stu-id="c39ae-109">Implement a service operation asynchronously</span></span>  
  
1.  <span data-ttu-id="c39ae-110">Ve vašem kontrakt služby deklarujte dvojici asynchronní metoda podle pokynů pro asynchronní návrh .NET.</span><span class="sxs-lookup"><span data-stu-id="c39ae-110">In your service contract, declare an asynchronous method pair according to the .NET asynchronous design guidelines.</span></span> <span data-ttu-id="c39ae-111">`Begin` Metoda přebírá parametr objekt zpětného volání a stavu objektu a vrátí <xref:System.IAsyncResult?displayProperty=nameWithType> a odpovídající `End` metody, která přijímá <xref:System.IAsyncResult?displayProperty=nameWithType> a vrátí návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c39ae-111">The `Begin` method takes a parameter, a callback object, and a state object, and returns a <xref:System.IAsyncResult?displayProperty=nameWithType> and a matching `End` method that takes a <xref:System.IAsyncResult?displayProperty=nameWithType> and returns the return value.</span></span> <span data-ttu-id="c39ae-112">Další informace o asynchronní volání najdete v tématu [asynchronní vzory návrhu programování](http://go.microsoft.com/fwlink/?LinkId=248221).</span><span class="sxs-lookup"><span data-stu-id="c39ae-112">For more information about asynchronous calls, see [Asynchronous Programming Design Patterns](http://go.microsoft.com/fwlink/?LinkId=248221).</span></span>  
  
2.  <span data-ttu-id="c39ae-113">Označit `Begin` metoda pár asynchronní metody s <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> atribut a nastavte <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="c39ae-113">Mark the `Begin` method of the asynchronous method pair with the <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType> attribute and set the <xref:System.ServiceModel.OperationContractAttribute.AsyncPattern%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="c39ae-114">Například následující kód provede kroky 1 a 2.</span><span class="sxs-lookup"><span data-stu-id="c39ae-114">For example, the following code performs steps 1 and 2.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#6)]
     [!code-vb[C_SyncAsyncClient#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#6)]  
  
3.  <span data-ttu-id="c39ae-115">Implementace `Begin/End` dvojice metody ve třídě služby podle pokynů pro asynchronní návrh.</span><span class="sxs-lookup"><span data-stu-id="c39ae-115">Implement the `Begin/End` method pair in your service class according to the asynchronous design guidelines.</span></span> <span data-ttu-id="c39ae-116">Například následující příklad kódu ukazuje implementaci, ve kterém je řetězec zapsána do konzoly v obou `Begin` a `End` části operace asynchronní služby a vrátí hodnotu, která `End` operace vrácen do klienta.</span><span class="sxs-lookup"><span data-stu-id="c39ae-116">For example, the following code example shows an implementation in which a string is written to the console in both the `Begin` and `End` portions of the asynchronous service operation, and the return value of the `End` operation is returned to the client.</span></span> <span data-ttu-id="c39ae-117">Úplný příklad kódu najdete v části příklad.</span><span class="sxs-lookup"><span data-stu-id="c39ae-117">For the complete code example, see the Example section.</span></span>  
  
     [!code-csharp[C_SyncAsyncClient#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#3)]
     [!code-vb[C_SyncAsyncClient#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="c39ae-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="c39ae-118">Example</span></span>  
 <span data-ttu-id="c39ae-119">Následující příklady kódu ukazují:</span><span class="sxs-lookup"><span data-stu-id="c39ae-119">The following code examples show:</span></span>  
  
1.  <span data-ttu-id="c39ae-120">Rozhraní kontrakt služby s:</span><span class="sxs-lookup"><span data-stu-id="c39ae-120">A service contract interface with:</span></span>  
  
    1.  <span data-ttu-id="c39ae-121">Synchronního `SampleMethod` operaci.</span><span class="sxs-lookup"><span data-stu-id="c39ae-121">A synchronous `SampleMethod` operation.</span></span>  
  
    2.  <span data-ttu-id="c39ae-122">Asynchronní `BeginSampleMethod` operaci.</span><span class="sxs-lookup"><span data-stu-id="c39ae-122">An asynchronous `BeginSampleMethod` operation.</span></span>  
  
    3.  <span data-ttu-id="c39ae-123">Asynchronní `BeginServiceAsyncMethod` / `EndServiceAsyncMethod` pár operaci.</span><span class="sxs-lookup"><span data-stu-id="c39ae-123">An asynchronous `BeginServiceAsyncMethod`/`EndServiceAsyncMethod` operation pair.</span></span>  
  
2.  <span data-ttu-id="c39ae-124">Službu pomocí implementace <xref:System.IAsyncResult?displayProperty=nameWithType> objektu.</span><span class="sxs-lookup"><span data-stu-id="c39ae-124">A service implementation using a <xref:System.IAsyncResult?displayProperty=nameWithType> object.</span></span>  
  
 [!code-csharp[C_SyncAsyncClient#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_syncasyncclient/cs/services.cs#1)]
 [!code-vb[C_SyncAsyncClient#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_syncasyncclient/vb/services.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="c39ae-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="c39ae-125">See Also</span></span>  
 [<span data-ttu-id="c39ae-126">Navrhování kontraktů služby</span><span class="sxs-lookup"><span data-stu-id="c39ae-126">Designing Service Contracts</span></span>](../../../docs/framework/wcf/designing-service-contracts.md)  
 [<span data-ttu-id="c39ae-127">Synchronní a asynchronní operace</span><span class="sxs-lookup"><span data-stu-id="c39ae-127">Synchronous and Asynchronous Operations</span></span>](../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)
