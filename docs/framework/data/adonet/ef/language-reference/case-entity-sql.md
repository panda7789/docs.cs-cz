---
title: PŘÍPAD (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 79544f4180313a008669c56c4f2740c889043c6d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251251"
---
# <a name="case-entity-sql"></a><span data-ttu-id="6ff81-102">PŘÍPAD (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6ff81-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="6ff81-103">Vyhodnotí sadu `Boolean` výrazů pro určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="6ff81-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ff81-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ff81-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="6ff81-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6ff81-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="6ff81-106">Je zástupný symbol, který označuje, že `Boolean_expression` lze `result_expression` použít více klauzulí When Then.</span><span class="sxs-lookup"><span data-stu-id="6ff81-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="6ff81-107">STISKNUTÍM`result_expression`</span><span class="sxs-lookup"><span data-stu-id="6ff81-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="6ff81-108">Je výraz vrácený při `Boolean_expression` vyhodnocování. `true`</span><span class="sxs-lookup"><span data-stu-id="6ff81-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="6ff81-109">`result expression`je libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="6ff81-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="6ff81-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="6ff81-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="6ff81-111">Je výraz vrácený, pokud není vyhodnocena `true`žádná operace porovnání.</span><span class="sxs-lookup"><span data-stu-id="6ff81-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="6ff81-112">Pokud je tento argument vynechán a žádná operace porovnání není vyhodnocena `true`jako, vrátí Case hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="6ff81-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="6ff81-113">`else_result_expression`je libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="6ff81-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="6ff81-114">Datové typy `else_result_expression` a Any `result_expression` musí být stejné nebo musí být implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="6ff81-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="6ff81-115">KDY`Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="6ff81-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="6ff81-116">`Boolean` Je výraz vyhodnocen při použití formátu případu hledání.</span><span class="sxs-lookup"><span data-stu-id="6ff81-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="6ff81-117">`Boolean_expression`je libovolný platný `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="6ff81-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ff81-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="6ff81-118">Return Value</span></span>  
 <span data-ttu-id="6ff81-119">Vrátí nejvyšší prioritu typu ze sady typů v `result_expression` a volitelné. `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="6ff81-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ff81-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ff81-120">Remarks</span></span>  
 <span data-ttu-id="6ff81-121">Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Case se podobá výrazu Case Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="6ff81-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="6ff81-122">Výraz Case použijete k vytvoření řady podmíněných testů, které určují, který výraz bude poskytovat odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="6ff81-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="6ff81-123">Tato forma výrazu Case se vztahuje na řadu jednoho nebo více `Boolean` výrazů pro určení správného výsledného výrazu.</span><span class="sxs-lookup"><span data-stu-id="6ff81-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="6ff81-124">Funkce Case vyhodnocuje `Boolean_expression` každou klauzuli when v zadaném pořadí a vrátí `result_expression` `true`první `Boolean_expression` , která je vyhodnocena jako.</span><span class="sxs-lookup"><span data-stu-id="6ff81-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="6ff81-125">Zbývající výrazy nejsou vyhodnocovány.</span><span class="sxs-lookup"><span data-stu-id="6ff81-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="6ff81-126">Pokud není `true`vyhodnocena, databázový stroj vrátí `else_result_expression` klauzuli if, pokud je zadána klauzule else, nebo hodnotu null, pokud není zadána klauzule else. `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="6ff81-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="6ff81-127">Příkaz CASE nemůže vracet multiset.</span><span class="sxs-lookup"><span data-stu-id="6ff81-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ff81-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ff81-128">Example</span></span>  
 <span data-ttu-id="6ff81-129">Následující Entity SQL dotaz používá výraz Case k vyhodnocení sady `Boolean` výrazů za účelem určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="6ff81-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="6ff81-130">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6ff81-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6ff81-131">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="6ff81-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="6ff81-132">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-primitivetype-results.md)PrimitiveType.</span><span class="sxs-lookup"><span data-stu-id="6ff81-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="6ff81-133">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="6ff81-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="6ff81-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ff81-134">See also</span></span>

- [<span data-ttu-id="6ff81-135">THEN</span><span class="sxs-lookup"><span data-stu-id="6ff81-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="6ff81-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="6ff81-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="6ff81-137">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6ff81-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
