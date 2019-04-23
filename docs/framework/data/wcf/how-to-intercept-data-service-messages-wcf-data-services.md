---
title: 'Postupy: Zachycování zpráv datové služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: ad0673f72b1a81d6bcfaf0704ccd698eda7bb20c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517821"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="7c752-102">Postupy: Zachycování zpráv datové služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="7c752-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="7c752-103">S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], tak, že můžete přidat vlastní logiku na operaci je možné zachytit zprávy s požadavkem.</span><span class="sxs-lookup"><span data-stu-id="7c752-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="7c752-104">Aby se zachytily zprávu, použijte metody speciálně s atributy v datové služby.</span><span class="sxs-lookup"><span data-stu-id="7c752-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="7c752-105">Další informace najdete v tématu [sběrače](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c752-105">For more information, see [Interceptors](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="7c752-106">V příkladu v tomto tématu se používá ukázková datová služba Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c752-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="7c752-107">Tato služba se vytvoří při dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="7c752-107">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="7c752-108">Chcete-li definovat zachycování dotazů pro sadu entit objednávky</span><span class="sxs-lookup"><span data-stu-id="7c752-108">To define a query interceptor for the Orders entity set</span></span>  
  
1. <span data-ttu-id="7c752-109">V projektu služby Northwind data otevřete soubor Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="7c752-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="7c752-110">Na stránce kódu `Northwind` třídy, přidejte následující `using` – příkaz (`Imports` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="7c752-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. <span data-ttu-id="7c752-111">V `Northwind` tříd, definice služby operace metodu s názvem `OnQueryOrders` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7c752-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="7c752-112">Chcete-li definovat zachycování změnu pro sadu entit produkty</span><span class="sxs-lookup"><span data-stu-id="7c752-112">To define a change interceptor for the Products entity set</span></span>  
  
1. <span data-ttu-id="7c752-113">V projektu služby Northwind data otevřete soubor Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="7c752-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="7c752-114">V `Northwind` tříd, definice služby operace metodu s názvem `OnChangeProducts` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="7c752-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="7c752-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c752-115">Example</span></span>  
 <span data-ttu-id="7c752-116">Tento příklad definuje metodu pro zachycování dotazů `Orders` sadu entit, který vrací výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="7c752-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="7c752-117">Tento výraz obsahuje delegáta, který filtruje požadovanou `Orders` podle související `Customers` , které mají konkrétní jméno kontaktu.</span><span class="sxs-lookup"><span data-stu-id="7c752-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="7c752-118">Název pak závisí na žádajícího uživatele.</span><span class="sxs-lookup"><span data-stu-id="7c752-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="7c752-119">Tento příklad předpokládá, že datové služby je hostovaná ve webové aplikaci ASP.NET, která používá WCF a že ověřování je povoleno.</span><span class="sxs-lookup"><span data-stu-id="7c752-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="7c752-120"><xref:System.Web.HttpContext> Třída se používá k načtení Princip aktuálního požadavku.</span><span class="sxs-lookup"><span data-stu-id="7c752-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="7c752-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c752-121">Example</span></span>  
 <span data-ttu-id="7c752-122">Tento příklad definuje metoda pro zachycování dotazů pro `Products` sady entit.</span><span class="sxs-lookup"><span data-stu-id="7c752-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="7c752-123">Tato metoda ověřuje vstup do služby pro <xref:System.Data.Services.UpdateOperations.Add> nebo <xref:System.Data.Services.UpdateOperations.Change> operace a vyvolá výjimku, pokud je se provede změna ukončená produktu.</span><span class="sxs-lookup"><span data-stu-id="7c752-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="7c752-124">Blokuje taky odstranění produkty jako nepodporovaná operace.</span><span class="sxs-lookup"><span data-stu-id="7c752-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="7c752-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c752-125">See also</span></span>

- [<span data-ttu-id="7c752-126">Postupy: Definování operace služby</span><span class="sxs-lookup"><span data-stu-id="7c752-126">How to: Define a Service Operation</span></span>](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)
- [<span data-ttu-id="7c752-127">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="7c752-127">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
