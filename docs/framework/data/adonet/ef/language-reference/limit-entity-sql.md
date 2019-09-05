---
title: LIMIT (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c22ffede-0a52-44d1-99b9-4a91e651e1b9
ms.openlocfilehash: 432dfe2c8b2b87daf885be6de4da9bbeaaa37638
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250448"
---
# <a name="limit-entity-sql"></a><span data-ttu-id="306f9-102">LIMIT (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="306f9-102">LIMIT (Entity SQL)</span></span>
<span data-ttu-id="306f9-103">Fyzické stránkování lze provést pomocí dílčí klauzule LIMIT v klauzuli ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="306f9-103">Physical paging can be performed by using LIMIT sub-clause in ORDER BY clause.</span></span> <span data-ttu-id="306f9-104">LIMIT nelze použít odděleně od klauzule ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="306f9-104">LIMIT can not be used separately from ORDER BY clause.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="306f9-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="306f9-105">Syntax</span></span>  
  
```  
[ LIMIT n ]  
```  
  
## <a name="arguments"></a><span data-ttu-id="306f9-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="306f9-106">Arguments</span></span>  
 `n`  
 <span data-ttu-id="306f9-107">Počet položek, které budou vybrány.</span><span class="sxs-lookup"><span data-stu-id="306f9-107">The number of items that will be selected.</span></span>  
  
 <span data-ttu-id="306f9-108">Pokud je dílčí klauzule výrazu omezení přítomna v klauzuli ORDER BY, dotaz se seřadí podle specifikace řazení a výsledný počet řádků bude omezen výrazem LIMIT.</span><span class="sxs-lookup"><span data-stu-id="306f9-108">If a LIMIT expression sub-clause is present in an ORDER BY clause, the query will be sorted according to the sort specification and the resulting number of rows will be restricted by the LIMIT expression.</span></span> <span data-ttu-id="306f9-109">Například omezení 5 omezí výsledek sady výsledků na 5 instancí nebo řádků.</span><span class="sxs-lookup"><span data-stu-id="306f9-109">For instance, LIMIT 5 will restrict the result set to 5 instances or rows.</span></span> <span data-ttu-id="306f9-110">LIMIT je funkčně ekvivalentní k hodnotě TOP s výjimkou, která omezuje omezení vyžaduje, aby klauzule ORDER BY byla k dispozici.</span><span class="sxs-lookup"><span data-stu-id="306f9-110">LIMIT is functionally equivalent to TOP with the exception that LIMIT requires ORDER BY clause to be present.</span></span> <span data-ttu-id="306f9-111">Klauzuli SKIP a LIMIT lze použít nezávisle spolu s klauzulí ORDER BY.</span><span class="sxs-lookup"><span data-stu-id="306f9-111">SKIP and LIMIT can be used independently along with ORDER BY clause.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="306f9-112">Dotaz Entity SQL se považuje za neplatný, pokud je ve stejném výrazu dotazu přítomný modifikátor TOP a SKIP – dílčí klauzule.</span><span class="sxs-lookup"><span data-stu-id="306f9-112">An Entity Sql query will be considered invalid if TOP modifier and SKIP sub-clause is present in the same query expression.</span></span> <span data-ttu-id="306f9-113">Dotaz by měl být přepsán změnou výrazu TOP na výraz omezení.</span><span class="sxs-lookup"><span data-stu-id="306f9-113">The query should be rewritten by changing TOP expression to LIMIT expression.</span></span>  
  
## <a name="example"></a><span data-ttu-id="306f9-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="306f9-114">Example</span></span>  
 <span data-ttu-id="306f9-115">Následující Entity SQL dotaz používá operátor ORDER BY s LIMITem k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="306f9-115">The following Entity SQL query uses the ORDER BY operator with LIMIT to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="306f9-116">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="306f9-116">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="306f9-117">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="306f9-117">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="306f9-118">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="306f9-118">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="306f9-119">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="306f9-119">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#LIMIT](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#limit)]  
  
## <a name="see-also"></a><span data-ttu-id="306f9-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="306f9-120">See also</span></span>

- [<span data-ttu-id="306f9-121">ORDER BY</span><span class="sxs-lookup"><span data-stu-id="306f9-121">ORDER BY</span></span>](order-by-entity-sql.md)
- <span data-ttu-id="306f9-122">[Postupy: Stránka prostřednictvím výsledků dotazu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="306f9-122">[How to: Page Through Query Results](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738702(v=vs.100))</span></span>
- [<span data-ttu-id="306f9-123">Stránkování</span><span class="sxs-lookup"><span data-stu-id="306f9-123">Paging</span></span>](paging-entity-sql.md)
- [<span data-ttu-id="306f9-124">TOP</span><span class="sxs-lookup"><span data-stu-id="306f9-124">TOP</span></span>](top-entity-sql.md)
