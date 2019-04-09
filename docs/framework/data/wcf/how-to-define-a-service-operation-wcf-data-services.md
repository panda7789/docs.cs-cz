---
title: 'Postupy: Definování operace služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 75691a49624c179166d18225fac9fdc6c17a2308
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138096"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="e1e47-102">Postupy: Definování operace služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="e1e47-102">How to: Define a Service Operation (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="e1e47-103">Zveřejněte metody, které jsou definovány na serveru jako servisní operace.</span><span class="sxs-lookup"><span data-stu-id="e1e47-103">expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="e1e47-104">Operace služby umožňují datové služby a zajistit tak přístup prostřednictvím identifikátoru URI metodě, která je definována na serveru.</span><span class="sxs-lookup"><span data-stu-id="e1e47-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="e1e47-105">K definování operace služby, použít [`WebGet]` nebo `[WebInvoke]` atribut do metody.</span><span class="sxs-lookup"><span data-stu-id="e1e47-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="e1e47-106">Pro podporu operátorů dotazu, musí vrátit operace služby <xref:System.Linq.IQueryable%601> instance.</span><span class="sxs-lookup"><span data-stu-id="e1e47-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="e1e47-107">Operace služby může přístup k podkladovému zdroji dat prostřednictvím <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> vlastnost <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="e1e47-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="e1e47-108">Další informace najdete v tématu [operací služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e1e47-108">For more information, see [Service Operations](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="e1e47-109">V příkladu v tomto tématu je definována operace služby s názvem `GetOrdersByCity` , která vrací vyfiltrované <xref:System.Linq.IQueryable%601> instanci `Orders` a související `Order_Details` objekty.</span><span class="sxs-lookup"><span data-stu-id="e1e47-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="e1e47-110">V příkladu přistupuje <xref:System.Data.Objects.ObjectContext> instanci, která je zdrojem dat pro datová služba Northwind vzorku.</span><span class="sxs-lookup"><span data-stu-id="e1e47-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="e1e47-111">Tato služba se vytvoří při dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="e1e47-111">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="e1e47-112">K definování operace služby v datová služba Northwind</span><span class="sxs-lookup"><span data-stu-id="e1e47-112">To define a service operation in the Northwind data service</span></span>  
  
1.  <span data-ttu-id="e1e47-113">V projektu služby Northwind data otevřete soubor Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="e1e47-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="e1e47-114">V `Northwind` tříd, definice služby operace metodu s názvem `GetOrdersByCity` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="e1e47-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  <span data-ttu-id="e1e47-115">V `InitializeService` metodu `Northwind` třídy, přidejte následující kód k umožnění přístupu k operace služby:</span><span class="sxs-lookup"><span data-stu-id="e1e47-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="e1e47-116">K dotazování GetOrdersByCity operace služby</span><span class="sxs-lookup"><span data-stu-id="e1e47-116">To query the GetOrdersByCity service operation</span></span>  
  
-   <span data-ttu-id="e1e47-117">Ve webovém prohlížeči zadejte jeden z následujících identifikátorů URI k vyvolání operace služby, který je definován v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="e1e47-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a><span data-ttu-id="e1e47-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1e47-118">Example</span></span>  
 <span data-ttu-id="e1e47-119">Následující příklad implementuje operace služby s názvem `GetOrderByCity` na datová služba Northwind.</span><span class="sxs-lookup"><span data-stu-id="e1e47-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="e1e47-120">Tato operace používá rozhraní ADO.NET Entity Framework vrátit sadu `Orders` a související `Order_Details` objektů jako <xref:System.Linq.IQueryable%601> instance podle zadané město.</span><span class="sxs-lookup"><span data-stu-id="e1e47-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1e47-121">Operátory dotazu jsou podporované na tomto koncovém bodu služby operaci, protože metoda vrátí <xref:System.Linq.IQueryable%601> instance.</span><span class="sxs-lookup"><span data-stu-id="e1e47-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a><span data-ttu-id="e1e47-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e1e47-122">See also</span></span>

- [<span data-ttu-id="e1e47-123">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="e1e47-123">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
