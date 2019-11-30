---
title: 'Postupy: zachycení zpráv datových služeb (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: 4f2d6cf34c820c60181d5287298898af5eb8d038
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569034"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="f2e6e-102">Postupy: zachycení zpráv datových služeb (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="f2e6e-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="f2e6e-103">Pomocí WCF Data Services můžete zachytit zprávy s požadavkem, abyste mohli přidat vlastní logiku k operaci.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-103">With WCF Data Services, you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="f2e6e-104">Chcete-li zachytit zprávu, použijte v datové službě speciálně používané metody s atributy.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="f2e6e-105">Další informace naleznete v tématu [zachycení](interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f2e6e-105">For more information, see [Interceptors](interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="f2e6e-106">Příklad v tomto tématu používá ukázkovou datovou službu Northwind.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="f2e6e-107">Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f2e6e-107">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="f2e6e-108">Definování zachycování dotazů pro sadu entit objednávky</span><span class="sxs-lookup"><span data-stu-id="f2e6e-108">To define a query interceptor for the Orders entity set</span></span>  
  
1. <span data-ttu-id="f2e6e-109">V projektu datové služby Northwind otevřete soubor Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="f2e6e-110">Na kódové stránce pro třídu `Northwind` přidejte následující příkaz `using` (`Imports` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="f2e6e-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. <span data-ttu-id="f2e6e-111">Ve třídě `Northwind` Definujte metodu operace služby s názvem `OnQueryOrders` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f2e6e-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="f2e6e-112">Definování zachytávací pro sadu entit produktů</span><span class="sxs-lookup"><span data-stu-id="f2e6e-112">To define a change interceptor for the Products entity set</span></span>  
  
1. <span data-ttu-id="f2e6e-113">V projektu datové služby Northwind otevřete soubor Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="f2e6e-114">Ve třídě `Northwind` Definujte metodu operace služby s názvem `OnChangeProducts` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="f2e6e-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="f2e6e-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e6e-115">Example</span></span>  
 <span data-ttu-id="f2e6e-116">Tento příklad definuje metodu zachycování dotazů pro sadu entit `Orders`, která vrací výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="f2e6e-117">Tento výraz obsahuje delegáta, který filtruje požadované `Orders` na základě souvisejících `Customers`, které mají konkrétní název kontaktu.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="f2e6e-118">Název se pak určí na základě žádajícího uživatele.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="f2e6e-119">V tomto příkladu se předpokládá, že je datová služba hostovaná v ASP.NET webové aplikaci, která používá WCF a toto ověřování je povolené.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="f2e6e-120">Třída <xref:System.Web.HttpContext> slouží k načtení principu aktuální žádosti.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="f2e6e-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="f2e6e-121">Example</span></span>  
 <span data-ttu-id="f2e6e-122">Tento příklad definuje metodu pro zachycování `Products` entit pro sadu entit.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="f2e6e-123">Tato metoda ověřuje vstup služby pro operaci <xref:System.Data.Services.UpdateOperations.Add> nebo <xref:System.Data.Services.UpdateOperations.Change> a vyvolá výjimku, pokud se změní na zastavený produkt.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="f2e6e-124">Také blokuje odstraňování produktů jako nepodporovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="f2e6e-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="f2e6e-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f2e6e-125">See also</span></span>

- [<span data-ttu-id="f2e6e-126">Postupy: Definování operace služby</span><span class="sxs-lookup"><span data-stu-id="f2e6e-126">How to: Define a Service Operation</span></span>](how-to-define-a-service-operation-wcf-data-services.md)
- [<span data-ttu-id="f2e6e-127">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="f2e6e-127">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
