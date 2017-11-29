---
title: "Postupy: Definování operace služby (služby WCF Data Services)"
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
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: feac51c92a7e963d440eefbae94a58b94f49797e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="d16ee-102">Postupy: Definování operace služby (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="d16ee-102">How to: Define a Service Operation (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="d16ee-103">vystavení metody, které jsou definovány na serveru jako operací služby.</span><span class="sxs-lookup"><span data-stu-id="d16ee-103"> expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="d16ee-104">Operace služby povolit datové služby poskytovat přístup pomocí identifikátoru URI na metodu, která je definován na serveru.</span><span class="sxs-lookup"><span data-stu-id="d16ee-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="d16ee-105">Chcete-li definovat operace služby, použít [`WebGet]` nebo `[WebInvoke]` atribut do metody.</span><span class="sxs-lookup"><span data-stu-id="d16ee-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="d16ee-106">Pro podporu operátory dotazu, musí vracet operace služby <xref:System.Linq.IQueryable%601> instance.</span><span class="sxs-lookup"><span data-stu-id="d16ee-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="d16ee-107">Operace služby může přístup ke zdroji dat základní prostřednictvím <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> vlastnost <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="d16ee-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="d16ee-108">Další informace najdete v tématu [operací služby](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d16ee-108">For more information, see [Service Operations](../../../../docs/framework/data/wcf/service-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="d16ee-109">V příkladu v tomto tématu definuje operace služby s názvem `GetOrdersByCity` , který vrací vyfiltrované <xref:System.Linq.IQueryable%601> instanci `Orders` a související `Order_Details` objekty.</span><span class="sxs-lookup"><span data-stu-id="d16ee-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="d16ee-110">V příkladu přistupuje <xref:System.Data.Objects.ObjectContext> instance, který je zdrojem dat pro službu Northwind ukázková data.</span><span class="sxs-lookup"><span data-stu-id="d16ee-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="d16ee-111">Tato služba se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d16ee-111">This service is created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="d16ee-112">Chcete-li definovat operace služby ve službě data Northwind</span><span class="sxs-lookup"><span data-stu-id="d16ee-112">To define a service operation in the Northwind data service</span></span>  
  
1.  <span data-ttu-id="d16ee-113">V projektu služby Northwind data otevřete soubor Northwind.svc.</span><span class="sxs-lookup"><span data-stu-id="d16ee-113">In the Northwind data service project, open the Northwind.svc file.</span></span>  
  
2.  <span data-ttu-id="d16ee-114">V `Northwind` třídy, definování metody operace služby s názvem `GetOrdersByCity` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="d16ee-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
3.  <span data-ttu-id="d16ee-115">V `InitializeService` metodu `Northwind` třídy, přidejte následující kód k povolení přístupu k operaci služby:</span><span class="sxs-lookup"><span data-stu-id="d16ee-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>  
  
     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="d16ee-116">K dotazování GetOrdersByCity operaci služby</span><span class="sxs-lookup"><span data-stu-id="d16ee-116">To query the GetOrdersByCity service operation</span></span>  
  
-   <span data-ttu-id="d16ee-117">Ve webovém prohlížeči zadejte jeden z následujících identifikátorů URI k vyvolání operace služby, která je definována v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="d16ee-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`  
  
    -   `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`  
  
## <a name="example"></a><span data-ttu-id="d16ee-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d16ee-118">Example</span></span>  
 <span data-ttu-id="d16ee-119">Následující příklad implementuje operace služby s názvem `GetOrderByCity` na službu Northwind data.</span><span class="sxs-lookup"><span data-stu-id="d16ee-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="d16ee-120">Tato operace používá k vrácení sadu ADO.NET Entity Framework `Orders` a související `Order_Details` objekty jako <xref:System.Linq.IQueryable%601> instance na základě zadané města názvu.</span><span class="sxs-lookup"><span data-stu-id="d16ee-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d16ee-121">Operátory dotazu jsou podporována pro tento koncový bod služby operaci, protože metoda vrátí <xref:System.Linq.IQueryable%601> instance.</span><span class="sxs-lookup"><span data-stu-id="d16ee-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperation)]
 [!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperation)]  
  
## <a name="see-also"></a><span data-ttu-id="d16ee-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="d16ee-122">See Also</span></span>  
 [<span data-ttu-id="d16ee-123">Definování datových služeb WCF</span><span class="sxs-lookup"><span data-stu-id="d16ee-123">Defining WCF Data Services</span></span>](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)
