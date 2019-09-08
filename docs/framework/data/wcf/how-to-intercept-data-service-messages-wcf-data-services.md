---
title: 'Postupy: Zachytávání zpráv datových služeb (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- query interceptors [WCF Data Services]
ms.assetid: 24b9df1b-b54b-4795-a033-edf333675de6
ms.openlocfilehash: cecfdd74779e3ab1c908957afac3c9fccf79f383
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780033"
---
# <a name="how-to-intercept-data-service-messages-wcf-data-services"></a><span data-ttu-id="0af4d-102">Postupy: Zachytávání zpráv datových služeb (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="0af4d-102">How to: Intercept Data Service Messages (WCF Data Services)</span></span>
<span data-ttu-id="0af4d-103">Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]můžete zachytit zprávy s požadavkem, abyste mohli přidat vlastní logiku k operaci.</span><span class="sxs-lookup"><span data-stu-id="0af4d-103">With [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], you can intercept request messages so that you can add custom logic to an operation.</span></span> <span data-ttu-id="0af4d-104">Chcete-li zachytit zprávu, použijte v datové službě speciálně používané metody s atributy.</span><span class="sxs-lookup"><span data-stu-id="0af4d-104">To intercept a message, you use specially attributed methods in the data service.</span></span> <span data-ttu-id="0af4d-105">Další informace naleznete v tématu [zachycení](interceptors-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="0af4d-105">For more information, see [Interceptors](interceptors-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="0af4d-106">Příklad v tomto tématu používá ukázkovou datovou službu Northwind.</span><span class="sxs-lookup"><span data-stu-id="0af4d-106">The example in this topic uses the Northwind sample data service.</span></span> <span data-ttu-id="0af4d-107">Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="0af4d-107">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-query-interceptor-for-the-orders-entity-set"></a><span data-ttu-id="0af4d-108">Definování zachycování dotazů pro sadu entit objednávky</span><span class="sxs-lookup"><span data-stu-id="0af4d-108">To define a query interceptor for the Orders entity set</span></span>  
  
1. <span data-ttu-id="0af4d-109">V projektu datové služby Northwind otevřete soubor Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="0af4d-109">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="0af4d-110">Na kódové stránce `Northwind` třídy přidejte následující `using` příkaz (`Imports` v Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="0af4d-110">In the code page for the `Northwind` class, add the following `using` statement (`Imports` in Visual Basic).</span></span>  
  
     [!code-csharp[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#usinglinqexpressions)]
     [!code-vb[Astoria Northwind Service#UsingLinqExpressions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#usinglinqexpressions)]  
  
3. <span data-ttu-id="0af4d-111">Ve třídě Definujte metodu operace služby s názvem `OnQueryOrders` následujícím způsobem: `Northwind`</span><span class="sxs-lookup"><span data-stu-id="0af4d-111">In the `Northwind` class, define a service operation method named `OnQueryOrders` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptordef)]
     [!code-vb[Astoria Northwind Service#QueryInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptordef)]  
  
### <a name="to-define-a-change-interceptor-for-the-products-entity-set"></a><span data-ttu-id="0af4d-112">Definování zachytávací pro sadu entit produktů</span><span class="sxs-lookup"><span data-stu-id="0af4d-112">To define a change interceptor for the Products entity set</span></span>  
  
1. <span data-ttu-id="0af4d-113">V projektu datové služby Northwind otevřete soubor Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="0af4d-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2. <span data-ttu-id="0af4d-114">Ve třídě Definujte metodu operace služby s názvem `OnChangeProducts` následujícím způsobem: `Northwind`</span><span class="sxs-lookup"><span data-stu-id="0af4d-114">In the `Northwind` class, define a service operation method named `OnChangeProducts` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptordef)]
     [!code-vb[Astoria Northwind Service#ChangeInterceptorDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptordef)]  
  
## <a name="example"></a><span data-ttu-id="0af4d-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="0af4d-115">Example</span></span>  
 <span data-ttu-id="0af4d-116">Tento příklad definuje metodu pro zachycování dotazů pro `Orders` sadu entit, která vrací výraz lambda.</span><span class="sxs-lookup"><span data-stu-id="0af4d-116">This example defines a query interceptor method for the `Orders` entity set that returns a lambda expression.</span></span> <span data-ttu-id="0af4d-117">Tento výraz obsahuje delegáta, který filtruje požadovaný `Orders` název na základě `Customers` souvisejícího názvu kontaktu.</span><span class="sxs-lookup"><span data-stu-id="0af4d-117">This expression contains a delegate that filters the requested `Orders` based on related `Customers` that have a specific contact name.</span></span> <span data-ttu-id="0af4d-118">Název se pak určí na základě žádajícího uživatele.</span><span class="sxs-lookup"><span data-stu-id="0af4d-118">The name is in turn determined based on the requesting user.</span></span> <span data-ttu-id="0af4d-119">V tomto příkladu se předpokládá, že je datová služba hostovaná v ASP.NET webové aplikaci, která používá WCF a toto ověřování je povolené.</span><span class="sxs-lookup"><span data-stu-id="0af4d-119">This example assumes that the data service is hosted within an ASP.NET Web application that uses WCF, and that authentication is enabled.</span></span> <span data-ttu-id="0af4d-120"><xref:System.Web.HttpContext> Třída se používá k načtení principu aktuální žádosti.</span><span class="sxs-lookup"><span data-stu-id="0af4d-120">The <xref:System.Web.HttpContext> class is used to retrieve the principle of the current request.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#queryinterceptor)]
 [!code-vb[Astoria Northwind Service#QueryInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#queryinterceptor)]  
  
## <a name="example"></a><span data-ttu-id="0af4d-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="0af4d-121">Example</span></span>  
 <span data-ttu-id="0af4d-122">Tento příklad definuje metodu pro zachycování pro `Products` sadu entit.</span><span class="sxs-lookup"><span data-stu-id="0af4d-122">This example defines a change interceptor method for the `Products` entity set.</span></span> <span data-ttu-id="0af4d-123">Tato metoda ověřuje vstup služby pro <xref:System.Data.Services.UpdateOperations.Add> operaci nebo <xref:System.Data.Services.UpdateOperations.Change> a vyvolá výjimku, pokud se změní na zastavený produkt.</span><span class="sxs-lookup"><span data-stu-id="0af4d-123">This method validates input to the service for an <xref:System.Data.Services.UpdateOperations.Add> or <xref:System.Data.Services.UpdateOperations.Change> operation and raises an exception if a change is being made to a discontinued product.</span></span> <span data-ttu-id="0af4d-124">Také blokuje odstraňování produktů jako nepodporovanou operaci.</span><span class="sxs-lookup"><span data-stu-id="0af4d-124">It also blocks the deletion of products as an unsupported operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#changeinterceptor)]
 [!code-vb[Astoria Northwind Service#ChangeInterceptor](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#changeinterceptor)]  
  
## <a name="see-also"></a><span data-ttu-id="0af4d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0af4d-125">See also</span></span>

- [<span data-ttu-id="0af4d-126">Postupy: Definovat operaci služby</span><span class="sxs-lookup"><span data-stu-id="0af4d-126">How to: Define a Service Operation</span></span>](how-to-define-a-service-operation-wcf-data-services.md)
- [<span data-ttu-id="0af4d-127">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="0af4d-127">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
