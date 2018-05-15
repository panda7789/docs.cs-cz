---
title: PAK (entita SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: 5f0bbb0cadd736d476077685e08ba1a03b9c4001
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="then-entity-sql"></a><span data-ttu-id="0b0a1-102">PAK (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="0b0a1-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="0b0a1-103">Výsledek klauzuli WHEN vyhodnocení na `true`.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b0a1-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0b0a1-104">Syntax</span></span>  
  
```  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="0b0a1-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="0b0a1-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="0b0a1-106">Platný logický výraz.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="0b0a1-107">Jakýkoli platný dotaz výraz, která vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b0a1-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0b0a1-108">Remarks</span></span>  
 <span data-ttu-id="0b0a1-109">Pokud `when_expression` vyhodnocen jako hodnota `true`, výsledkem je, odpovídající `then-expression`.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="0b0a1-110">Pokud není k dispozici z tím, kdy jsou splněny podmínky, `else-expression` vyhodnotí.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="0b0a1-111">Ale pokud neexistuje žádné `else-expression`, výsledkem je null.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="0b0a1-112">Příklad, naleznete v části [případ](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="0b0a1-112">For an example, see [CASE](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0b0a1-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="0b0a1-113">Example</span></span>  
 <span data-ttu-id="0b0a1-114">Následující dotaz Entity SQL používá případu výraz k vyhodnocení sadu `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="0b0a1-115">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="0b0a1-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="0b0a1-116">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="0b0a1-116">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="0b0a1-117">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="0b0a1-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="0b0a1-118">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="0b0a1-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="0b0a1-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="0b0a1-119">See Also</span></span>  
 [<span data-ttu-id="0b0a1-120">CASE</span><span class="sxs-lookup"><span data-stu-id="0b0a1-120">CASE</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/case-entity-sql.md)  
 [<span data-ttu-id="0b0a1-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="0b0a1-121">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
