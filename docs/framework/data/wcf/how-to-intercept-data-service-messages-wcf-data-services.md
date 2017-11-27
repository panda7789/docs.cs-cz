---
title: "Postupy: zachycení datových služba zpráv (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6c18664eaa154fbc048c77cb359d0926f04b7e52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="f183c-102">Postupy: zachycení datových služba zpráv (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="f183c-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="f183c-103">S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], tak, aby můžete přidat vlastní logiky do operace je možné zachytit zprávy žádosti.</span><span class="sxs-lookup"><span data-stu-id="f183c-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="f183c-104">K zachycení zprávy, použijete speciálně s atributy metody ve službě data.</span><span class="sxs-lookup"><span data-stu-id="f183c-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="f183c-105">Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f183c-105">For more information, see [Interceptors](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="f183c-106">Příklad v tomto tématu používá službu Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="f183c-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="f183c-107">Tato služba se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f183c-107">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="f183c-108">Chcete-li definovat interceptoru dotazu pro sadu entit objednávky</span><span class="sxs-lookup"><span data-stu-id="f183c-108">To define a query interceptor for the Orders entity set</span></span>  
  
1.  <span data-ttu-id="f183c-109">V projektu služby Northwind data otevřete soubor Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="f183c-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="f183c-110">V kódové stránky pro `Northwind` třídy, přidejte následující `using` – příkaz (`Imports` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f183c-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3.  <span data-ttu-id="f183c-111">V `Northwind` třídy, definování metody operace služby s názvem `OnQueryOrders` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f183c-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="f183c-112">Chcete-li definovat Změna interceptoru pro sadu entit produkty</span><span class="sxs-lookup"><span data-stu-id="f183c-112">To define a change interceptor for the Products entity set</span></span>  
  
1.  <span data-ttu-id="f183c-113">V projektu služby Northwind data otevřete soubor Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="f183c-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="f183c-114">V `Northwind` třídy, definování metody operace služby s názvem `OnChangeProducts` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f183c-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="f183c-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f183c-115">Example</span></span>  
 <span data-ttu-id="f183c-116">Tento příklad definuje metodu interceptoru dotaz `Orders` sady entit, který vrací výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="f183c-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="f183c-117">Tento výraz obsahuje delegáta, který filtruje požadované `Orders` podle související `Customers` mají konkrétní jméno kontaktní osoby.</span><span class="sxs-lookup"><span data-stu-id="f183c-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="f183c-118">Název je zase určen na základě žádajícího uživatele.</span><span class="sxs-lookup"><span data-stu-id="f183c-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="f183c-119">Tento příklad předpokládá, že je služba data hostovaným v rámci ASP.NET – webové aplikace, která používá WCF a je povolen, ověření.</span><span class="sxs-lookup"><span data-stu-id="f183c-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="f183c-120"><xref:System.Web.HttpContext> Třída se používá k načtení Princip aktuální žádosti.</span><span class="sxs-lookup"><span data-stu-id="f183c-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="f183c-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="f183c-121">Example</span></span>  
 <span data-ttu-id="f183c-122">Tento příklad definuje metodu interceptoru změn `Products` sady entit.</span><span class="sxs-lookup"><span data-stu-id="f183c-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="f183c-123">Tato metoda ověří vstup se službou pro <xref:System.Data.Services.UpdateOperations.Add> nebo <xref:System.Data.Services.UpdateOperations.Change> operace a vyvolá výjimku, je-li ke změně je odeslána na deaktivovaný produkt.</span><span class="sxs-lookup"><span data-stu-id="f183c-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="f183c-124">Blokuje taky odstranění produkty jako nepodporovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="f183c-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="f183c-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="f183c-125">See Also</span></span>  
 [<span data-ttu-id="f183c-126">Postupy: definování operaci služby</span><span class="sxs-lookup"><span data-stu-id="f183c-126">How to: Define a Service Operation</span></span>](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)  
 [<span data-ttu-id="f183c-127">Definování datových služeb WCF</span><span class="sxs-lookup"><span data-stu-id="f183c-127">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
