---
title: 'Postupy: Definovat operaci služby (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Service Operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: dfcd3cb1-2f07-4d0b-b16a-6b056c4f45fa
ms.openlocfilehash: 3154fadeda400440f68a184b430b7ff15a02203d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780086"
---
# <a name="how-to-define-a-service-operation-wcf-data-services"></a><span data-ttu-id="9695e-102">Postupy: Definovat operaci služby (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="9695e-102">How to: Define a Service Operation (WCF Data Services)</span></span>

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="9695e-103">Vystavte metody, které jsou definovány na serveru jako operace služby.</span><span class="sxs-lookup"><span data-stu-id="9695e-103">expose methods that are defined on the server as service operations.</span></span> <span data-ttu-id="9695e-104">Operace služby umožňují datové službě poskytovat přístup prostřednictvím identifikátoru URI metodě, která je definována na serveru.</span><span class="sxs-lookup"><span data-stu-id="9695e-104">Service operations allow a data service to provide access through a URI to a method that is defined on the server.</span></span> <span data-ttu-id="9695e-105">Chcete-li definovat operaci služby, použijte atribut`WebGet]` [ `[WebInvoke]` nebo pro metodu.</span><span class="sxs-lookup"><span data-stu-id="9695e-105">To define a service operation, apply the [`WebGet]` or `[WebInvoke]` attribute to the method.</span></span> <span data-ttu-id="9695e-106">Aby bylo možné podporovat operátory dotazů, musí operace služby vracet <xref:System.Linq.IQueryable%601> instanci.</span><span class="sxs-lookup"><span data-stu-id="9695e-106">To support query operators, the service operation must return an <xref:System.Linq.IQueryable%601> instance.</span></span> <span data-ttu-id="9695e-107">Operace služby mohou přistupovat k základnímu zdroji dat prostřednictvím <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> vlastnosti <xref:System.Data.Services.DataService%601>v.</span><span class="sxs-lookup"><span data-stu-id="9695e-107">Service operations may access the underlying data source through the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> property on the <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="9695e-108">Další informace najdete v tématu [provozní operace](service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9695e-108">For more information, see [Service Operations](service-operations-wcf-data-services.md).</span></span>

<span data-ttu-id="9695e-109">Příklad v tomto tématu definuje operaci služby s `GetOrdersByCity` názvem, která vrací filtrovanou <xref:System.Linq.IQueryable%601> instanci `Orders` a související `Order_Details` objekty.</span><span class="sxs-lookup"><span data-stu-id="9695e-109">The example in this topic defines a service operation named `GetOrdersByCity` that returns a filtered <xref:System.Linq.IQueryable%601> instance of `Orders` and related `Order_Details` objects.</span></span> <span data-ttu-id="9695e-110">V příkladu se přistupuje k <xref:System.Data.Objects.ObjectContext> instanci, která je zdrojem dat pro ukázkovou datovou službu Northwind.</span><span class="sxs-lookup"><span data-stu-id="9695e-110">The example accesses the <xref:System.Data.Objects.ObjectContext> instance that is the data source for the Northwind sample data service.</span></span> <span data-ttu-id="9695e-111">Tato služba se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="9695e-111">This service is created when you complete the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

### <a name="to-define-a-service-operation-in-the-northwind-data-service"></a><span data-ttu-id="9695e-112">Definování operace služby v datové službě Northwind</span><span class="sxs-lookup"><span data-stu-id="9695e-112">To define a service operation in the Northwind data service</span></span>

1. <span data-ttu-id="9695e-113">V projektu datové služby Northwind otevřete soubor Northwind. svc.</span><span class="sxs-lookup"><span data-stu-id="9695e-113">In the Northwind data service project, open the Northwind.svc file.</span></span>

2. <span data-ttu-id="9695e-114">Ve třídě Definujte metodu operace služby s názvem `GetOrdersByCity` následujícím způsobem: `Northwind`</span><span class="sxs-lookup"><span data-stu-id="9695e-114">In the `Northwind` class, define a service operation method named `GetOrdersByCity` as follows:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
     [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]

3. <span data-ttu-id="9695e-115">`InitializeService` V metodě `Northwind` třídy přidejte následující kód pro povolení přístupu k operaci služby:</span><span class="sxs-lookup"><span data-stu-id="9695e-115">In the `InitializeService` method of the `Northwind` class, add the following code to enable access to the service operation:</span></span>

     [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
     [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]

### <a name="to-query-the-getordersbycity-service-operation"></a><span data-ttu-id="9695e-116">Dotazování na operaci služby GetOrdersByCity</span><span class="sxs-lookup"><span data-stu-id="9695e-116">To query the GetOrdersByCity service operation</span></span>

- <span data-ttu-id="9695e-117">Ve webovém prohlížeči zadejte jeden z následujících identifikátorů URI pro vyvolání operace služby, která je definována v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="9695e-117">In a Web browser, enter one of the following URIs to invoke the service operation that is defined in the following example:</span></span>

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$top=2`

  - `http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc`

## <a name="example"></a><span data-ttu-id="9695e-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="9695e-118">Example</span></span>

<span data-ttu-id="9695e-119">Následující příklad implementuje operaci služby s názvem `GetOrderByCity` ve službě Northwind data Service.</span><span class="sxs-lookup"><span data-stu-id="9695e-119">The following example implements a service operation named `GetOrderByCity` on the Northwind data service.</span></span> <span data-ttu-id="9695e-120">Tato operace používá Entity Framework ADO.NET k vrácení sady `Orders` a souvisejících `Order_Details` objektů jako <xref:System.Linq.IQueryable%601> instance na základě zadaného názvu města.</span><span class="sxs-lookup"><span data-stu-id="9695e-120">This operation uses the ADO.NET Entity Framework to return a set of `Orders` and related `Order_Details` objects as an <xref:System.Linq.IQueryable%601> instance based on the provided city name.</span></span>

> [!NOTE]
> <span data-ttu-id="9695e-121">Operátory dotazů jsou podporovány u tohoto koncového bodu operace služby, protože metoda <xref:System.Linq.IQueryable%601> vrací instanci.</span><span class="sxs-lookup"><span data-stu-id="9695e-121">Query operators are supported on this service operation endpoint because the method returns an <xref:System.Linq.IQueryable%601> instance.</span></span>

[!code-csharp[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperation)]
[!code-vb[Astoria Northwind Service#ServiceOperation](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperation)]

## <a name="see-also"></a><span data-ttu-id="9695e-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9695e-122">See also</span></span>

- [<span data-ttu-id="9695e-123">Definování datových služeb WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="9695e-123">Defining WCF Data Services</span></span>](defining-wcf-data-services.md)
