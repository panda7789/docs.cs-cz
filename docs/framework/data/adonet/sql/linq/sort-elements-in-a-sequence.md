---
title: Řazení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: 33473eadefabc2bcbbb552d225d021eae4bed0bb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169010"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="dc359-102">Řazení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="dc359-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="dc359-103">Použití <xref:System.Linq.Enumerable.OrderBy%2A> operátor seřadit řady podle jednoho nebo více klíčů.</span><span class="sxs-lookup"><span data-stu-id="dc359-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="dc359-104">je navržena pro podporu řazení podle jednoduchých primitivní typy, jako například `string`, `int`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="dc359-104">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="dc359-105">Nepodporuje řazení pro komplexní více Vážíme si toho třídy, jako je například anonymních typů.</span><span class="sxs-lookup"><span data-stu-id="dc359-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="dc359-106">Také nepodporuje `byte` datové typy.</span><span class="sxs-lookup"><span data-stu-id="dc359-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc359-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc359-107">Example</span></span>  
 <span data-ttu-id="dc359-108">Následující příklad řadí `Employees` podle data přijetím.</span><span class="sxs-lookup"><span data-stu-id="dc359-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="dc359-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc359-109">Example</span></span>  
 <span data-ttu-id="dc359-110">V následujícím příkladu `where` seřadíte `Orders` dodáno `London` podle přístavů.</span><span class="sxs-lookup"><span data-stu-id="dc359-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="dc359-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc359-111">Example</span></span>  
 <span data-ttu-id="dc359-112">Následující příklad řadí `Products` jednotky cena od nejvyšší k nejnižší.</span><span class="sxs-lookup"><span data-stu-id="dc359-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="dc359-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc359-113">Example</span></span>  
 <span data-ttu-id="dc359-114">V následujícím příkladu složeného `OrderBy` seřadíte `Customers` podle města a pak podle jméno kontaktní osoby.</span><span class="sxs-lookup"><span data-stu-id="dc359-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="dc359-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc359-115">Example</span></span>  
 <span data-ttu-id="dc359-116">Následující příklad řadí objednávky z `EmployeeID 1` podle země příjemce a pak podle nejvyšší po nejnižší přístavů.</span><span class="sxs-lookup"><span data-stu-id="dc359-116">The following example sorts Orders from `EmployeeID 1` by ship-to country, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="dc359-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="dc359-117">Example</span></span>  
 <span data-ttu-id="dc359-118">Následující příklad kombinuje <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, a <xref:System.Linq.Enumerable.GroupBy%2A> operátory najít `Products` , které mají nejvyšší cena za jednotku v jednotlivých kategoriích a pak Seřadí skupiny podle id kategorie.</span><span class="sxs-lookup"><span data-stu-id="dc359-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="dc359-119">Pokud spouštíte skript v ukázkové databázi Northwind předchozí dotaz, výsledky budou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="dc359-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
 `1`  
  
 `Côte de Blaye`  
  
 `2`  
  
 `Vegie-spread`  
  
 `3`  
  
 `Sir Rodney's Marmalade`  
  
 `4`  
  
 `Raclette Courdavault`  
  
 `5`  
  
 `Gnocchi di nonna Alice`  
  
 `6`  
  
 `Thüringer Rostbratwurst`  
  
 `7`  
  
 `Manjimup Dried Apples`  
  
 `8`  
  
 `Carnarvon Tigers`  
  
## <a name="see-also"></a><span data-ttu-id="dc359-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dc359-120">See also</span></span>

- [<span data-ttu-id="dc359-121">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="dc359-121">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="dc359-122">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="dc359-122">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
