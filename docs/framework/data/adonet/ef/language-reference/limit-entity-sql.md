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
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: f6933c7e3d5b3e7ed5fd4b55974e5869ab83a982
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="limit-entity-sql"></a><span data-ttu-id="4e073-102">OMEZENÍ (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="4e073-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="4e073-103">Fyzické stránkování lze provést pomocí dílčí klauzuli LIMIT v klauzuli ORDER by.</span><span class="sxs-lookup"><span data-stu-id="4e073-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="4e073-104">LIMIT nelze použít samostatně z klauzule ORDER by.</span><span class="sxs-lookup"><span data-stu-id="4e073-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e073-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4e073-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="4e073-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="4e073-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="4e073-107">Počet položek, které bude možné vybrat.</span><span class="sxs-lookup"><span data-stu-id="4e073-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="4e073-108">Pokud dílčí klauzuli LIMIT výrazu nachází v klauzuli ORDER BY, dotaz seřadí podle specifikace řazení a výsledný počet řádků, bude omezený LIMIT výrazem.</span><span class="sxs-lookup"><span data-stu-id="4e073-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="4e073-109">Například LIMIT 5 se omezí sadu výsledků do 5 instance nebo řádků.</span><span class="sxs-lookup"><span data-stu-id="4e073-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="4e073-110">LIMIT je funkčně srovnatelný horní s tím rozdílem, že LIMIT vyžaduje klauzule ORDER by nacházet.</span><span class="sxs-lookup"><span data-stu-id="4e073-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="4e073-111">Přeskočit a LIMIT můžete použít nezávisle klauzule ORDER by.</span><span class="sxs-lookup"><span data-stu-id="4e073-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4e073-112">Entity Sql dotazu bude považovat za neplatné, pokud nejvyšší modifikátor a dílčí klauzuli SKIP se nachází ve stejném výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="4e073-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="4e073-113">Dotaz by měl být přepsána změnou jako výraz TOP na výrazu omezení.</span><span class="sxs-lookup"><span data-stu-id="4e073-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4e073-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="4e073-114">Example</span></span>  
 <span data-ttu-id="4e073-115">Následující dotaz Entity SQL pomocí operátoru Order limit pro určení pořadí řazení použít u objektů, vrátí se v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="4e073-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="4e073-116">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="4e073-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="4e073-117">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="4e073-117">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="4e073-118">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="4e073-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="4e073-119">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="4e073-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="4e073-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="4e073-120">See Also</span></span>  
 [<span data-ttu-id="4e073-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="4e073-121">ORDER BY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/order-by-entity-sql.md)  
 [<span data-ttu-id="4e073-122">Postupy: výsledky stránky prostřednictvím dotazu</span><span class="sxs-lookup"><span data-stu-id="4e073-122">How to: Page Through Query Results</span></span>](http://msdn.microsoft.com/en-us/ffc0f920-e7de-42e0-9b12-ef356421d030)  
 [<span data-ttu-id="4e073-123">Stránkování</span><span class="sxs-lookup"><span data-stu-id="4e073-123">Paging</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/paging-entity-sql.md)  
 [<span data-ttu-id="4e073-124">TOP</span><span class="sxs-lookup"><span data-stu-id="4e073-124">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
