---
title: "Řadit podle (entita SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e4ef6edfc56fe73cd509d466fcc26cdb24069c9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="7d9da-102">Řadit podle (entita SQL)</span><span class="sxs-lookup"><span data-stu-id="7d9da-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="7d9da-103">Určuje pořadí řazení použít u objektů, vrátí se v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="7d9da-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d9da-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d9da-104">Syntax</span></span>  
  
```  
[ ORDER BY   
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]   
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="7d9da-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="7d9da-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="7d9da-106">Jakýkoli platný dotaz výraz zadání vlastnosti, na kterém se má seřadit.</span><span class="sxs-lookup"><span data-stu-id="7d9da-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="7d9da-107">Je možné zadat více výrazů řazení.</span><span class="sxs-lookup"><span data-stu-id="7d9da-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="7d9da-108">Definuje pořadí řazení výrazů v klauzuli ORDER by organizace ze seřazené sady.</span><span class="sxs-lookup"><span data-stu-id="7d9da-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="7d9da-109">Klauzuli COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="7d9da-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="7d9da-110">Určuje, že operaci Order by mělo být provedeno řazení zadané v `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="7d9da-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="7d9da-111">Klauzuli COLLATE lze použít pouze u řetězců výrazy.</span><span class="sxs-lookup"><span data-stu-id="7d9da-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="7d9da-112">ASC</span><span class="sxs-lookup"><span data-stu-id="7d9da-112">ASC</span></span>  
 <span data-ttu-id="7d9da-113">Určuje, že hodnoty v zadané vlastnosti by měl být seřazeny ve vzestupném pořadí od nejnižší hodnoty po nejvyšší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d9da-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="7d9da-114">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="7d9da-114">This is the default.</span></span>  
  
 <span data-ttu-id="7d9da-115">DESC</span><span class="sxs-lookup"><span data-stu-id="7d9da-115">DESC</span></span>  
 <span data-ttu-id="7d9da-116">Určuje, že hodnoty v zadané vlastnosti by měl být seřazeny sestupně, z nejvyšší hodnotu s nejnižší hodnotou.</span><span class="sxs-lookup"><span data-stu-id="7d9da-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="7d9da-117">LIMIT`n`</span><span class="sxs-lookup"><span data-stu-id="7d9da-117">LIMIT `n`</span></span>  
 <span data-ttu-id="7d9da-118">Pouze první `n` budou vybrány položky.</span><span class="sxs-lookup"><span data-stu-id="7d9da-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="7d9da-119">PŘESKOČIT`n`</span><span class="sxs-lookup"><span data-stu-id="7d9da-119">SKIP `n`</span></span>  
 <span data-ttu-id="7d9da-120">Přeskočí první `n` položky.</span><span class="sxs-lookup"><span data-stu-id="7d9da-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d9da-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d9da-121">Remarks</span></span>  
 <span data-ttu-id="7d9da-122">Klauzuli ORDER by je logicky použita na výsledek klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="7d9da-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="7d9da-123">Klauzuli ORDER by můžete odkazovat na položky v seznamu select pomocí jejich aliasy.</span><span class="sxs-lookup"><span data-stu-id="7d9da-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="7d9da-124">Klauzuli ORDER by můžete také odkazovat na jiné proměnné, které jsou aktuálně oboru.</span><span class="sxs-lookup"><span data-stu-id="7d9da-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="7d9da-125">Ale pokud se odlišné modifikátor byla zadána klauzule SELECT, klauzuli ORDER by může odkazovat pouze aliasy z klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="7d9da-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="7d9da-126">Každý výraz v klauzuli ORDER BY se musí vyhodnotit nějaký typ, který je možné porovnávat nerovnost seřazené (je menší než nebo rovna, a tak dále).</span><span class="sxs-lookup"><span data-stu-id="7d9da-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="7d9da-127">Tyto typy jsou obecně skalární primitiv například čísla, řetězce a data.</span><span class="sxs-lookup"><span data-stu-id="7d9da-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="7d9da-128">RowTypes porovnatelnými typy jsou také porovnatelný z hlediska pořadí.</span><span class="sxs-lookup"><span data-stu-id="7d9da-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="7d9da-129">Pokud váš kód iteruje nad seřazené sady, jiné než pro projekci nejvyšší úrovně, výstup není zaručena tak, aby měl jeho pořadí zachovaná.</span><span class="sxs-lookup"><span data-stu-id="7d9da-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
