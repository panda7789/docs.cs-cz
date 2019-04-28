---
title: PŘÍPAD (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
ms.openlocfilehash: e44f48d040fc77bf702759be0c53a618cd84f9fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61607190"
---
# <a name="case-entity-sql"></a><span data-ttu-id="dab36-102">PŘÍPAD (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="dab36-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="dab36-103">Vyhodnotí sadu `Boolean` výrazy k určení výsledků.</span><span class="sxs-lookup"><span data-stu-id="dab36-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dab36-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dab36-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="dab36-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="dab36-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="dab36-106">Je zástupný symbol, který označuje, že více při `Boolean_expression` pak `result_expression` klauzule můžete použít.</span><span class="sxs-lookup"><span data-stu-id="dab36-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="dab36-107">POTOM `result_expression`</span><span class="sxs-lookup"><span data-stu-id="dab36-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="dab36-108">Výraz dochází při `Boolean_expression` vyhodnotí jako `true`.</span><span class="sxs-lookup"><span data-stu-id="dab36-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="dab36-109">`result expression` Je libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="dab36-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="dab36-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="dab36-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="dab36-111">Se výraz vrátí, pokud žádná operace porovnání vyhodnocen `true`.</span><span class="sxs-lookup"><span data-stu-id="dab36-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="dab36-112">Pokud je tento argument vynechán a žádná operace porovnání vyhodnocen jako `true`, případě vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="dab36-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="dab36-113">`else_result_expression` Je libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="dab36-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="dab36-114">Datové typy `else_result_expression` a jakékoli `result_expression` musí být stejný nebo musí být proveden implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="dab36-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="dab36-115">KDY `Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="dab36-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="dab36-116">Je `Boolean` výraz vyhodnocen při použití hledaný případu formátu.</span><span class="sxs-lookup"><span data-stu-id="dab36-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="dab36-117">`Boolean_expression` je libovolný platný `Boolean` výrazu.</span><span class="sxs-lookup"><span data-stu-id="dab36-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dab36-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="dab36-118">Return Value</span></span>  
 <span data-ttu-id="dab36-119">Vrátí nejvyšší prioritu typ ze sady typů v `result_expression` a volitelné `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="dab36-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dab36-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dab36-120">Remarks</span></span>  
 <span data-ttu-id="dab36-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Výraz case vypadá podobně jako [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] výraz malá a velká.</span><span class="sxs-lookup"><span data-stu-id="dab36-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="dab36-122">Výraz case můžete provádět řadu podmíněné testů, abyste zjistili výrazu, který předá odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="dab36-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="dab36-123">Tato forma výraz case se vztahuje na řadu jeden nebo více `Boolean` výrazy k určení správné výsledný výraz.</span><span class="sxs-lookup"><span data-stu-id="dab36-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="dab36-124">Funkce CASE se vyhodnotí `Boolean_expression` pro každou klauzuli WHEN v pořadí zadané a vrátí `result_expression` prvního `Boolean_expression` vyhodnocenou nečíselnou `true`.</span><span class="sxs-lookup"><span data-stu-id="dab36-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="dab36-125">Zbývající výrazy se nevyhodnocují.</span><span class="sxs-lookup"><span data-stu-id="dab36-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="dab36-126">Pokud ne `Boolean_expression` vyhodnotí jako `true`, vrátí databázový stroj `else_result_expression` Pokud není zadána klauzule ELSE, nebo hodnotu null, pokud není zadána žádná klauzule ELSE.</span><span class="sxs-lookup"><span data-stu-id="dab36-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="dab36-127">CASE – příkaz nemůže vrátit použita třída multiset.</span><span class="sxs-lookup"><span data-stu-id="dab36-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dab36-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="dab36-128">Example</span></span>  
 <span data-ttu-id="dab36-129">Následující dotaz Entity SQL používá k vyhodnocení sady výraz CASE `Boolean` výrazů, aby bylo možné zjistit výsledek.</span><span class="sxs-lookup"><span data-stu-id="dab36-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="dab36-130">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="dab36-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="dab36-131">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="dab36-131">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="dab36-132">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="dab36-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2. <span data-ttu-id="dab36-133">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="dab36-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="dab36-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dab36-134">See also</span></span>

- [<span data-ttu-id="dab36-135">THEN</span><span class="sxs-lookup"><span data-stu-id="dab36-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)
- [<span data-ttu-id="dab36-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="dab36-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)
- [<span data-ttu-id="dab36-137">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="dab36-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
