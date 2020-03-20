---
title: MEZI (Entita SQL)
ms.date: 03/30/2017
ms.assetid: 4dcdd754-ae01-4e78-bf28-8a117fb2b73e
ms.openlocfilehash: a0f5dd19c439861451b1e88c3ae35f9f265288fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150490"
---
# <a name="between-entity-sql"></a><span data-ttu-id="22287-102">MEZI (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="22287-102">BETWEEN (Entity SQL)</span></span>
<span data-ttu-id="22287-103">Určuje, zda má výraz za následek hodnotu v zadaném rozsahu.</span><span class="sxs-lookup"><span data-stu-id="22287-103">Determines whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="22287-104">Výraz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] MEZI má stejné funkce jako výraz Transact-SQL MEZI.</span><span class="sxs-lookup"><span data-stu-id="22287-104">The [!INCLUDE[esql](../../../../../../includes/esql-md.md)] BETWEEN expression has the same functionality as the Transact-SQL BETWEEN expression.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="22287-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="22287-105">Syntax</span></span>  
  
```csharp  
expression [ NOT ] BETWEEN begin_expression AND end_expression
```  
  
## <a name="arguments"></a><span data-ttu-id="22287-106">Argumenty</span><span class="sxs-lookup"><span data-stu-id="22287-106">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="22287-107">Libovolný platný výraz, který chcete `begin_expression` testovat `end_expression`v rozsahu definovaném písmenem a).</span><span class="sxs-lookup"><span data-stu-id="22287-107">Any valid expression to test for in the range defined by `begin_expression` and `end_expression`.</span></span> <span data-ttu-id="22287-108">`expression`musí být stejného `begin_expression` typu `end_expression`jako oba a .</span><span class="sxs-lookup"><span data-stu-id="22287-108">`expression` must be the same type as both `begin_expression` and `end_expression`.</span></span>  
  
 `begin_expression`  
 <span data-ttu-id="22287-109">Libovolný platný výraz</span><span class="sxs-lookup"><span data-stu-id="22287-109">Any valid expression.</span></span> <span data-ttu-id="22287-110">`begin_expression`musí být stejného `expression` typu `end_expression`jako oba a .</span><span class="sxs-lookup"><span data-stu-id="22287-110">`begin_expression` must be the same type as both `expression` and `end_expression`.</span></span> <span data-ttu-id="22287-111">`begin_expression`by měla `end_expression`být menší než , jinak bude vrácená hodnota negována.</span><span class="sxs-lookup"><span data-stu-id="22287-111">`begin_expression` should be less than `end_expression`, else the return value will be negated.</span></span>  
  
 `end_expression`  
 <span data-ttu-id="22287-112">Libovolný platný výraz</span><span class="sxs-lookup"><span data-stu-id="22287-112">Any valid expression.</span></span> <span data-ttu-id="22287-113">`end_expression`musí být stejného `expression` typu `begin_expression`jako oba a .</span><span class="sxs-lookup"><span data-stu-id="22287-113">`end_expression` must be the same type as both `expression` and `begin_expression`.</span></span>  
  
 <span data-ttu-id="22287-114">NOT</span><span class="sxs-lookup"><span data-stu-id="22287-114">NOT</span></span>  
 <span data-ttu-id="22287-115">Určuje, že výsledek between být negována.</span><span class="sxs-lookup"><span data-stu-id="22287-115">Specifies that the result of BETWEEN be negated.</span></span>  
  
 <span data-ttu-id="22287-116">AND</span><span class="sxs-lookup"><span data-stu-id="22287-116">AND</span></span>  
 <span data-ttu-id="22287-117">Funguje jako zástupný `expression` symbol, který označuje by `begin_expression` `end_expression`měl být v rozsahu označeném a .</span><span class="sxs-lookup"><span data-stu-id="22287-117">Acts as a placeholder that indicates `expression` should be within the range indicated by `begin_expression` and `end_expression`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="22287-118">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="22287-118">Return Value</span></span>  
 <span data-ttu-id="22287-119">`true`jestliže `expression` se nachází mezi `begin_expression` `end_expression`rozsahem označeným písmenem a) a b); v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="22287-119">`true` if `expression` is between the range indicated by `begin_expression` and `end_expression`; otherwise, `false`.</span></span> <span data-ttu-id="22287-120">`null`bude vrácena, `null` pokud `begin_expression` `end_expression` `null` `expression` je nebo pokud nebo je .</span><span class="sxs-lookup"><span data-stu-id="22287-120">`null` will be returned if `expression` is `null` or if `begin_expression` or `end_expression` is `null`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="22287-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="22287-121">Remarks</span></span>  
 <span data-ttu-id="22287-122">Chcete-li určit výhradní rozsah, použijte operátory větší než (>) a menší než (<) namísto BETWEEN.</span><span class="sxs-lookup"><span data-stu-id="22287-122">To specify an exclusive range, use the greater than (>) and less than (<) operators instead of BETWEEN.</span></span>  
  
## <a name="example"></a><span data-ttu-id="22287-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="22287-123">Example</span></span>  
 <span data-ttu-id="22287-124">Následující entita SQL dotaz používá operátor MEZI k určení, zda výraz má za následek hodnotu v zadanéoblasti.</span><span class="sxs-lookup"><span data-stu-id="22287-124">The following Entity SQL query uses BETWEEN operator to determine whether an expression results in a value in a specified range.</span></span> <span data-ttu-id="22287-125">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="22287-125">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="22287-126">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="22287-126">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="22287-127">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="22287-127">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="22287-128">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="22287-128">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#BETWEEN](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#between)]  
  
## <a name="see-also"></a><span data-ttu-id="22287-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="22287-129">See also</span></span>

- [<span data-ttu-id="22287-130">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="22287-130">Entity SQL Reference</span></span>](entity-sql-reference.md)
