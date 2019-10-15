---
title: PAK (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 54222642-23c6-4f61-9861-67caca53ac5f
ms.openlocfilehash: ba01a978c53b58f7e6c1ac9bc42a97277ac64bbc
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319287"
---
# <a name="then-entity-sql"></a><span data-ttu-id="af447-102">PAK (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="af447-102">THEN (Entity SQL)</span></span>
<span data-ttu-id="af447-103">Výsledek klauzule WHEN, když se vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="af447-103">The result of a WHEN clause when it evaluates to `true`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="af447-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="af447-104">Syntax</span></span>  
  
```sql  
WHEN when_expression THEN then_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="af447-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="af447-105">Arguments</span></span>  
 `when_expression`  
 <span data-ttu-id="af447-106">Libovolný platný logický výraz.</span><span class="sxs-lookup"><span data-stu-id="af447-106">Any valid Boolean expression.</span></span>  
  
 `then_expression`  
 <span data-ttu-id="af447-107">Libovolný platný výraz dotazu, který vrací kolekci.</span><span class="sxs-lookup"><span data-stu-id="af447-107">Any valid query expression that returns a collection.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="af447-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="af447-108">Remarks</span></span>  
 <span data-ttu-id="af447-109">Pokud `when_expression` se vyhodnotí na hodnotu `true`, výsledkem bude odpovídající `then-expression`.</span><span class="sxs-lookup"><span data-stu-id="af447-109">If `when_expression` evaluates to the value `true`, the result is the corresponding `then-expression`.</span></span> <span data-ttu-id="af447-110">Pokud žádné podmínky if nejsou splněné, je vyhodnocena hodnota `else-expression`.</span><span class="sxs-lookup"><span data-stu-id="af447-110">If none of the WHEN conditions are satisfied, the `else-expression` is evaluated.</span></span> <span data-ttu-id="af447-111">Pokud však není `else-expression`, výsledkem je hodnota null.</span><span class="sxs-lookup"><span data-stu-id="af447-111">However, if there is no `else-expression`, the result is null.</span></span>  
  
 <span data-ttu-id="af447-112">Příklad naleznete v tématu [case](case-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="af447-112">For an example, see [CASE](case-entity-sql.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="af447-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="af447-113">Example</span></span>  
 <span data-ttu-id="af447-114">Následující Entity SQL dotaz používá výraz CASE k vyhodnocení sady výrazů `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="af447-114">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions.</span></span> <span data-ttu-id="af447-115">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="af447-115">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="af447-116">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="af447-116">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="af447-117">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="af447-117">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="af447-118">Předat následující dotaz jako argument metodě `ExecutePrimitiveTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="af447-118">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#CASE_WHEN_THEN_ELSE](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="af447-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="af447-119">See also</span></span>

- [<span data-ttu-id="af447-120">CASE</span><span class="sxs-lookup"><span data-stu-id="af447-120">CASE</span></span>](case-entity-sql.md)
- [<span data-ttu-id="af447-121">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="af447-121">Entity SQL Reference</span></span>](entity-sql-reference.md)
