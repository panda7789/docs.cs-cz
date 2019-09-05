---
title: BETWEEN (Entity SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: 41036e629837bd5861368df545bed9423eac5b23
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251285"
---
# <a name="between-entity-sql"></a><span data-ttu-id="e8dc1-102">BETWEEN (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="e8dc1-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="e8dc1-103">Určuje, zda výraz má za následek hodnotu v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="e8dc1-104">Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] Between má stejné funkce jako výraz Transact-SQL Between.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8dc1-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e8dc1-105">Syntax</span></span>  
  
```  
expression [ NOT ] BETWEEN begin_expression AND end_expression    
```  
  
## <a name="arguments"></a><span data-ttu-id="e8dc1-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="e8dc1-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="e8dc1-107">Libovolný platný výraz pro otestování v rozsahu definovaném `begin_expression` a. `end_expression`</span><span class="sxs-lookup"><span data-stu-id="e8dc1-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="e8dc1-108">`expression`musí být stejný typ jako i `begin_expression`. `end_expression`</span><span class="sxs-lookup"><span data-stu-id="e8dc1-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="e8dc1-109">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-109">Any valid expression.</span></span> <span data-ttu-id="e8dc1-110">`begin_expression`musí být stejný typ jako i `expression`. `end_expression`</span><span class="sxs-lookup"><span data-stu-id="e8dc1-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="e8dc1-111">`begin_expression`hodnota by měla být `end_expression`menší než, jinak vrácená hodnota bude negace.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="e8dc1-112">Libovolný platný výraz.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-112">Any valid expression.</span></span> <span data-ttu-id="e8dc1-113">`end_expression`musí být stejný typ jako i `expression`. `begin_expression`</span><span class="sxs-lookup"><span data-stu-id="e8dc1-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="e8dc1-114">NOT</span><span class="sxs-lookup"><span data-stu-id="e8dc1-114">NOT</span></span>  
 <span data-ttu-id="e8dc1-115">Určuje, že výsledek mezi je negace.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="e8dc1-116">AND</span><span class="sxs-lookup"><span data-stu-id="e8dc1-116">AND</span></span>  
 <span data-ttu-id="e8dc1-117">Funguje jako zástupný symbol, který `expression` indikuje, že by měl být v `begin_expression` rozsahu `end_expression`uvedeném a.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8dc1-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="e8dc1-118">Return Value</span></span>  
 <span data-ttu-id="e8dc1-119">`true`, `expression` Pokud je mezi rozsahem, `begin_expression` který `end_expression`je určen a `false`; jinak.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="e8dc1-120">`null`Vrátí se, pokud `expression` je `null` , nebo `begin_expression` `end_expression` Pokud`null`je.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e8dc1-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e8dc1-121">Remarks</span></span>  
 <span data-ttu-id="e8dc1-122">Chcete-li určit výhradní rozsah, použijte operátory větší než (>) a menší než (<) místo mezi.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8dc1-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8dc1-123">Example</span></span>  
 <span data-ttu-id="e8dc1-124">Následující Entity SQL dotaz používá operátor BETWEEN k určení, zda výraz má za následek hodnotu v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="e8dc1-125">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="e8dc1-126">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="e8dc1-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="e8dc1-127">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="e8dc1-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="e8dc1-128">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="e8dc1-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="e8dc1-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e8dc1-129">See also</span></span>

- [<span data-ttu-id="e8dc1-130">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e8dc1-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
