---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: f3310274766ff3619604e30bfb5f5ca437cb1acd
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70249755"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="70cc7-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="70cc7-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="70cc7-103">Určuje pořadí řazení používané u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="70cc7-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70cc7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70cc7-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="70cc7-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="70cc7-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="70cc7-106">Libovolný platný výraz dotazu určující vlastnost, podle které se má řadit.</span><span class="sxs-lookup"><span data-stu-id="70cc7-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="70cc7-107">Lze zadat vícenásobné výrazy řazení.</span><span class="sxs-lookup"><span data-stu-id="70cc7-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="70cc7-108">Sekvence výrazů řazení v klauzuli ORDER BY definuje organizaci seřazené sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="70cc7-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="70cc7-109">KOMPLETování {collation_name}</span><span class="sxs-lookup"><span data-stu-id="70cc7-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="70cc7-110">Určuje, že operace ORDER by měla být provedena podle kolace zadané v `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="70cc7-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="70cc7-111">Klauzuli COLLATE lze použít pouze pro řetězcové výrazy.</span><span class="sxs-lookup"><span data-stu-id="70cc7-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="70cc7-112">ASC</span><span class="sxs-lookup"><span data-stu-id="70cc7-112">ASC</span></span>  
 <span data-ttu-id="70cc7-113">Určuje, že hodnoty v zadané vlastnosti by měly být seřazeny vzestupně, od nejnižší hodnoty po nejvyšší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="70cc7-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="70cc7-114">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="70cc7-114">This is the default.</span></span>  
  
 <span data-ttu-id="70cc7-115">DESC</span><span class="sxs-lookup"><span data-stu-id="70cc7-115">DESC</span></span>  
 <span data-ttu-id="70cc7-116">Určuje, že hodnoty v zadané vlastnosti by měly být seřazené v sestupném pořadí, od nejvyšší hodnoty po nejnižší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="70cc7-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="70cc7-117">POČTU`n`</span><span class="sxs-lookup"><span data-stu-id="70cc7-117">LIMIT `n`</span></span>  
 <span data-ttu-id="70cc7-118">Budou vybrány pouze `n` první položky.</span><span class="sxs-lookup"><span data-stu-id="70cc7-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="70cc7-119">PŘÍMO`n`</span><span class="sxs-lookup"><span data-stu-id="70cc7-119">SKIP `n`</span></span>  
 <span data-ttu-id="70cc7-120">Přeskočí první `n` položky.</span><span class="sxs-lookup"><span data-stu-id="70cc7-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="70cc7-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70cc7-121">Remarks</span></span>  
 <span data-ttu-id="70cc7-122">Klauzule ORDER BY je logicky aplikována na výsledek klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="70cc7-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="70cc7-123">Klauzule ORDER BY může odkazovat na položky v seznamu SELECT pomocí jejich aliasů.</span><span class="sxs-lookup"><span data-stu-id="70cc7-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="70cc7-124">Klauzule ORDER BY může odkazovat také na jiné proměnné, které jsou aktuálně v oboru.</span><span class="sxs-lookup"><span data-stu-id="70cc7-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="70cc7-125">Pokud je však klauzule SELECT zadána s modifikátorem DISTINCT, klauzule ORDER BY může odkazovat pouze na aliasy z klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="70cc7-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="70cc7-126">Každý výraz v klauzuli ORDER BY se musí vyhodnotit na určitý typ, který lze porovnat s seřazenou nerovností (menší než nebo větší než a tak dále).</span><span class="sxs-lookup"><span data-stu-id="70cc7-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="70cc7-127">Tyto typy jsou všeobecně skalární primitivní prvky, jako jsou čísla, řetězce a data.</span><span class="sxs-lookup"><span data-stu-id="70cc7-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="70cc7-128">RowTypes srovnatelných typů je také porovnatelný z pořadí.</span><span class="sxs-lookup"><span data-stu-id="70cc7-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="70cc7-129">Pokud váš kód projde seřazenou sadou, která je jiná než pro projekci nejvyšší úrovně, není zaručeno, že se ve výstupu nezachová jeho objednávka.</span><span class="sxs-lookup"><span data-stu-id="70cc7-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
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
  
 <span data-ttu-id="70cc7-130">Pokud chcete mít objednanou operaci SJEDNOCENí, SJEDNOCENí, vyloučení nebo průnik, použijte následující vzor:</span><span class="sxs-lookup"><span data-stu-id="70cc7-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="70cc7-131">Omezená klíčová slova</span><span class="sxs-lookup"><span data-stu-id="70cc7-131">Restricted keywords</span></span>  
 <span data-ttu-id="70cc7-132">Při použití v `ORDER BY` klauzuli musí být v uvozovkách uzavřená následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="70cc7-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="70cc7-133">JÍŽDÍ</span><span class="sxs-lookup"><span data-stu-id="70cc7-133">CROSS</span></span>  
  
- <span data-ttu-id="70cc7-134">KOMPLETNÍ</span><span class="sxs-lookup"><span data-stu-id="70cc7-134">FULL</span></span>  
  
- <span data-ttu-id="70cc7-135">KEY</span><span class="sxs-lookup"><span data-stu-id="70cc7-135">KEY</span></span>  
  
- <span data-ttu-id="70cc7-136">ZBÝVÁ</span><span class="sxs-lookup"><span data-stu-id="70cc7-136">LEFT</span></span>  
  
- <span data-ttu-id="70cc7-137">ZA</span><span class="sxs-lookup"><span data-stu-id="70cc7-137">ORDER</span></span>  
  
- <span data-ttu-id="70cc7-138">VNĚJŠÍ</span><span class="sxs-lookup"><span data-stu-id="70cc7-138">OUTER</span></span>  
  
- <span data-ttu-id="70cc7-139">KLIKNUTÍM</span><span class="sxs-lookup"><span data-stu-id="70cc7-139">RIGHT</span></span>  
  
- <span data-ttu-id="70cc7-140">ROW</span><span class="sxs-lookup"><span data-stu-id="70cc7-140">ROW</span></span>  
  
- <span data-ttu-id="70cc7-141">OSA</span><span class="sxs-lookup"><span data-stu-id="70cc7-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="70cc7-142">Řazení vnořených dotazů</span><span class="sxs-lookup"><span data-stu-id="70cc7-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="70cc7-143">V Entity Framework vnořený výraz může být umístěn kdekoli v dotazu; pořadí vnořeného dotazu není zachováno.</span><span class="sxs-lookup"><span data-stu-id="70cc7-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="70cc7-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="70cc7-144">Example</span></span>  
 <span data-ttu-id="70cc7-145">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ORDER by k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="70cc7-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="70cc7-146">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="70cc7-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="70cc7-147">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="70cc7-147">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="70cc7-148">Postupujte podle pokynů v [tématu Postupy: Spustí dotaz, který vrátí výsledky](../how-to-execute-a-query-that-returns-structuraltype-results.md)StructuralType.</span><span class="sxs-lookup"><span data-stu-id="70cc7-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="70cc7-149">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="70cc7-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="70cc7-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70cc7-150">See also</span></span>

- [<span data-ttu-id="70cc7-151">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="70cc7-151">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="70cc7-152">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="70cc7-152">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="70cc7-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="70cc7-153">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="70cc7-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="70cc7-154">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="70cc7-155">TOP</span><span class="sxs-lookup"><span data-stu-id="70cc7-155">TOP</span></span>](top-entity-sql.md)
