---
title: PAK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: c64e440e8cd8f86706db69d923ba7085d0cb3b3a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70248993"
---
# <a name="then-entity-sql"></a><span data-ttu-id="baba9-102">PAK (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="baba9-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="baba9-103">Výsledek klauzule WHEN při vyhodnocování `true`.</span><span class="sxs-lookup"><span data-stu-id="baba9-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="baba9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="baba9-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="baba9-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="baba9-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="baba9-106">Libovolný platný logický výraz.</span><span class="sxs-lookup"><span data-stu-id="baba9-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="baba9-107">Libovolný platný výraz dotazu, který vrací kolekci.</span><span class="sxs-lookup"><span data-stu-id="baba9-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="baba9-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="baba9-108">Remarks</span></span>  
 <span data-ttu-id="baba9-109">Je `when_expression` -li hodnota vyhodnocena na hodnotu `true`, výsledek je `then-expression`odpovídající.</span><span class="sxs-lookup"><span data-stu-id="baba9-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="baba9-110">Pokud žádné podmínky if nejsou splněné, `else-expression` je vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="baba9-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="baba9-111">Pokud ale ne `else-expression`, výsledek je null.</span><span class="sxs-lookup"><span data-stu-id="baba9-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="baba9-112">Příklad naleznete v tématu [case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="baba9-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="baba9-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="baba9-113">Example</span></span>  
 <span data-ttu-id="baba9-114">Následující Entity SQL dotaz používá výraz Case k vyhodnocení sady `Boolean` výrazů.</span><span class="sxs-lookup"><span data-stu-id="baba9-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="baba9-115">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="baba9-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="baba9-116">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="baba9-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="baba9-117">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="baba9-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="baba9-118">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="baba9-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="baba9-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="baba9-119">See also</span></span>

- [<span data-ttu-id="baba9-120">CASE</span><span class="sxs-lookup"><span data-stu-id="baba9-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="baba9-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="baba9-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
