---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 3f5d3c9a65bd9ac412a908a3e850a7e01d2ee6cd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59116659"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="6eb0e-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="6eb0e-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="6eb0e-103">Určuje pořadí řazení použít u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6eb0e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6eb0e-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="6eb0e-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="6eb0e-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="6eb0e-106">Libovolný platný dotaz výraz určující vlastnost, na kterém se má seřadit.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="6eb0e-107">Je možné zadat více výrazů řazení.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="6eb0e-108">Definuje sekvenci výrazů řazení v klauzuli ORDER by organizace sady seřazených výsledků.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="6eb0e-109">COLLATE {collation_name}</span><span class="sxs-lookup"><span data-stu-id="6eb0e-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="6eb0e-110">Určuje, že operaci Order by mělo být provedeno řazení zadané v `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="6eb0e-111">KOLACE je možné použít pouze řetězcové výrazy.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="6eb0e-112">ASC</span><span class="sxs-lookup"><span data-stu-id="6eb0e-112">ASC</span></span>  
 <span data-ttu-id="6eb0e-113">Určuje, zda mají být řazeny hodnoty v zadané vlastnosti ve vzestupném pořadí od nejnižší hodnoty po nejvyšší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="6eb0e-114">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-114">This is the default.</span></span>  
  
 <span data-ttu-id="6eb0e-115">DESC</span><span class="sxs-lookup"><span data-stu-id="6eb0e-115">DESC</span></span>  
 <span data-ttu-id="6eb0e-116">Určuje, že mají být řazeny hodnoty v zadané vlastnosti v sestupném pořadí, v nejvyšší hodnotu na nejnižší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="6eb0e-117">LIMIT</span><span class="sxs-lookup"><span data-stu-id="6eb0e-117">LIMIT</span></span> `n`  
 <span data-ttu-id="6eb0e-118">Pouze první `n` budou vybrané položky.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="6eb0e-119">SKIP</span><span class="sxs-lookup"><span data-stu-id="6eb0e-119">SKIP</span></span> `n`  
 <span data-ttu-id="6eb0e-120">Přeskočí první `n` položky.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6eb0e-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6eb0e-121">Remarks</span></span>  
 <span data-ttu-id="6eb0e-122">Klauzule ORDER by je logicky použít výsledek výrazu klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="6eb0e-123">Klauzule ORDER by může odkazovat položky v seznamu select pomocí jejich aliasy.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="6eb0e-124">Klauzule ORDER by může také odkazovat další proměnné, které jsou aktuálně oboru.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="6eb0e-125">Ale pokud byl zadán klauzuli SELECT DISTINCT modifikátorem, klauzule ORDER by mohou odkazovat pouze aliasy v klauzuli SELECT.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="6eb0e-126">Každý výraz v klauzuli ORDER by musí vyhodnotit na nějaký typ, který je možné porovnat seřazený nerovnost (menší než nebo rovna, a tak dále).</span><span class="sxs-lookup"><span data-stu-id="6eb0e-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="6eb0e-127">Tyto typy jsou obecně skalární primitivních elementů, jako jsou čísla, řetězce a data.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="6eb0e-128">RowTypes srovnatelných typů jsou také porovnatelný z hlediska pořadí.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="6eb0e-129">Pokud váš kód iteruje seřazené sady, jiné než pro nejvyšší úrovně projekce výstup není zaručeno má jeho pořadí zachovány.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  
  
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
  
 <span data-ttu-id="6eb0e-130">Pokud chcete mít seřazený UNION, UNION ALL, EXCEPT nebo INTERSECT operace, použijte následující vzor:</span><span class="sxs-lookup"><span data-stu-id="6eb0e-130">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="6eb0e-131">Klíčová slova s omezeným přístupem</span><span class="sxs-lookup"><span data-stu-id="6eb0e-131">Restricted keywords</span></span>  
 <span data-ttu-id="6eb0e-132">Následující klíčová slova musí být uzavřen v uvozovkách při použití `ORDER BY` klauzule:</span><span class="sxs-lookup"><span data-stu-id="6eb0e-132">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
-   <span data-ttu-id="6eb0e-133">RŮZNÉ</span><span class="sxs-lookup"><span data-stu-id="6eb0e-133">CROSS</span></span>  
  
-   <span data-ttu-id="6eb0e-134">ÚPLNÉ</span><span class="sxs-lookup"><span data-stu-id="6eb0e-134">FULL</span></span>  
  
-   <span data-ttu-id="6eb0e-135">KEY</span><span class="sxs-lookup"><span data-stu-id="6eb0e-135">KEY</span></span>  
  
-   <span data-ttu-id="6eb0e-136">DOLEVA</span><span class="sxs-lookup"><span data-stu-id="6eb0e-136">LEFT</span></span>  
  
-   <span data-ttu-id="6eb0e-137">POŘADÍ</span><span class="sxs-lookup"><span data-stu-id="6eb0e-137">ORDER</span></span>  
  
-   <span data-ttu-id="6eb0e-138">VNĚJŠÍ</span><span class="sxs-lookup"><span data-stu-id="6eb0e-138">OUTER</span></span>  
  
-   <span data-ttu-id="6eb0e-139">DOPRAVA</span><span class="sxs-lookup"><span data-stu-id="6eb0e-139">RIGHT</span></span>  
  
-   <span data-ttu-id="6eb0e-140">ROW</span><span class="sxs-lookup"><span data-stu-id="6eb0e-140">ROW</span></span>  
  
-   <span data-ttu-id="6eb0e-141">HODNOTA</span><span class="sxs-lookup"><span data-stu-id="6eb0e-141">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="6eb0e-142">Řazení vnořené dotazy</span><span class="sxs-lookup"><span data-stu-id="6eb0e-142">Ordering Nested Queries</span></span>  
 <span data-ttu-id="6eb0e-143">V rozhraní Entity Framework vnořený výraz může být umístěna kdekoli v dotazu; není zachováno pořadí vnořeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-143">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="6eb0e-144">Příklad</span><span class="sxs-lookup"><span data-stu-id="6eb0e-144">Example</span></span>  
 <span data-ttu-id="6eb0e-145">Následující [!INCLUDE[esql](../../../../../../includes/esql-md.md)] dotazu používá operátor klauzule ORDER BY k určení pořadí řazení použít u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-145">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="6eb0e-146">Dotaz je založen na modelu Sales AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="6eb0e-146">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="6eb0e-147">Kompilace a spuštění tohoto dotazu, postupujte podle těchto kroků:</span><span class="sxs-lookup"><span data-stu-id="6eb0e-147">To compile and run this query, follow these steps:</span></span>  
  
1.  <span data-ttu-id="6eb0e-148">Postupujte podle pokynů v [jak: Spustit dotaz, který vrátí výsledky typu StructuralType](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="6eb0e-148">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../../../../../../docs/framework/data/adonet/ef/how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2.  <span data-ttu-id="6eb0e-149">Předat jako argument pro následující dotaz `ExecuteStructuralTypeQuery` metody:</span><span class="sxs-lookup"><span data-stu-id="6eb0e-149">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-csharp[DP EntityServices Concepts 2#ORDERBY](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts 2/cs/entitysql.cs#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="6eb0e-150">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6eb0e-150">See also</span></span>

- [<span data-ttu-id="6eb0e-151">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="6eb0e-151">Query Expressions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/query-expressions-entity-sql.md)
- [<span data-ttu-id="6eb0e-152">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6eb0e-152">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="6eb0e-153">SKIP</span><span class="sxs-lookup"><span data-stu-id="6eb0e-153">SKIP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/skip-entity-sql.md)
- [<span data-ttu-id="6eb0e-154">LIMIT</span><span class="sxs-lookup"><span data-stu-id="6eb0e-154">LIMIT</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/limit-entity-sql.md)
- [<span data-ttu-id="6eb0e-155">TOP</span><span class="sxs-lookup"><span data-stu-id="6eb0e-155">TOP</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/top-entity-sql.md)
