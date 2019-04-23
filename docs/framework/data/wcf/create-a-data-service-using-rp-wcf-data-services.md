---
title: 'Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: 233b17de17b7f50547b2f4fbf6a543d7258183cf
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517093"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="ae7cc-102">Postupy: Vytvoření datové služby pomocí zprostředkovatel reflexe (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="ae7cc-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] <span data-ttu-id="ae7cc-103">Umožňuje definovat datový model, který je založen na libovolné třídy tak dlouho, dokud tyto třídy jsou vystaveny jako objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="ae7cc-104">Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="ae7cc-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ae7cc-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="ae7cc-105">Example</span></span>  
 <span data-ttu-id="ae7cc-106">Následující příklad definuje datový model, který zahrnuje `Orders` a `Items`.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="ae7cc-107">Třída kontejneru entity `OrderItemData` má dvě veřejné metody, které vracejí <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="ae7cc-108">Tato rozhraní jsou sady entit `Orders` a `Items` typy entit.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="ae7cc-109">`Order` Může obsahovat více `Items`, takže `Orders` má typ entity `Items` vlastnost navigace, která vrátí kolekci `Items` objekty.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="ae7cc-110">`OrderItemData` Třída kontejneru entity je obecný typ <xref:System.Data.Services.DataService%601> třídu, ze které `OrderItems` datové služby je odvozený.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ae7cc-111">Protože tento příklad ukazuje poskytovatele dat v paměti a nejsou trvalé změny mimo aktuální instance objektů, neexistuje žádný přínos odvozen od implementace <xref:System.Data.Services.IUpdatable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="ae7cc-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="ae7cc-112">Příklad, který implementuje <xref:System.Data.Services.IUpdatable> rozhraní najdete v tématu [jak: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="ae7cc-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="ae7cc-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ae7cc-113">See also</span></span>

- [<span data-ttu-id="ae7cc-114">Postupy: Vytvoření datové služby pomocí LINQ ke zdroji dat SQL</span><span class="sxs-lookup"><span data-stu-id="ae7cc-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="ae7cc-115">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="ae7cc-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="ae7cc-116">Postupy: Vytvoření datové služby pomocí zdroje dat rozhraní ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ae7cc-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
