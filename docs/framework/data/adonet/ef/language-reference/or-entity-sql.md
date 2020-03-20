---
title: '|| (NEBO) (Entita SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 8c93e68095a0e0ff63532f53152f166d6c3d047c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150090"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="2b550-102">|| (NEBO) (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="2b550-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="2b550-103">Kombinuje dva `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="2b550-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b550-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2b550-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="2b550-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="2b550-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="2b550-106">Libovolný platný výraz, `Boolean`který vrací .</span><span class="sxs-lookup"><span data-stu-id="2b550-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2b550-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="2b550-107">Return Value</span></span>  
 <span data-ttu-id="2b550-108">`true`pokud je `true`některá z podmínek ; v `false`opačném případě .</span><span class="sxs-lookup"><span data-stu-id="2b550-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b550-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2b550-109">Remarks</span></span>  
 <span data-ttu-id="2b550-110">NEBO je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logický operátor.</span><span class="sxs-lookup"><span data-stu-id="2b550-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="2b550-111">Používá se ke kombinaci dvou podmínek.</span><span class="sxs-lookup"><span data-stu-id="2b550-111">It is used to combine two conditions.</span></span> <span data-ttu-id="2b550-112">Pokud je v příkazu použito více než jeden logický operátor, operátory OR jsou vyhodnoceny po operátorech AND.</span><span class="sxs-lookup"><span data-stu-id="2b550-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="2b550-113">Pořadí hodnocení však můžete změnit pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="2b550-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="2b550-114">Dvojité svislé pruhy (&#124;&#124;) mají stejné funkce jako operátor OR.</span><span class="sxs-lookup"><span data-stu-id="2b550-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="2b550-115">V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="2b550-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="2b550-116">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b550-116">TRUE</span></span>|<span data-ttu-id="2b550-117">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b550-117">TRUE</span></span>|<span data-ttu-id="2b550-118">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b550-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="2b550-119">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b550-119">TRUE</span></span>|<span data-ttu-id="2b550-120">FALSE</span><span class="sxs-lookup"><span data-stu-id="2b550-120">FALSE</span></span>|<span data-ttu-id="2b550-121">NULL</span><span class="sxs-lookup"><span data-stu-id="2b550-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="2b550-122">TRUE</span><span class="sxs-lookup"><span data-stu-id="2b550-122">TRUE</span></span>|<span data-ttu-id="2b550-123">NULL</span><span class="sxs-lookup"><span data-stu-id="2b550-123">NULL</span></span>|<span data-ttu-id="2b550-124">NULL</span><span class="sxs-lookup"><span data-stu-id="2b550-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="2b550-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2b550-125">Example</span></span>  
 <span data-ttu-id="2b550-126">Následující dotaz ENTITY SQL používá operátor `Boolean` OR ke sloučení dvou výrazů.</span><span class="sxs-lookup"><span data-stu-id="2b550-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="2b550-127">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="2b550-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="2b550-128">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="2b550-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="2b550-129">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="2b550-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="2b550-130">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="2b550-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="2b550-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="2b550-131">See also</span></span>

- [<span data-ttu-id="2b550-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="2b550-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
