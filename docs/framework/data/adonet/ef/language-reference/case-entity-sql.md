---
title: CASE (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: 58b21d3be8e13a0a2204a4fd6d355f734207c509
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150464"
---
# <a name="case-entity-sql"></a><span data-ttu-id="45f07-102">CASE (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="45f07-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="45f07-103">Vyhodnotí sadu `Boolean` výrazů k určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="45f07-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f07-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="45f07-104">Syntax</span></span>  
  
```csharp  
CASE  
     WHEN Boolean_expression THEN result_expression
    [ ...n ]
     [
    ELSE else_result_expression
     ]
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="45f07-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="45f07-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="45f07-106">Je zástupný symbol, který `Boolean_expression` `result_expression` označuje, že lze použít více klauzulí WHEN THEN.</span><span class="sxs-lookup"><span data-stu-id="45f07-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="45f07-107">Pak`result_expression`</span><span class="sxs-lookup"><span data-stu-id="45f07-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="45f07-108">Je výraz vrácena `Boolean_expression` při `true`vyhodnocuje na .</span><span class="sxs-lookup"><span data-stu-id="45f07-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="45f07-109">`result expression`je libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="45f07-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="45f07-110">Jiného`else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="45f07-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="45f07-111">Je výraz vrácena, pokud žádná `true`operace porovnání vyhodnotí .</span><span class="sxs-lookup"><span data-stu-id="45f07-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="45f07-112">Pokud je tento argument vynechán a žádná `true`operace porovnání vyhodnocena na , funkce CASE vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="45f07-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="45f07-113">`else_result_expression`je libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="45f07-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="45f07-114">Datové typy `else_result_expression` a `result_expression` všechny musí být stejné nebo musí být implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="45f07-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="45f07-115">Kdy`Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="45f07-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="45f07-116">Je `Boolean` výraz vyhodnocen při použití prohledávaná case formát.</span><span class="sxs-lookup"><span data-stu-id="45f07-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="45f07-117">`Boolean_expression`je libovolný `Boolean` platný výraz.</span><span class="sxs-lookup"><span data-stu-id="45f07-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45f07-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="45f07-118">Return Value</span></span>  
 <span data-ttu-id="45f07-119">Vrátí nejvyšší typ priority ze sady typů `result_expression` v `else_result_expression`a volitelné .</span><span class="sxs-lookup"><span data-stu-id="45f07-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45f07-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45f07-120">Remarks</span></span>  
 <span data-ttu-id="45f07-121">Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] případu se podobá výrazu případu Transact-SQL.</span><span class="sxs-lookup"><span data-stu-id="45f07-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the Transact-SQL case expression.</span></span> <span data-ttu-id="45f07-122">Výraz případu slouží k vytvoření řady podmíněných testů k určení, který výraz přinese odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="45f07-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="45f07-123">Tato forma výrazu case se vztahuje na `Boolean` řadu jednoho nebo více výrazů k určení správného výsledného výrazu.</span><span class="sxs-lookup"><span data-stu-id="45f07-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="45f07-124">Funkce CASE `Boolean_expression` vyhodnotí pro každou klauzuli WHEN `result_expression` v `Boolean_expression` zadaném pořadí `true`a vrátí první, která je vyhodnocena .</span><span class="sxs-lookup"><span data-stu-id="45f07-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="45f07-125">Zbývající výrazy nejsou vyhodnoceny.</span><span class="sxs-lookup"><span data-stu-id="45f07-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="45f07-126">Pokud `Boolean_expression` žádné vyhodnotí `true`, databázový stroj vrátí `else_result_expression` pokud else klauzule je zadána nebo null hodnotu, pokud není zadána žádná klauzule ELSE.</span><span class="sxs-lookup"><span data-stu-id="45f07-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="45f07-127">Příkaz CASE nemůže vrátit vícesetovou sadu.</span><span class="sxs-lookup"><span data-stu-id="45f07-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f07-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="45f07-128">Example</span></span>  
 <span data-ttu-id="45f07-129">Následující dotaz ENTITY SQL používá výraz CASE `Boolean` k vyhodnocení sady výrazů za účelem určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="45f07-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="45f07-130">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="45f07-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="45f07-131">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="45f07-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="45f07-132">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu PrimitiveType](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="45f07-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="45f07-133">Předat následující dotaz jako argument `ExecutePrimitiveTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="45f07-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="45f07-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="45f07-134">See also</span></span>

- [<span data-ttu-id="45f07-135">Pak</span><span class="sxs-lookup"><span data-stu-id="45f07-135">THEN</span></span>](then-entity-sql.md)
- [<span data-ttu-id="45f07-136">Vyberte</span><span class="sxs-lookup"><span data-stu-id="45f07-136">SELECT</span></span>](select-entity-sql.md)
- [<span data-ttu-id="45f07-137">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="45f07-137">Entity SQL Reference</span></span>](entity-sql-reference.md)
