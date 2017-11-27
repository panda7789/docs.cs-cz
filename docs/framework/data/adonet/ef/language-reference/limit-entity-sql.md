---
title: "OMEZENÍ (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: c890bf6950f94c04350902276193f5a43239f63f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="limit-entity-sql"></a><span data-ttu-id="3d9f4-102">OMEZENÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="3d9f4-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="3d9f4-103">Fyzické stránkování lze provést pomocí dílčí klauzuli LIMIT v klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="3d9f4-104">LIMIT nelze použít samostatně z klauzule ORDER by.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d9f4-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d9f4-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d9f4-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="3d9f4-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="3d9f4-107">Počet položek, které bude možné vybrat.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="3d9f4-108">Pokud dílčí klauzuli LIMIT výrazu nachází v klauzuli ORDER BY, dotaz seřadí podle specifikace řazení a výsledný počet řádků, bude omezený LIMIT výrazem.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="3d9f4-109">Například LIMIT 5 se omezí sadu výsledků do 5 instance nebo řádků.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="3d9f4-110">LIMIT je funkčně srovnatelný horní s tím rozdílem, že LIMIT vyžaduje klauzule ORDER by nacházet.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="3d9f4-111">Přeskočit a LIMIT můžete použít nezávisle klauzule ORDER by.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d9f4-112">Entity Sql dotazu bude považovat za neplatné, pokud nejvyšší modifikátor a dílčí klauzuli SKIP se nachází ve stejném výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="3d9f4-113">Dotaz by měl být přepsána změnou jako výraz TOP na výrazu omezení.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3d9f4-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d9f4-114">Example</span></span>  
 <span data-ttu-id="3d9f4-115">Následující dotaz Entity SQL pomocí operátoru Order limit pro určení pořadí řazení použít u objektů, vrátí se v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="3d9f4-116">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="3d9f4-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3d9f4-117">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="3d9f4-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="3d9f4-118">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3d9f4-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="3d9f4-119">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="3d9f4-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="3d9f4-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d9f4-120">See Also</span></span>  
 [<span data-ttu-id="3d9f4-121">ŘADIT PODLE</span><span class="sxs-lookup"><span data-stu-id="3d9f4-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="3d9f4-122">Postupy: výsledky stránky prostřednictvím dotazu</span><span class="sxs-lookup"><span data-stu-id="3d9f4-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="3d9f4-123">Stránkování</span><span class="sxs-lookup"><span data-stu-id="3d9f4-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="3d9f4-124">HORNÍ</span><span class="sxs-lookup"><span data-stu-id="3d9f4-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
