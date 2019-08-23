---
title: Řazení prvků v posloupnosti
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
ms.openlocfilehash: f6f112a63dd976a1d6ae91f2fafd6678a9f40846
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945094"
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="8d261-102">Řazení prvků v posloupnosti</span><span class="sxs-lookup"><span data-stu-id="8d261-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="8d261-103"><xref:System.Linq.Enumerable.OrderBy%2A> Použijte operátor pro řazení pořadí podle jednoho nebo více klíčů.</span><span class="sxs-lookup"><span data-stu-id="8d261-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
> [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="8d261-104">je navržena pro podporu řazení podle jednoduchých primitivních typů, `string`například `int`, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="8d261-104">is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="8d261-105">Nepodporuje řazení složitých tříd s více hodnotami, jako jsou například anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="8d261-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="8d261-106">Nepodporuje také `byte` typy DataTypes.</span><span class="sxs-lookup"><span data-stu-id="8d261-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d261-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d261-107">Example</span></span>  
 <span data-ttu-id="8d261-108">Následující příklad seřadí `Employees` podle data přijetí.</span><span class="sxs-lookup"><span data-stu-id="8d261-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="8d261-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d261-109">Example</span></span>  
 <span data-ttu-id="8d261-110">Následující příklad používá `where` k řazení `Orders` expedovaného do `London` dopravného.</span><span class="sxs-lookup"><span data-stu-id="8d261-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="8d261-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d261-111">Example</span></span>  
 <span data-ttu-id="8d261-112">Následující příklad seřadí `Products` podle jednotkové ceny od nejvyšší po nejnižší.</span><span class="sxs-lookup"><span data-stu-id="8d261-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="8d261-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d261-113">Example</span></span>  
 <span data-ttu-id="8d261-114">Následující příklad používá složené `OrderBy` pro řazení `Customers` podle města a potom podle jména kontaktu.</span><span class="sxs-lookup"><span data-stu-id="8d261-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="8d261-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d261-115">Example</span></span>  
 <span data-ttu-id="8d261-116">Následující příklad seřadí objednávky od `EmployeeID 1` z `ShipCountry`a pak podle nejvyšších po nejnižší dopravného.</span><span class="sxs-lookup"><span data-stu-id="8d261-116">The following example sorts Orders from `EmployeeID 1` by `ShipCountry`, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="8d261-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d261-117">Example</span></span>  
 <span data-ttu-id="8d261-118">Následující příklad kombinuje <xref:System.Linq.Enumerable.OrderBy%2A>operátory, <xref:System.Linq.Enumerable.Max%2A> <xref:System.Linq.Enumerable.GroupBy%2A> aknalezenínejvyššíjednotkovécenyvkaždékategoriianásledněseřadíseskupenípodleIDkategorie.`Products`</span><span class="sxs-lookup"><span data-stu-id="8d261-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="8d261-119">Pokud spustíte předchozí dotaz na ukázkovou databázi Northwind, výsledky budou vypadat přibližně takto:</span><span class="sxs-lookup"><span data-stu-id="8d261-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d261-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d261-120">See also</span></span>

- [<span data-ttu-id="8d261-121">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="8d261-121">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)
- [<span data-ttu-id="8d261-122">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="8d261-122">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
