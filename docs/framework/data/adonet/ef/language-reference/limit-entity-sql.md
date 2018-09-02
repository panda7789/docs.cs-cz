---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 4534148279ece3b00c45f61c6a35a74a64ca3b6f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406884"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="86766-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="86766-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="86766-103">Fyzické stránkování lze provést pomocí dílčí klauzuli LIMIT v klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="86766-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="86766-104">OMEZENÍ nemůže být použita samostatně z klauzule ORDER by.</span><span class="sxs-lookup"><span data-stu-id="86766-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86766-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86766-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="86766-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="86766-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="86766-107">Počet položek, které bude vybrána.</span><span class="sxs-lookup"><span data-stu-id="86766-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="86766-108">Pokud dílčí klauzuli LIMIT výrazu je přítomna v klauzuli ORDER BY, dotazu budou seřazeny podle specifikace řazení a výsledný počet řádků se omezí výrazu omezení.</span><span class="sxs-lookup"><span data-stu-id="86766-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="86766-109">LIMIT 5, omezí výsledek nastavena na 5 instancí nebo řádků.</span><span class="sxs-lookup"><span data-stu-id="86766-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="86766-110">LIMIT je funkčně srovnatelný s nejvyšší s tím rozdílem, že LIMIT vyžaduje klauzuli ORDER by nacházet.</span><span class="sxs-lookup"><span data-stu-id="86766-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="86766-111">Přeskočit a LIMIT je možné nezávisle na sobě spolu s klauzulí ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="86766-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="86766-112">Dotazu Entity Sql se budou považovat za modifikátor neplatný, pokud je to hlavní a dílčí klauzuli SKIP je k dispozici ve stejném výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="86766-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="86766-113">Dotaz by měl být přepsán změnou výraz TOP na LIMITU výrazu.</span><span class="sxs-lookup"><span data-stu-id="86766-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86766-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="86766-114">Example</span></span>  
 <span data-ttu-id="86766-115">Následující dotaz Entity SQL používá operátor klauzule ORDER BY s LIMITEM k určení pořadí řazení použít u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="86766-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="86766-116">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="86766-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="86766-117">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="86766-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="86766-118">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="86766-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="86766-119">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="86766-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="86766-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="86766-120">See Also</span></span>  
 [<span data-ttu-id="86766-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="86766-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="86766-122">Postupy: výsledky stránky pomocí dotazu</span><span class="sxs-lookup"><span data-stu-id="86766-122">How to: Page Through Query Results</span></span>](https://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="86766-123">Stránkování</span><span class="sxs-lookup"><span data-stu-id="86766-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="86766-124">TOP</span><span class="sxs-lookup"><span data-stu-id="86766-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
