---
title: "PŘÍPAD (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 26a47873-e87d-4ba2-9e2c-3787c21efe89
caps.latest.revision: "5"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 9afc5e3bbf8e6fe732aca9e65c8ba5bd5f620c85
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2018
---
# <a name="case-entity-sql"></a><span data-ttu-id="c9391-102">PŘÍPAD (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="c9391-102">CASE (Entity SQL)</span></span>
<span data-ttu-id="c9391-103">Vyhodnotí sadu `Boolean` výrazy k určení výsledku.</span><span class="sxs-lookup"><span data-stu-id="c9391-103">Evaluates a set of `Boolean` expressions to determine the result.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9391-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c9391-104">Syntax</span></span>  
  
```  
CASE  
     WHEN Boolean_expression THEN result_expression   
    [ ...n ]   
     [   
    ELSE else_result_expression   
     ]   
END  
```  
  
## <a name="arguments"></a><span data-ttu-id="c9391-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="c9391-105">Arguments</span></span>  
 `n`  
 <span data-ttu-id="c9391-106">Je zástupný symbol, který označuje, že více při `Boolean_expression` pak `result_expression` klauzule můžete použít.</span><span class="sxs-lookup"><span data-stu-id="c9391-106">Is a placeholder that indicates that multiple WHEN `Boolean_expression` THEN `result_expression` clauses can be used.</span></span>  
  
 <span data-ttu-id="c9391-107">POTOM`result_expression`</span><span class="sxs-lookup"><span data-stu-id="c9391-107">THEN `result_expression`</span></span>  
 <span data-ttu-id="c9391-108">Výraz dochází při `Boolean_expression` vyhodnocuje `true`.</span><span class="sxs-lookup"><span data-stu-id="c9391-108">Is the expression returned when `Boolean_expression` evaluates to `true`.</span></span> <span data-ttu-id="c9391-109">`result expression`je jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="c9391-109">`result expression` is any valid expression.</span></span>  
  
 <span data-ttu-id="c9391-110">ELSE `else_result_expression`</span><span class="sxs-lookup"><span data-stu-id="c9391-110">ELSE `else_result_expression`</span></span>  
 <span data-ttu-id="c9391-111">Je výraz vrácena, pokud žádná operace porovnání vyhodnocen `true`.</span><span class="sxs-lookup"><span data-stu-id="c9391-111">Is the expression returned if no comparison operation evaluates to `true`.</span></span> <span data-ttu-id="c9391-112">Pokud je tento argument vynechán a žádná operace porovnání se vyhodnocuje `true`, případě vrátí hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="c9391-112">If this argument is omitted and no comparison operation evaluates to `true`, CASE returns null.</span></span> <span data-ttu-id="c9391-113">`else_result_expression`je jakýkoli platný výraz.</span><span class="sxs-lookup"><span data-stu-id="c9391-113">`else_result_expression` is any valid expression.</span></span> <span data-ttu-id="c9391-114">Datové typy `else_result_expression` a jakýkoli `result_expression` musí být stejné nebo musí být implicitní převod.</span><span class="sxs-lookup"><span data-stu-id="c9391-114">The data types of `else_result_expression` and any `result_expression` must be the same or must be an implicit conversion.</span></span>  
  
 <span data-ttu-id="c9391-115">KDY`Boolean_expression`</span><span class="sxs-lookup"><span data-stu-id="c9391-115">WHEN `Boolean_expression`</span></span>  
 <span data-ttu-id="c9391-116">Je `Boolean` výrazu vyhodnoceného při použití vyhledávaná případu formátu.</span><span class="sxs-lookup"><span data-stu-id="c9391-116">Is the `Boolean` expression evaluated when the searched CASE format is used.</span></span> <span data-ttu-id="c9391-117">`Boolean_expression`je libovolný platný `Boolean` výraz.</span><span class="sxs-lookup"><span data-stu-id="c9391-117">`Boolean_expression` is any valid `Boolean` expression.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c9391-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="c9391-118">Return Value</span></span>  
 <span data-ttu-id="c9391-119">Vrátí typ nejvyšší prioritu ze sady typy v `result_expression` a volitelné `else_result_expression`.</span><span class="sxs-lookup"><span data-stu-id="c9391-119">Returns the highest precedence type from the set of types in the `result_expression` and the optional `else_result_expression`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9391-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c9391-120">Remarks</span></span>  
 <span data-ttu-id="c9391-121">[!INCLUDE[esql](../../../../../../includes/esql-md.md)] Případu výraz vypadá takto: [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] případ výraz.</span><span class="sxs-lookup"><span data-stu-id="c9391-121">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] case expression resembles the [!INCLUDE[tsql](../../../../../../includes/tsql-md.md)] case expression.</span></span> <span data-ttu-id="c9391-122">Výraz case použijete k provedení řady podmíněného testů, abyste zjistili, výrazu, který předá odpovídající výsledek.</span><span class="sxs-lookup"><span data-stu-id="c9391-122">You use the case expression to make a series of conditional tests to determine which expression will yield the appropriate result.</span></span> <span data-ttu-id="c9391-123">Tento formulář případu výrazu se vztahují na řadu jeden nebo více `Boolean` výrazy k určení správné výsledný výraz.</span><span class="sxs-lookup"><span data-stu-id="c9391-123">This form of the case expression applies to a series of one or more `Boolean` expressions to determine the correct resulting expression.</span></span>  
  
 <span data-ttu-id="c9391-124">Funkce CASE vyhodnotí `Boolean_expression` pro každou klauzuli WHEN v pořadí zadané a vrátí `result_expression` prvního `Boolean_expression` , jehož výsledkem `true`.</span><span class="sxs-lookup"><span data-stu-id="c9391-124">The CASE function evaluates `Boolean_expression` for each WHEN clause in the order specified, and returns `result_expression` of the first `Boolean_expression` that evaluates to `true`.</span></span> <span data-ttu-id="c9391-125">Zbývající výrazy nejsou vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="c9391-125">The remaining expressions are not evaluated.</span></span> <span data-ttu-id="c9391-126">Pokud žádné `Boolean_expression` vyhodnotí jako `true`, vrátí databázového stroje `else_result_expression` -li zadána klauzule ELSE, nebo hodnotu null, pokud není zadána žádná klauzule ELSE.</span><span class="sxs-lookup"><span data-stu-id="c9391-126">If no `Boolean_expression` evaluates to `true`, the Database Engine returns the `else_result_expression` if an ELSE clause is specified, or a null value if no ELSE clause is specified.</span></span>  
  
 <span data-ttu-id="c9391-127">Příkaz CASE nemůže vrátit multimnožina.</span><span class="sxs-lookup"><span data-stu-id="c9391-127">A CASE statement cannot return a multiset.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9391-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9391-128">Example</span></span>  
 <span data-ttu-id="c9391-129">Následující dotaz Entity SQL používá případu výraz k vyhodnocení sadu `Boolean` výrazy, aby bylo možné zjistit výsledek.</span><span class="sxs-lookup"><span data-stu-id="c9391-129">The following Entity SQL query uses the CASE expression to evaluate a set of `Boolean` expressions in order to determine the result.</span></span> <span data-ttu-id="c9391-130">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="c9391-130">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="c9391-131">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="c9391-131">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="c9391-132">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky PrimitiveType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span><span class="sxs-lookup"><span data-stu-id="c9391-132">Follow the procedure in [How to: Execute a Query that Returns PrimitiveType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-primitivetype-results.md).</span></span>  
  
2.  <span data-ttu-id="c9391-133">Předat jako argument pro následující dotaz `ExecutePrimitiveTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="c9391-133">Pass the following query as an argument to the `ExecutePrimitiveTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#CASE_WHEN_THEN_ELSE](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#case_when_then_else)]  
  
## <a name="see-also"></a><span data-ttu-id="c9391-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9391-134">See Also</span></span>  
 [<span data-ttu-id="c9391-135">THEN</span><span class="sxs-lookup"><span data-stu-id="c9391-135">THEN</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/then-entity-sql.md)  
 [<span data-ttu-id="c9391-136">SELECT</span><span class="sxs-lookup"><span data-stu-id="c9391-136">SELECT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/select-entity-sql.md)  
 [<span data-ttu-id="c9391-137">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="c9391-137">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
