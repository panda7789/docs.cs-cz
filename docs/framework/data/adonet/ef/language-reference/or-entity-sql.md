---
title: '|| ANI (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: c88e041638fbe6f32717ce9c4f9c2ff6fb56d803
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249763"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="7712f-102">|| ANI (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7712f-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="7712f-103">Kombinuje dva `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="7712f-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7712f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7712f-104">Syntax</span></span>  
  
```  
boolean_expression OR boolean_expression  
or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="7712f-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7712f-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="7712f-106">Libovolný platný výraz, který vrátí `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="7712f-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7712f-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="7712f-107">Return Value</span></span>  
 <span data-ttu-id="7712f-108">`true`Pokud je `true`jedna z podmínek, `false`v opačném případě.</span><span class="sxs-lookup"><span data-stu-id="7712f-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7712f-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7712f-109">Remarks</span></span>  
 <span data-ttu-id="7712f-110">Nebo je [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logický operátor.</span><span class="sxs-lookup"><span data-stu-id="7712f-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="7712f-111">Používá se ke kombinování dvou podmínek.</span><span class="sxs-lookup"><span data-stu-id="7712f-111">It is used to combine two conditions.</span></span> <span data-ttu-id="7712f-112">Je-li v příkazu použit více než jeden logický operátor nebo jsou operátory vyhodnoceny po operátoru AND.</span><span class="sxs-lookup"><span data-stu-id="7712f-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="7712f-113">Pořadí vyhodnocování však můžete změnit pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="7712f-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="7712f-114">Dvojité svislé čáry (&#124;&#124;) mají stejné funkce jako operátor OR.</span><span class="sxs-lookup"><span data-stu-id="7712f-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="7712f-115">V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="7712f-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="7712f-116">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="7712f-116">TRUE</span></span>|<span data-ttu-id="7712f-117">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="7712f-117">TRUE</span></span>|<span data-ttu-id="7712f-118">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="7712f-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="7712f-119">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="7712f-119">TRUE</span></span>|<span data-ttu-id="7712f-120">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="7712f-120">FALSE</span></span>|<span data-ttu-id="7712f-121">NULL</span><span class="sxs-lookup"><span data-stu-id="7712f-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="7712f-122">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="7712f-122">TRUE</span></span>|<span data-ttu-id="7712f-123">NULL</span><span class="sxs-lookup"><span data-stu-id="7712f-123">NULL</span></span>|<span data-ttu-id="7712f-124">NULL</span><span class="sxs-lookup"><span data-stu-id="7712f-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7712f-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="7712f-125">Example</span></span>  
 <span data-ttu-id="7712f-126">Následující Entity SQL dotaz pomocí operátoru OR kombinuje dva `Boolean` výrazy.</span><span class="sxs-lookup"><span data-stu-id="7712f-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="7712f-127">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7712f-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7712f-128">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="7712f-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="7712f-129">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="7712f-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="7712f-130">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="7712f-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#OR](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#or)]  
  
## <a name="see-also"></a><span data-ttu-id="7712f-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7712f-131">See also</span></span>

- [<span data-ttu-id="7712f-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7712f-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
