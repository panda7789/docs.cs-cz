---
title: "Postupy: vytvoření služby Data pomocí poskytovatele reflexe (služby WCF Data Services)"
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
helpviewer_keywords: WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 343fc6043b4cfc7ea02ff33c18aaaf5ced14c11d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="82ad9-102">Postupy: vytvoření služby Data pomocí poskytovatele reflexe (služby WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="82ad9-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="82ad9-103">Umožňuje definovat datového modelu, který je založen na libovolný třídách tak dlouho, dokud tyto třídy jsou zveřejněné jako objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="82ad9-103"> enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="82ad9-104">Další informace najdete v tématu [zprostředkovatelé dat služby](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="82ad9-104">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="82ad9-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="82ad9-105">Example</span></span>  
 <span data-ttu-id="82ad9-106">V následujícím příkladu definuje datového modelu, který zahrnuje `Orders` a `Items`.</span><span class="sxs-lookup"><span data-stu-id="82ad9-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="82ad9-107">Kontejner – třída entity `OrderItemData` má dvě veřejné metody, které vracejí <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="82ad9-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="82ad9-108">Tato rozhraní jsou sady entit `Orders` a `Items` typy entit.</span><span class="sxs-lookup"><span data-stu-id="82ad9-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="82ad9-109">`Order` Může obsahovat více `Items`, proto `Orders` typ entity má `Items` navigační vlastnost, která vrátí kolekci `Items` objekty.</span><span class="sxs-lookup"><span data-stu-id="82ad9-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="82ad9-110">`OrderItemData` Třídy kontejneru entita je obecný typ <xref:System.Data.Services.DataService%601> třídu, ze které `OrderItems` služba dat je odvozený.</span><span class="sxs-lookup"><span data-stu-id="82ad9-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="82ad9-111">Protože tento příklad ukazuje poskytovatele dat v paměti a změny nejsou trvalé mimo aktuální instance objektů, nepřináší žádný užitek odvozené z implementace <xref:System.Data.Services.IUpdatable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="82ad9-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="82ad9-112">Pro příklad, který implementuje <xref:System.Data.Services.IUpdatable> rozhraní najdete v tématu [postupy: vytvoření službu dat pomocí LINQ to SQL zdroj dat](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span><span class="sxs-lookup"><span data-stu-id="82ad9-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria reflection provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria reflection provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="82ad9-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="82ad9-113">See Also</span></span>  
 [<span data-ttu-id="82ad9-114">Postupy: Vytvoření datové služby pomocí zdroje dat LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="82ad9-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)  
 [<span data-ttu-id="82ad9-115">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="82ad9-115">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)  
 [<span data-ttu-id="82ad9-116">Postupy: Vytvoření datové služby pomocí zdroje dat ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="82ad9-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
