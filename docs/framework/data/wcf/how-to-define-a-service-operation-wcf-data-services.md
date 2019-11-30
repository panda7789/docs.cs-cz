---
title: 'Postupy: definování operace služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: e9d15698c1e020f5b4179efb3e8492f3754ff02f
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569132"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="a7669-102">Postupy: definování operace služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="a7669-102">How to: Define a Service Operation (WCF Data Services)</span></span>

<span data-ttu-id="a7669-103">WCF Data Services vystavovat metody, které jsou definovány na serveru jako operace služby.</span><span class="sxs-lookup"><span data-stu-id="a7669-103">WCF Data Services expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="a7669-104">Operace služby umožňují datové službě poskytovat přístup prostřednictvím identifikátoru URI metodě, která je definována na serveru.</span><span class="sxs-lookup"><span data-stu-id="a7669-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="a7669-105">Chcete-li definovat operaci služby, použijte pro metodu atribut [`WebGet]` nebo `[WebInvoke]`.</span><span class="sxs-lookup"><span data-stu-id="a7669-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="a7669-106">Aby bylo možné podporovat operátory dotazů, musí operace služby vracet instanci <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="a7669-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="a7669-107">Operace služby mohou přistupovat k základnímu zdroji dat prostřednictvím vlastnosti <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> v <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="a7669-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="a7669-108">Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a7669-108">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="a7669-109">Příklad v tomto tématu definuje operaci služby s názvem `GetOrdersByCity`, která vrací filtrovanou <xref:System.Linq.IQueryable%601> instanci `Orders` a související objekty `Order_Details`.</span><span class="sxs-lookup"><span data-stu-id="a7669-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="a7669-110">Tento příklad přistupuje k instanci <xref:System.Data.Objects.ObjectContext>, která je zdrojem dat pro ukázkovou datovou službu Northwind.</span><span class="sxs-lookup"><span data-stu-id="a7669-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="a7669-111">Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a7669-111">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="a7669-112">Definování operace služby v datové službě Northwind</span><span class="sxs-lookup"><span data-stu-id="a7669-112">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="a7669-113">V projektu datové služby Northwind otevřete soubor Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="a7669-113">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="a7669-114">Ve třídě `Northwind` Definujte metodu operace služby s názvem `GetOrdersByCity` následujícím způsobem:</span><span class="sxs-lookup"><span data-stu-id="a7669-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="a7669-115">V metodě `InitializeService` `Northwind` třídy přidejte následující kód pro povolení přístupu k operaci služby:</span><span class="sxs-lookup"><span data-stu-id="a7669-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="a7669-116">Dotazování na operaci služby GetOrdersByCity</span><span class="sxs-lookup"><span data-stu-id="a7669-116">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="a7669-117">Ve webovém prohlížeči zadejte jeden z následujících identifikátorů URI pro vyvolání operace služby, která je definována v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a7669-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="a7669-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7669-118">Example</span></span>

<span data-ttu-id="a7669-119">Následující příklad implementuje operaci služby s názvem `GetOrderByCity` ve službě Northwind data Service.</span><span class="sxs-lookup"><span data-stu-id="a7669-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="a7669-120">Tato operace používá Entity Framework ADO.NET k vrácení sady `Orders` a souvisejících `Order_Details` objektů jako instance <xref:System.Linq.IQueryable%601> na základě zadaného názvu města.</span><span class="sxs-lookup"><span data-stu-id="a7669-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="a7669-121">Operátory dotazů jsou podporovány u tohoto koncového bodu operace služby, protože metoda vrací instanci <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="a7669-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="a7669-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7669-122">See also</span></span>

- [<span data-ttu-id="a7669-123">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="a7669-123">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
