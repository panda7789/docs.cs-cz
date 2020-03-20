---
title: POŘADÍ OD (Entita SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 1233971b172079aa48227d0ec520068afbdf0952
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150066"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="3d814-102">POŘADÍ OD (Entita SQL)</span><span class="sxs-lookup"><span data-stu-id="3d814-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="3d814-103">Určuje pořadí řazení použité u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="3d814-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d814-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3d814-104">Syntax</span></span>  
  
```sql  
[ ORDER BY
   {  
      order_by_expression [SKIP n] [LIMIT n]  
      [ COLLATE collation_name ]  
      [ ASC | DESC ]  
   }  
   [ ,…n ]
]  
```  
  
## <a name="arguments"></a><span data-ttu-id="3d814-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="3d814-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="3d814-106">Libovolný platný výraz dotazu určující vlastnost, na které se má řadit.</span><span class="sxs-lookup"><span data-stu-id="3d814-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="3d814-107">Lze zadat více výrazů řazení.</span><span class="sxs-lookup"><span data-stu-id="3d814-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="3d814-108">Posloupnost výrazů řazení v klauzuli ORDER BY definuje organizaci seřazené sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="3d814-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="3d814-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="3d814-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="3d814-110">Určuje, že operace OBJEDNÁNÍ BY má být provedena `collation_name`podle kolace zadané v .</span><span class="sxs-lookup"><span data-stu-id="3d814-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="3d814-111">COLLATE je použitelná pouze pro řetězcové výrazy.</span><span class="sxs-lookup"><span data-stu-id="3d814-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="3d814-112">ASC</span><span class="sxs-lookup"><span data-stu-id="3d814-112">ASC</span></span>  
 <span data-ttu-id="3d814-113">Určuje, že hodnoty v zadané vlastnosti by měly být seřazeny vzestupně, od nejnižší hodnoty po nejvyšší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3d814-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="3d814-114">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="3d814-114">This is the default.</span></span>  
  
 <span data-ttu-id="3d814-115">DESC</span><span class="sxs-lookup"><span data-stu-id="3d814-115">DESC</span></span>  
 <span data-ttu-id="3d814-116">Určuje, že hodnoty v zadané vlastnosti by měly být seřazeny v sestupném pořadí, od nejvyšší hodnoty po nejnižší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3d814-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="3d814-117">Limit`n`</span><span class="sxs-lookup"><span data-stu-id="3d814-117">LIMIT `n`</span></span>  
 <span data-ttu-id="3d814-118">Budou vybrány pouze první `n` položky.</span><span class="sxs-lookup"><span data-stu-id="3d814-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="3d814-119">Přeskočit`n`</span><span class="sxs-lookup"><span data-stu-id="3d814-119">SKIP `n`</span></span>  
 <span data-ttu-id="3d814-120">Přeskočí první `n` položky.</span><span class="sxs-lookup"><span data-stu-id="3d814-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d814-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3d814-121">Remarks</span></span>  
 <span data-ttu-id="3d814-122">Klauzule ORDER BY je logicky použita na výsledek klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="3d814-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="3d814-123">Klauzule ORDER BY může odkazovat na položky ve výběrovém seznamu pomocí jejich aliasů.</span><span class="sxs-lookup"><span data-stu-id="3d814-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="3d814-124">Klauzule ORDER BY může také odkazovat na jiné proměnné, které jsou aktuálně v oboru.</span><span class="sxs-lookup"><span data-stu-id="3d814-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="3d814-125">Pokud však byla klauzule SELECT zadána s modifikátorem DISTINCT, klauzule ORDER BY může odkazovat pouze na aliasy z klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="3d814-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="3d814-126">Každý výraz v klauzuli ORDER BY musí být vyhodnocen na nějaký typ, který lze porovnat pro objednanou nerovnost (menší než nebo větší než a tak dále).</span><span class="sxs-lookup"><span data-stu-id="3d814-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="3d814-127">Tyto typy jsou obecně skalární primitiva, jako jsou čísla, řetězce a data.</span><span class="sxs-lookup"><span data-stu-id="3d814-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="3d814-128">RowTypes srovnatelné typy jsou také pořadí srovnatelné.</span><span class="sxs-lookup"><span data-stu-id="3d814-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="3d814-129">Pokud váš kód iterates přes objednané sady, jiné než pro projekci nejvyšší úrovně, výstup není zaručeno, že jeho pořadí zachována.</span><span class="sxs-lookup"><span data-stu-id="3d814-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="3d814-130">V následujícím vzorku je zaručeno, že objednávka bude zachována:</span><span class="sxs-lookup"><span data-stu-id="3d814-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="3d814-131">V následujícím dotazu je řazení vnořeného dotazu ignorováno:</span><span class="sxs-lookup"><span data-stu-id="3d814-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="3d814-132">Chcete-li mít objednané union, UNION ALL, EXCEPT, nebo INTERSECT operace, použijte následující vzor:</span><span class="sxs-lookup"><span data-stu-id="3d814-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="3d814-133">Klíčová slova s omezeným přístupem</span><span class="sxs-lookup"><span data-stu-id="3d814-133">Restricted keywords</span></span>  
 <span data-ttu-id="3d814-134">Následující klíčová slova musí být uzavřena v `ORDER BY` uvozovkách při použití v klauzuli:</span><span class="sxs-lookup"><span data-stu-id="3d814-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="3d814-135">Kříž</span><span class="sxs-lookup"><span data-stu-id="3d814-135">CROSS</span></span>  
  
- <span data-ttu-id="3d814-136">Plné</span><span class="sxs-lookup"><span data-stu-id="3d814-136">FULL</span></span>  
  
- <span data-ttu-id="3d814-137">KEY</span><span class="sxs-lookup"><span data-stu-id="3d814-137">KEY</span></span>  
  
- <span data-ttu-id="3d814-138">LEFT</span><span class="sxs-lookup"><span data-stu-id="3d814-138">LEFT</span></span>  
  
- <span data-ttu-id="3d814-139">Objednávky</span><span class="sxs-lookup"><span data-stu-id="3d814-139">ORDER</span></span>  
  
- <span data-ttu-id="3d814-140">Vnější</span><span class="sxs-lookup"><span data-stu-id="3d814-140">OUTER</span></span>  
  
- <span data-ttu-id="3d814-141">RIGHT</span><span class="sxs-lookup"><span data-stu-id="3d814-141">RIGHT</span></span>  
  
- <span data-ttu-id="3d814-142">ROW</span><span class="sxs-lookup"><span data-stu-id="3d814-142">ROW</span></span>  
  
- <span data-ttu-id="3d814-143">HODNOTA</span><span class="sxs-lookup"><span data-stu-id="3d814-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="3d814-144">Řazení vnořených dotazů</span><span class="sxs-lookup"><span data-stu-id="3d814-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="3d814-145">V rámci entity vnořený výraz lze umístit kdekoli v dotazu; pořadí vnořeného dotazu není zachováno.</span><span class="sxs-lookup"><span data-stu-id="3d814-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="3d814-146">Následující dotaz seřídí výsledky podle příjmení:</span><span class="sxs-lookup"><span data-stu-id="3d814-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="3d814-147">V následujícím dotazu je řazení vnořeného dotazu ignorováno:</span><span class="sxs-lookup"><span data-stu-id="3d814-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="3d814-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d814-148">Example</span></span>  
 <span data-ttu-id="3d814-149">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotaz používá operátor ORDER BY k určení pořadí řazení použitého u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="3d814-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="3d814-150">Dotaz je založen na adventureworks prodejní model.</span><span class="sxs-lookup"><span data-stu-id="3d814-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="3d814-151">Chcete-li tento dotaz zkompilovat a spustit, postupujte takto:</span><span class="sxs-lookup"><span data-stu-id="3d814-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="3d814-152">Postupujte podle postupu v [části Postup: Spusťte dotaz, který vrací výsledky typu StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="3d814-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="3d814-153">Předat následující dotaz jako argument `ExecuteStructuralTypeQuery` metodě:</span><span class="sxs-lookup"><span data-stu-id="3d814-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="3d814-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d814-154">See also</span></span>

- [<span data-ttu-id="3d814-155">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="3d814-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="3d814-156">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="3d814-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="3d814-157">Přeskočit</span><span class="sxs-lookup"><span data-stu-id="3d814-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="3d814-158">Limit</span><span class="sxs-lookup"><span data-stu-id="3d814-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="3d814-159">Top</span><span class="sxs-lookup"><span data-stu-id="3d814-159">TOP</span></span>](top-entity-sql.md)