```  
-- In the following sample, order is guaranteed to be preserved:  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="7d9da-130">Pokud chcete mít seřazené UNION, UNION ALL, EXCEPT nebo INTERSECT operace, použijte následující vzor:</span><span class="sxs-lookup"><span data-stu-id="7d9da-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="7d9da-131">Klíčová slova s omezeným přístupem</span><span class="sxs-lookup"><span data-stu-id="7d9da-131">Restricted keywords</span></span>  
 <span data-ttu-id="7d9da-132">Následující klíčová slova musí být uzavřena v uvozovkách, když se používá v `ORDER BY` klauzule:</span><span class="sxs-lookup"><span data-stu-id="7d9da-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
-   <span data-ttu-id="7d9da-133">MEZI</span><span class="sxs-lookup"><span data-stu-id="7d9da-133">CROSS</span></span>  
  
-   <span data-ttu-id="7d9da-134">ÚPLNÁ</span><span class="sxs-lookup"><span data-stu-id="7d9da-134">FULL</span></span>  
  
-   <span data-ttu-id="7d9da-135">KLÍČ</span><span class="sxs-lookup"><span data-stu-id="7d9da-135">KEY</span></span>  
  
-   <span data-ttu-id="7d9da-136">VLEVO</span><span class="sxs-lookup"><span data-stu-id="7d9da-136">LEFT</span></span>  
  
-   <span data-ttu-id="7d9da-137">POŘADÍ</span><span class="sxs-lookup"><span data-stu-id="7d9da-137">ORDER</span></span>  
  
-   <span data-ttu-id="7d9da-138">VNĚJŠÍ</span><span class="sxs-lookup"><span data-stu-id="7d9da-138">OUTER</span></span>  
  
-   <span data-ttu-id="7d9da-139">VPRAVO</span><span class="sxs-lookup"><span data-stu-id="7d9da-139">RIGHT</span></span>  
  
-   <span data-ttu-id="7d9da-140">ŘÁDEK</span><span class="sxs-lookup"><span data-stu-id="7d9da-140">ROW</span></span>  
  
-   <span data-ttu-id="7d9da-141">HODNOTA</span><span class="sxs-lookup"><span data-stu-id="7d9da-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="7d9da-142">Řazení vnořené dotazy</span><span class="sxs-lookup"><span data-stu-id="7d9da-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="7d9da-143">V rozhraní Entity Framework výraz vnořené můžete umístit kdekoli v dotazu; není zachovávané pořadí vnořený dotaz.</span><span class="sxs-lookup"><span data-stu-id="7d9da-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
```  
-- The following query will order the results by the last name.  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  
  
```  
-- In the following query, ordering of the nested query is ignored.  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="7d9da-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d9da-144">Example</span></span>  
 <span data-ttu-id="7d9da-145">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor Order k určení pořadí řazení použít u objektů, vrátí se v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="7d9da-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="7d9da-146">Dotaz je založen na modelu prodej AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="7d9da-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="7d9da-147">Pro zkompilování a spuštění tohoto dotazu, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="7d9da-147">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="7d9da-148">Postupujte podle pokynů v [postup: provedení dotazu tohoto vrátí výsledky StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="7d9da-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="7d9da-149">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metoda:</span><span class="sxs-lookup"><span data-stu-id="7d9da-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="7d9da-150">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d9da-150">See Also</span></span>  
 [<span data-ttu-id="7d9da-151">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="7d9da-151">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)  
 [<span data-ttu-id="7d9da-152">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7d9da-152">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)  
 [<span data-ttu-id="7d9da-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="7d9da-153">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)  
 [<span data-ttu-id="7d9da-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="7d9da-154">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)  
 [<span data-ttu-id="7d9da-155">TOP</span><span class="sxs-lookup"><span data-stu-id="7d9da-155">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
