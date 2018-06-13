---
title: OMEZENÍ (entita SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: b844c5a132d36a4ca9d660607bbfe0f39ceab718
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759631"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="6c4a0-102">OMEZENÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="6c4a0-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="6c4a0-103">Fyzické stránkování lze provést pomocí dílčí klauzuli LIMIT v klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="6c4a0-104">LIMIT nelze použít samostatně z klauzule ORDER by.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c4a0-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6c4a0-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="6c4a0-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="6c4a0-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="6c4a0-107">Počet položek, které bude možné vybrat.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="6c4a0-108">Pokud dílčí klauzuli LIMIT výrazu nachází v klauzuli ORDER BY, dotaz seřadí podle specifikace řazení a výsledný počet řádků, bude omezený LIMIT výrazem.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="6c4a0-109">Například LIMIT 5 se omezí sadu výsledků do 5 instance nebo řádků.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="6c4a0-110">LIMIT je funkčně srovnatelný horní s tím rozdílem, že LIMIT vyžaduje klauzule ORDER by nacházet.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="6c4a0-111">Přeskočit a LIMIT můžete použít nezávisle klauzule ORDER by.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6c4a0-112">Entity Sql dotazu bude považovat za neplatné, pokud nejvyšší modifikátor a dílčí klauzuli SKIP se nachází ve stejném výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="6c4a0-113">Dotaz by měl být přepsána změnou jako výraz TOP na výrazu omezení.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c4a0-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="6c4a0-114">Example</span></span>  
 <span data-ttu-id="6c4a0-115">Následující dotaz Entity SQL pomocí operátoru Order limit pro určení pořadí řazení použít u objektů, vrátí se v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="6c4a0-116">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6c4a0-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6c4a0-117">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="6c4a0-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6c4a0-118">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6c4a0-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6c4a0-119">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="6c4a0-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="6c4a0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="6c4a0-120">See Also</span></span>  
 [<span data-ttu-id="6c4a0-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="6c4a0-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="6c4a0-122">Postupy: výsledky stránky prostřednictvím dotazu</span><span class="sxs-lookup"><span data-stu-id="6c4a0-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/library/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="6c4a0-123">Stránkování</span><span class="sxs-lookup"><span data-stu-id="6c4a0-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="6c4a0-124">TOP</span><span class="sxs-lookup"><span data-stu-id="6c4a0-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
