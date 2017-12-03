---
title: "Operace služby (služby WCF Data Services)"
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
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 578f62773fc63ac48977116834bb5cd3238050d3
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="service-operations-wcf-data-services"></a><span data-ttu-id="96fc1-102">Operace služby (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="96fc1-102">Service Operations (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="96fc1-103">Umožňuje definovat operace služby ve službě data ke zveřejnění metody na serveru.</span><span class="sxs-lookup"><span data-stu-id="96fc1-103"> enables you to define service operations on a data service to expose methods on the server.</span></span> <span data-ttu-id="96fc1-104">Jako další prostředky služby dat jsou operací služby řešit identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="96fc1-104">Like other data service resources, service operations are addressed by URIs.</span></span> <span data-ttu-id="96fc1-105">Operace služby umožňují vystavit obchodní logiky v datové služby, jako třeba implementovat logiku ověření pro použití na základě rolí zabezpečení, nebo ke zveřejnění specializovaných dotazování možnosti.</span><span class="sxs-lookup"><span data-stu-id="96fc1-105">Service operations enable you to expose business logic in a data service, such as to implement validation logic, to apply role-based security, or to expose specialized querying capabilities.</span></span> <span data-ttu-id="96fc1-106">Operace služby jsou metody přidat k třídě služby data, která je odvozena od <xref:System.Data.Services.DataService%601>.</span><span class="sxs-lookup"><span data-stu-id="96fc1-106">Service operations are methods added to the data service class that derives from <xref:System.Data.Services.DataService%601>.</span></span> <span data-ttu-id="96fc1-107">Podobně jako všechny ostatní datové prostředky služby můžete zadat parametry pro metodu operaci služby.</span><span class="sxs-lookup"><span data-stu-id="96fc1-107">Like all other data service resources, you can supply parameters to the service operation method.</span></span> <span data-ttu-id="96fc1-108">Například následující operace identifikátor URI služby (na základě [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) služba dat) předá hodnotu `London` k `city` parametr:</span><span class="sxs-lookup"><span data-stu-id="96fc1-108">For example, the following service operation URI (based on the [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) data service) passes the value `London` to the `city` parameter:</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 <span data-ttu-id="96fc1-109">Definice pro tuto operaci služby je následující:</span><span class="sxs-lookup"><span data-stu-id="96fc1-109">The definition for this service operation is as follows:</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 <span data-ttu-id="96fc1-110">Můžete použít <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> z <xref:System.Data.Services.DataService%601> přímý přístup k zdroje dat, který používá službu data.</span><span class="sxs-lookup"><span data-stu-id="96fc1-110">You can use the <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> of the <xref:System.Data.Services.DataService%601> to directly access the data source that the data service is using.</span></span> <span data-ttu-id="96fc1-111">Další informace najdete v tématu [postupy: Definování operace služby](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="96fc1-111">For more information, see [How to: Define a Service Operation](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="96fc1-112">Informace o tom, jak volat operace služby z klientské aplikace rozhraní .NET Framework najdete v tématu [volání operací služby](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="96fc1-112">For information on how to call a service operation from a .NET Framework client application, see [Calling Service Operations](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md).</span></span>  
  
## <a name="service-operation-requirements"></a><span data-ttu-id="96fc1-113">Požadavky na operaci služby</span><span class="sxs-lookup"><span data-stu-id="96fc1-113">Service Operation Requirements</span></span>  
 <span data-ttu-id="96fc1-114">Následující požadavky platí při definování operací služby na službu data.</span><span class="sxs-lookup"><span data-stu-id="96fc1-114">The following requirements apply when defining service operations on the data service.</span></span> <span data-ttu-id="96fc1-115">Pokud metoda těchto požadavků nesplňuje, nebude vystavit jako operaci služby pro službu data.</span><span class="sxs-lookup"><span data-stu-id="96fc1-115">If a method does not meet these requirements, it will not be exposed as a service operation for the data service.</span></span>  
  
-   <span data-ttu-id="96fc1-116">Operace musí být veřejné instance metodu, která je členem třídě dat služby.</span><span class="sxs-lookup"><span data-stu-id="96fc1-116">The operation must be a public instance method that is a member of the data service class.</span></span>  
  
-   <span data-ttu-id="96fc1-117">Metoda operace může přijímat pouze vstupní parametry.</span><span class="sxs-lookup"><span data-stu-id="96fc1-117">The operation method may only accept input parameters.</span></span> <span data-ttu-id="96fc1-118">Data odeslaná v textu zprávy nelze přistupovat pomocí služby data.</span><span class="sxs-lookup"><span data-stu-id="96fc1-118">Data sent in the message body cannot be accessed by the data service.</span></span>  
  
-   <span data-ttu-id="96fc1-119">Pokud jsou definovány parametry, musí být typ každý parametr primitivní typ.</span><span class="sxs-lookup"><span data-stu-id="96fc1-119">If parameters are defined, the type of each parameter must be a primitive type.</span></span> <span data-ttu-id="96fc1-120">Žádná data není primitivní typ musí být serializován a předána do parametr řetězce.</span><span class="sxs-lookup"><span data-stu-id="96fc1-120">Any data of a non-primitive type must be serialized and passed into a string parameter.</span></span>  
  
-   <span data-ttu-id="96fc1-121">Metoda musí vrátit jednu z těchto možností:</span><span class="sxs-lookup"><span data-stu-id="96fc1-121">The method must return one of the following:</span></span>  
  
    -   <span data-ttu-id="96fc1-122">`void`(`Nothing` v jazyce Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96fc1-122">`void` (`Nothing` in Visual Basic)</span></span>  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   <span data-ttu-id="96fc1-123">Typ entity v datovém modelu, že data služby vystavuje.</span><span class="sxs-lookup"><span data-stu-id="96fc1-123">An entity type in the data model that the data service exposes.</span></span>  
  
    -   <span data-ttu-id="96fc1-124">Primitivní třída jako celé číslo nebo řetězec.</span><span class="sxs-lookup"><span data-stu-id="96fc1-124">A primitive class such as integer or string.</span></span>  
  
-   <span data-ttu-id="96fc1-125">Kvůli podpoře možnosti dotazu, jako je například řazení, stránkování a filtrování, by měla vrátit operaci metody služeb <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="96fc1-125">In order to support query options such as sorting, paging, and filtering, service operation methods should return <xref:System.Linq.IQueryable%601>.</span></span> <span data-ttu-id="96fc1-126">Požadavky k operacím služby, které zahrnují možnosti dotazu byly zamítnuty pro operace, které vrátit pouze <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="96fc1-126">Requests to service operations that include query options are rejected for operations that only return <xref:System.Collections.Generic.IEnumerable%601>.</span></span>  
  
-   <span data-ttu-id="96fc1-127">Aby bylo možné podporovat, přístup k entit v relaci s použitím navigační vlastnosti, musí vrátit operaci služby <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="96fc1-127">In order to support accessing related entities by using navigation properties, the service operation must return <xref:System.Linq.IQueryable%601>.</span></span>  
  
-   <span data-ttu-id="96fc1-128">Metoda musí být opatřena poznámkou `[WebGet]` nebo `[WebInvoke]` atribut.</span><span class="sxs-lookup"><span data-stu-id="96fc1-128">The method must be annotated with the `[WebGet]` or `[WebInvoke]` attribute.</span></span>  
  
    -   <span data-ttu-id="96fc1-129">`[WebGet]`umožňuje metoda k vyvolání pomocí požadavek GET.</span><span class="sxs-lookup"><span data-stu-id="96fc1-129">`[WebGet]` enables the method to be invoked by using a GET request.</span></span>  
  
    -   <span data-ttu-id="96fc1-130">`[WebInvoke(Method = "POST")]`umožňuje metoda k vyvolání pomocí požadavek POST.</span><span class="sxs-lookup"><span data-stu-id="96fc1-130">`[WebInvoke(Method = "POST")]` enables the method to be invoked by using a POST request.</span></span> <span data-ttu-id="96fc1-131">Další <xref:System.ServiceModel.Web.WebInvokeAttribute> metody nejsou podporovány.</span><span class="sxs-lookup"><span data-stu-id="96fc1-131">Other <xref:System.ServiceModel.Web.WebInvokeAttribute> methods are not supported.</span></span>  
  
-   <span data-ttu-id="96fc1-132">Operace služby, které může být opatřena poznámkou <xref:System.Data.Services.SingleResultAttribute> který určuje, že je vrácená hodnota z metody jedné entity, nikoli kolekci entit.</span><span class="sxs-lookup"><span data-stu-id="96fc1-132">A service operation may be annotated with the <xref:System.Data.Services.SingleResultAttribute> that specifies that the return value from the method is a single entity rather than a collection of entities.</span></span> <span data-ttu-id="96fc1-133">Tento rozdíl určuje výsledný serializaci odpovědi a způsob, ve kterém jsou další navigační vlastnost traversals určený v identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="96fc1-133">This distinction dictates the resulting serialization of the response and the manner in which additional navigation property traversals are represented in the URI.</span></span> <span data-ttu-id="96fc1-134">Například při použití AtomPub serializace, jeden prostředek typ instance reprezentována jako element položky a sady instancí jako element informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="96fc1-134">For example, when using AtomPub serialization, a single resource type instance is represented as an entry element and a set of instances as a feed element.</span></span>  
  
## <a name="addressing-service-operations"></a><span data-ttu-id="96fc1-135">Adresování operací služby</span><span class="sxs-lookup"><span data-stu-id="96fc1-135">Addressing Service Operations</span></span>  
 <span data-ttu-id="96fc1-136">Operace služby můžete vyřešit tak, že název metody první segment cesty identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="96fc1-136">You can address service operations by placing the name of the method in the first path segment of a URI.</span></span> <span data-ttu-id="96fc1-137">Jako příklad následující identifikátor URI přistupuje `GetOrdersByState` operaci, která vrátí <xref:System.Linq.IQueryable%601> kolekce `Orders` objekty.</span><span class="sxs-lookup"><span data-stu-id="96fc1-137">As an example, the following URI accesses a `GetOrdersByState` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects.</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 <span data-ttu-id="96fc1-138">Při volání operace služby, jsou zadány parametry jako možnosti dotazu.</span><span class="sxs-lookup"><span data-stu-id="96fc1-138">When calling a service operation, parameters are supplied as query options.</span></span> <span data-ttu-id="96fc1-139">Předchozí operace služby přijme parametr řetězec `state` a logickým parametrem `includeItems` určující, zda chcete zahrnout související `Order_Detail` objektů v odpovědi.</span><span class="sxs-lookup"><span data-stu-id="96fc1-139">The previous service operation accepts both a string parameter `state` and a Boolean parameter `includeItems` that indicates whether to include related `Order_Detail` objects in the response.</span></span>  
  
 <span data-ttu-id="96fc1-140">Tady jsou platné návratové typy pro operace služby:</span><span class="sxs-lookup"><span data-stu-id="96fc1-140">The following are valid return types for a service operation:</span></span>  
  
|<span data-ttu-id="96fc1-141">Platný návratové typy</span><span class="sxs-lookup"><span data-stu-id="96fc1-141">Valid Return Types</span></span>|<span data-ttu-id="96fc1-142">Identifikátor URI pravidla</span><span class="sxs-lookup"><span data-stu-id="96fc1-142">URI Rules</span></span>|  
|------------------------|---------------|  
|<span data-ttu-id="96fc1-143">`void`(`Nothing` v jazyce Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="96fc1-143">`void` (`Nothing` in Visual Basic)</span></span><br /><br /> <span data-ttu-id="96fc1-144">-nebo-</span><span class="sxs-lookup"><span data-stu-id="96fc1-144">-or-</span></span><br /><br /> <span data-ttu-id="96fc1-145">Typy entit</span><span class="sxs-lookup"><span data-stu-id="96fc1-145">Entity types</span></span><br /><br /> <span data-ttu-id="96fc1-146">-nebo-</span><span class="sxs-lookup"><span data-stu-id="96fc1-146">-or-</span></span><br /><br /> <span data-ttu-id="96fc1-147">Primitivní typy</span><span class="sxs-lookup"><span data-stu-id="96fc1-147">Primitive types</span></span>|<span data-ttu-id="96fc1-148">Identifikátor URI musí být jednou cestou segment, který je název operaci služby.</span><span class="sxs-lookup"><span data-stu-id="96fc1-148">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="96fc1-149">Možnosti dotazu nejsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="96fc1-149">Query options are not allowed.</span></span>|  
|<xref:System.Collections.Generic.IEnumerable%601>|<span data-ttu-id="96fc1-150">Identifikátor URI musí být jednou cestou segment, který je název operaci služby.</span><span class="sxs-lookup"><span data-stu-id="96fc1-150">The URI must be a single path segment that is the name of the service operation.</span></span> <span data-ttu-id="96fc1-151">Protože výsledný typ není <xref:System.Linq.IQueryable%601> typu nejsou povoleny možnosti dotazu.</span><span class="sxs-lookup"><span data-stu-id="96fc1-151">Because the result type is not an <xref:System.Linq.IQueryable%601> type, query options are not allowed.</span></span>|  
|<xref:System.Linq.IQueryable%601>|<span data-ttu-id="96fc1-152">Segmenty cesty dotazu kromě cestu, která je název operace služby jsou povoleny.</span><span class="sxs-lookup"><span data-stu-id="96fc1-152">Query path segments in addition to the path that is the name of the service operation are allowed.</span></span> <span data-ttu-id="96fc1-153">Povolené jsou i možnosti dotazu.</span><span class="sxs-lookup"><span data-stu-id="96fc1-153">Query options are also allowed.</span></span>|  
  
 <span data-ttu-id="96fc1-154">Segmenty cesty další nebo možnosti dotazu mohou být přidány do identifikátoru URI v závislosti na návratový typ operace služby.</span><span class="sxs-lookup"><span data-stu-id="96fc1-154">Additional path segments or query options may be added to the URI depending on the return type of the service operation.</span></span> <span data-ttu-id="96fc1-155">Například následující identifikátor URI přistupuje `GetOrdersByCity` operaci, která vrátí <xref:System.Linq.IQueryable%601> kolekce `Orders` objekty, které jsou seřazené podle `RequiredDate` v sestupném pořadí, společně s související `Order_Details` objekty:</span><span class="sxs-lookup"><span data-stu-id="96fc1-155">For example, the following URI accesses a `GetOrdersByCity` operation that returns an <xref:System.Linq.IQueryable%601> collection of `Orders` objects, ordered by `RequiredDate` in descending order, along with the related `Order_Details` objects:</span></span>  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a><span data-ttu-id="96fc1-156">Řízení přístupu ke službě Operations</span><span class="sxs-lookup"><span data-stu-id="96fc1-156">Service Operations Access Control</span></span>  
 <span data-ttu-id="96fc1-157">Řídí celé služby viditelnost operací služby <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> metodu <xref:System.Data.Services.IDataServiceConfiguration> třída mnohem stejným způsobem, že sada entit viditelnost je řízen pomocí <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="96fc1-157">Service-wide visibility of service operations is controlled by the <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> method on the <xref:System.Data.Services.IDataServiceConfiguration> class in much the same way that entity set visibility is controlled by using the <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> method.</span></span> <span data-ttu-id="96fc1-158">Například následující řádek kódu v definici datové služby umožňuje přístup k `CustomersByCity` operace služby.</span><span class="sxs-lookup"><span data-stu-id="96fc1-158">For example, the following line of code in the data service definition enables access to the `CustomersByCity` service operation.</span></span>  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  <span data-ttu-id="96fc1-159">Operace služby má návratový typ, který je skrytý tak, že omezíte přístup na základní sady entit, operace služby nebudete mít k dispozici pro klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="96fc1-159">If a service operation has a return type that has been hidden by restricting access on the underlying entity sets, then the service operation will not be available to client applications.</span></span>  
  
 <span data-ttu-id="96fc1-160">Další informace najdete v tématu [postupy: Definování operace služby](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="96fc1-160">For more information, see [How to: Define a Service Operation](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md).</span></span>  
  
## <a name="raising-exceptions"></a><span data-ttu-id="96fc1-161">Vyvolávání výjimek</span><span class="sxs-lookup"><span data-stu-id="96fc1-161">Raising Exceptions</span></span>  
 <span data-ttu-id="96fc1-162">Doporučujeme vám, že používáte <xref:System.Data.Services.DataServiceException> třídy vždy, když je vyvolána výjimka při provádění service data.</span><span class="sxs-lookup"><span data-stu-id="96fc1-162">We recommend that you use the <xref:System.Data.Services.DataServiceException> class whenever you raise an exception in the data service execution.</span></span> <span data-ttu-id="96fc1-163">To je proto zná běh služby data mapování vlastnosti tohoto objektu výjimka správně do zprávy s odpovědí HTTP.</span><span class="sxs-lookup"><span data-stu-id="96fc1-163">This is because the data service runtime knows how to map properties of this exception object correctly to the HTTP response message.</span></span> <span data-ttu-id="96fc1-164">Když zvýšíte <xref:System.Data.Services.DataServiceException> v operaci služby vrácený výjimka je zabalené do <xref:System.Reflection.TargetInvocationException>.</span><span class="sxs-lookup"><span data-stu-id="96fc1-164">When you raise a <xref:System.Data.Services.DataServiceException> in a service operation, the returned exception is wrapped in a <xref:System.Reflection.TargetInvocationException>.</span></span> <span data-ttu-id="96fc1-165">Vrátit základní <xref:System.Data.Services.DataServiceException> bez ohraničení <xref:System.Reflection.TargetInvocationException>, je nutné přepsat <xref:System.Data.Services.DataService%601.HandleException%2A> metoda v <xref:System.Data.Services.DataService%601>, rozbalte <xref:System.Data.Services.DataServiceException> z <xref:System.Reflection.TargetInvocationException>a obnoví v něm jako chyba nejvyšší úrovně, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="96fc1-165">To return the base <xref:System.Data.Services.DataServiceException> without the enclosing <xref:System.Reflection.TargetInvocationException>, you must override the <xref:System.Data.Services.DataService%601.HandleException%2A> method in the <xref:System.Data.Services.DataService%601>, extract the <xref:System.Data.Services.DataServiceException> from the <xref:System.Reflection.TargetInvocationException>, and return it as the top-level error, as in the following example:</span></span>  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a><span data-ttu-id="96fc1-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="96fc1-166">See Also</span></span>  
 [<span data-ttu-id="96fc1-167">Sběrače</span><span class="sxs-lookup"><span data-stu-id="96fc1-167">Interceptors</span></span>](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
