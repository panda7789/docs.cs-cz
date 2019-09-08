---
title: 'Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, providers
ms.assetid: 7315c6d8-f452-4fb2-a0c1-76ab0593c146
ms.openlocfilehash: feee679c37cd3dafb80021752ee25444c54f0809
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70791007"
---
# <a name="how-to-create-a-data-service-using-the-reflection-provider-wcf-data-services"></a><span data-ttu-id="8c586-102">Postupy: Vytvoření datové služby pomocí zprostředkovatele reflexe (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8c586-102">How to: Create a Data Service Using the Reflection Provider (WCF Data Services)</span></span>
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]<span data-ttu-id="8c586-103">umožňuje definovat datový model, který je založen na libovolných třídách, pokud jsou tyto třídy vystaveny jako objekty, které implementují <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c586-103">enables you to define a data model that is based on arbitrary classes as long as those classes are exposed as objects that implement the <xref:System.Linq.IQueryable%601> interface.</span></span> <span data-ttu-id="8c586-104">Další informace najdete v tématu [poskytovatelé Data Services](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8c586-104">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c586-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c586-105">Example</span></span>  
 <span data-ttu-id="8c586-106">Následující příklad definuje datový model, který obsahuje `Orders` a. `Items`</span><span class="sxs-lookup"><span data-stu-id="8c586-106">The following example defines a data model that includes `Orders` and `Items`.</span></span> <span data-ttu-id="8c586-107">Třída `OrderItemData` kontejneru entity má dvě veřejné metody, které vracejí <xref:System.Linq.IQueryable%601> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c586-107">The entity container class `OrderItemData` has two public methods that return <xref:System.Linq.IQueryable%601> interfaces.</span></span> <span data-ttu-id="8c586-108">Tato rozhraní jsou sady `Orders` entit typů entit a. `Items`</span><span class="sxs-lookup"><span data-stu-id="8c586-108">These interfaces are the entity sets of the `Orders` and `Items` entity types.</span></span> <span data-ttu-id="8c586-109">`Items` `Orders` `Items` Může obsahovat více, takže typ entity má vlastnost navigace, která vrací kolekci `Items` objektů. `Order`</span><span class="sxs-lookup"><span data-stu-id="8c586-109">An `Order` can include multiple `Items`, so the `Orders` entity type has an `Items` navigation property that returns a collection of `Items` objects.</span></span> <span data-ttu-id="8c586-110">Třída kontejneru <xref:System.Data.Services.DataService%601> entityje`OrderItems` obecný typ třídy, ze které je datová služba odvozena. `OrderItemData`</span><span class="sxs-lookup"><span data-stu-id="8c586-110">The `OrderItemData` entity container class is the generic type of the <xref:System.Data.Services.DataService%601> class from which the `OrderItems` data service is derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8c586-111">Vzhledem k tomu, že tento příklad ukazuje poskytovatele dat v paměti a změny nejsou zachovány mimo aktuální instance objektů, není implementováno žádné výhody odvozené od implementace <xref:System.Data.Services.IUpdatable> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8c586-111">Because this example demonstrates an in-memory data provider and changes are not persisted outside of the current object instances, there is no benefit derived from implementing the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="8c586-112">Příklad, který implementuje <xref:System.Data.Services.IUpdatable> rozhraní, naleznete v tématu [How to: Vytvořte datovou službu pomocí LINQ to SQL zdroje](create-a-data-service-using-linq-to-sql-wcf.md)dat.</span><span class="sxs-lookup"><span data-stu-id="8c586-112">For an example that implements the <xref:System.Data.Services.IUpdatable> interface, see [How to: Create a Data Service Using a LINQ to SQL Data Source](create-a-data-service-using-linq-to-sql-wcf.md).</span></span>  
  
 [!code-csharp[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_reflection_provider/cs/orderitems.svc.cs#customiqueryable)]
 [!code-vb[Astoria Reflection Provider#CustomIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_reflection_provider/vb/orderitems.svc.vb#customiqueryable)]  
  
## <a name="see-also"></a><span data-ttu-id="8c586-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c586-113">See also</span></span>

- [<span data-ttu-id="8c586-114">Postupy: Vytvoření datové služby pomocí LINQ to SQL zdroje dat</span><span class="sxs-lookup"><span data-stu-id="8c586-114">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
- [<span data-ttu-id="8c586-115">Zprostředkovatelé datových služeb</span><span class="sxs-lookup"><span data-stu-id="8c586-115">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="8c586-116">Postupy: Vytvoření datové služby pomocí zdroje dat Entity Framework ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8c586-116">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
