---
title: "Řazení elementů v pořadí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: d59b93a9-50c8-4770-a114-d902f6a0ea76
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 7a0dd445254d0434fe0825a5da0134084fbddbab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="sort-elements-in-a-sequence"></a><span data-ttu-id="eff9b-102">Řazení elementů v pořadí</span><span class="sxs-lookup"><span data-stu-id="eff9b-102">Sort Elements in a Sequence</span></span>
<span data-ttu-id="eff9b-103">Použití <xref:System.Linq.Enumerable.OrderBy%2A> operátor seřadit pořadí podle jeden či více klíčů.</span><span class="sxs-lookup"><span data-stu-id="eff9b-103">Use the <xref:System.Linq.Enumerable.OrderBy%2A> operator to sort a sequence according to one or more keys.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="eff9b-104">je navržen pro podporu řazení jednoduché primitivní typy, jako například `string`, `int`a tak dále.</span><span class="sxs-lookup"><span data-stu-id="eff9b-104"> is designed to support ordering by simple primitive types, such as `string`, `int`, and so on.</span></span> <span data-ttu-id="eff9b-105">Nepodporuje řazení pro komplexní třídy více hodnot, jako je například anonymní typy.</span><span class="sxs-lookup"><span data-stu-id="eff9b-105">It does not support ordering for complex multi-valued classes, such as anonymous types.</span></span> <span data-ttu-id="eff9b-106">Taky nepodporuje `byte` datové typy.</span><span class="sxs-lookup"><span data-stu-id="eff9b-106">It also does not support `byte` datatypes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eff9b-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff9b-107">Example</span></span>  
 <span data-ttu-id="eff9b-108">Následující příklad seřadí `Employees` data přijetím.</span><span class="sxs-lookup"><span data-stu-id="eff9b-108">The following example sorts `Employees` by date of hire.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#20](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#20)]
 [!code-vb[DLinqQueryExamples#20](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#20)]  
  
## <a name="example"></a><span data-ttu-id="eff9b-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff9b-109">Example</span></span>  
 <span data-ttu-id="eff9b-110">Následující příklad používá `where` seřadit `Orders` odeslaná do `London` podle nákladní.</span><span class="sxs-lookup"><span data-stu-id="eff9b-110">The following example uses `where` to sort `Orders` shipped to `London` by freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#21](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#21)]
 [!code-vb[DLinqQueryExamples#21](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#21)]  
  
## <a name="example"></a><span data-ttu-id="eff9b-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff9b-111">Example</span></span>  
 <span data-ttu-id="eff9b-112">Následující příklad seřadí `Products` jednotky cena od nejvyšší po nejnižší na.</span><span class="sxs-lookup"><span data-stu-id="eff9b-112">The following example sorts `Products` by unit price from highest to lowest.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#22](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#22)]
 [!code-vb[DLinqQueryExamples#22](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#22)]  
  
## <a name="example"></a><span data-ttu-id="eff9b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff9b-113">Example</span></span>  
 <span data-ttu-id="eff9b-114">Následující příklad používá složené `OrderBy` seřadit `Customers` podle města a poté podle jméno kontaktní osoby.</span><span class="sxs-lookup"><span data-stu-id="eff9b-114">The following example uses a compound `OrderBy` to sort `Customers` by city and then by contact name.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#24](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#24)]
 [!code-vb[DLinqQueryExamples#24](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#24)]  
  
## <a name="example"></a><span data-ttu-id="eff9b-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff9b-115">Example</span></span>  
 <span data-ttu-id="eff9b-116">Následující příklad seřadí objednávky z `EmployeeID 1` podle země příjemce a poté podle nejvyšší po nejnižší nákladní.</span><span class="sxs-lookup"><span data-stu-id="eff9b-116">The following example sorts Orders from `EmployeeID 1` by ship-to country, and then by highest to lowest freight.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#25](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#25)]
 [!code-vb[DLinqQueryExamples#25](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#25)]  
  
## <a name="example"></a><span data-ttu-id="eff9b-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="eff9b-117">Example</span></span>  
 <span data-ttu-id="eff9b-118">Následující příklad kombinuje <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, a <xref:System.Linq.Enumerable.GroupBy%2A> operátory najít `Products` , mít nejvyšší jednotkové ceny v každé kategorii a pak seřadí podle kategorie id skupiny.</span><span class="sxs-lookup"><span data-stu-id="eff9b-118">The following example combines <xref:System.Linq.Enumerable.OrderBy%2A>, <xref:System.Linq.Enumerable.Max%2A>, and <xref:System.Linq.Enumerable.GroupBy%2A> operators to find the `Products` that have the highest unit price in each category, and then sorts the group by category id.</span></span>  
  
 [!code-csharp[DLinqQueryExamples#26](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqQueryExamples/cs/Program.cs#26)]
 [!code-vb[DLinqQueryExamples#26](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqQueryExamples/vb/Module1.vb#26)]  
  
 <span data-ttu-id="eff9b-119">Pokud spustíte předchozí dotaz proti ukázková databáze Northwind, výsledky budou vypadat takto:</span><span class="sxs-lookup"><span data-stu-id="eff9b-119">If you run the previous query against the Northwind sample database, the results will resemble the following:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eff9b-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="eff9b-120">See Also</span></span>  
 [<span data-ttu-id="eff9b-121">Příklady dotazů</span><span class="sxs-lookup"><span data-stu-id="eff9b-121">Query Examples</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/query-examples.md)  
 [<span data-ttu-id="eff9b-122">Stažení ukázkových databází</span><span class="sxs-lookup"><span data-stu-id="eff9b-122">Downloading Sample Databases</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md)
