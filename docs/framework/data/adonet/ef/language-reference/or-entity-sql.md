---
title: '|| ANI (Entity SQL)'
ms.date: 03/30/2017
ms.assetid: 8e649648-eb9a-4380-9d74-36e62260628c
ms.openlocfilehash: 6437b17fe1c1277701f06988ef6c02f4caf70e62
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319473"
---
# <a name="-or-entity-sql"></a><span data-ttu-id="db6cf-102">|| ANI (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="db6cf-102">|| (OR) (Entity SQL)</span></span>
<span data-ttu-id="db6cf-103">Kombinuje dva výrazy `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="db6cf-103">Combines two `Boolean` expressions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db6cf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db6cf-104">Syntax</span></span>  
  
```sql  
boolean_expression OR boolean_expression  
-- or   
boolean_expression || boolean_expression  
```  
  
## <a name="arguments"></a><span data-ttu-id="db6cf-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="db6cf-105">Arguments</span></span>  
 `boolean_expression`  
 <span data-ttu-id="db6cf-106">Libovolný platný výraz, který vrací `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="db6cf-106">Any valid expression that returns a `Boolean`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db6cf-107">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="db6cf-107">Return Value</span></span>  
 <span data-ttu-id="db6cf-108">`true`, pokud je některá z podmínek `true`; v opačném případě `false`.</span><span class="sxs-lookup"><span data-stu-id="db6cf-108">`true` when either of the conditions is `true`; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="db6cf-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db6cf-109">Remarks</span></span>  
 <span data-ttu-id="db6cf-110">NEBO je logický operátor [!INCLUDE[esql](../../../../../../includes/esql-md.md)].</span><span class="sxs-lookup"><span data-stu-id="db6cf-110">OR is an [!INCLUDE[esql](../../../../../../includes/esql-md.md)] logical operator.</span></span> <span data-ttu-id="db6cf-111">Používá se ke kombinování dvou podmínek.</span><span class="sxs-lookup"><span data-stu-id="db6cf-111">It is used to combine two conditions.</span></span> <span data-ttu-id="db6cf-112">Je-li v příkazu použit více než jeden logický operátor nebo jsou operátory vyhodnoceny po operátoru AND.</span><span class="sxs-lookup"><span data-stu-id="db6cf-112">When more than one logical operator is used in a statement, OR operators are evaluated after AND operators.</span></span> <span data-ttu-id="db6cf-113">Pořadí vyhodnocování však můžete změnit pomocí závorek.</span><span class="sxs-lookup"><span data-stu-id="db6cf-113">However, you can change the order of evaluation by using parentheses.</span></span>  
  
 <span data-ttu-id="db6cf-114">Dvojité svislé čáry (&#124;&#124;) mají stejné funkce jako operátor OR.</span><span class="sxs-lookup"><span data-stu-id="db6cf-114">Double vertical bars (&#124;&#124;) have the same functionality as the OR operator.</span></span>  
  
 <span data-ttu-id="db6cf-115">V následující tabulce jsou uvedeny možné vstupní hodnoty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="db6cf-115">The following table shows possible input values and return types.</span></span>  
  
||`TRUE`|`FALSE`|`NULL`|  
|-|------------|-------------|------------|  
|`TRUE`|<span data-ttu-id="db6cf-116">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="db6cf-116">TRUE</span></span>|<span data-ttu-id="db6cf-117">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="db6cf-117">TRUE</span></span>|<span data-ttu-id="db6cf-118">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="db6cf-118">TRUE</span></span>|  
|`FALSE`|<span data-ttu-id="db6cf-119">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="db6cf-119">TRUE</span></span>|<span data-ttu-id="db6cf-120">CHYBNÉ</span><span class="sxs-lookup"><span data-stu-id="db6cf-120">FALSE</span></span>|<span data-ttu-id="db6cf-121">NULL</span><span class="sxs-lookup"><span data-stu-id="db6cf-121">NULL</span></span>|  
|`NULL`|<span data-ttu-id="db6cf-122">PODMÍNKA</span><span class="sxs-lookup"><span data-stu-id="db6cf-122">TRUE</span></span>|<span data-ttu-id="db6cf-123">NULL</span><span class="sxs-lookup"><span data-stu-id="db6cf-123">NULL</span></span>|<span data-ttu-id="db6cf-124">NULL</span><span class="sxs-lookup"><span data-stu-id="db6cf-124">NULL</span></span>|  
  
## <a name="example"></a><span data-ttu-id="db6cf-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="db6cf-125">Example</span></span>  
 <span data-ttu-id="db6cf-126">Následující Entity SQL dotaz pomocí operátoru OR kombinuje dva výrazy `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="db6cf-126">The following Entity SQL query uses the OR operator to combine two `Boolean` expressions.</span></span> <span data-ttu-id="db6cf-127">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="db6cf-127">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="db6cf-128">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="db6cf-128">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="db6cf-129">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="db6cf-129">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="db6cf-130">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="db6cf-130">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts 2#OR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#or)]  
  
## <a name="see-also"></a><span data-ttu-id="db6cf-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="db6cf-131">See also</span></span>

- [<span data-ttu-id="db6cf-132">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="db6cf-132">Entity SQL Reference</span></span>](entity-sql-reference.md)
