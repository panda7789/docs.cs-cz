---
title: ORDER BY (Entity SQL)
ms.date: 03/30/2017
ms.assetid: c0b61572-ecee-41eb-9d7f-74132ec8a26c
ms.openlocfilehash: 2010ef9d6fe37e65824cac877074453db1b789db
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319449"
---
# <a name="order-by-entity-sql"></a><span data-ttu-id="f7b83-102">ORDER BY (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="f7b83-102">ORDER BY (Entity SQL)</span></span>
<span data-ttu-id="f7b83-103">Určuje pořadí řazení používané u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="f7b83-103">Specifies the sort order used on objects returned in a SELECT statement.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7b83-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f7b83-104">Syntax</span></span>  
  
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
  
## <a name="arguments"></a><span data-ttu-id="f7b83-105">Arguments</span><span class="sxs-lookup"><span data-stu-id="f7b83-105">Arguments</span></span>  
 `order_by_expression`  
 <span data-ttu-id="f7b83-106">Libovolný platný výraz dotazu určující vlastnost, podle které se má řadit.</span><span class="sxs-lookup"><span data-stu-id="f7b83-106">Any valid query expression specifying a property on which to sort.</span></span> <span data-ttu-id="f7b83-107">Lze zadat vícenásobné výrazy řazení.</span><span class="sxs-lookup"><span data-stu-id="f7b83-107">Multiple sort expressions can be specified.</span></span> <span data-ttu-id="f7b83-108">Sekvence výrazů řazení v klauzuli ORDER BY definuje organizaci seřazené sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="f7b83-108">The sequence of the sort expressions in the ORDER BY clause defines the organization of the sorted result set.</span></span>  
  
 <span data-ttu-id="f7b83-109">KOMPLETování {collation_name}</span><span class="sxs-lookup"><span data-stu-id="f7b83-109">COLLATE {collation_name}</span></span>  
 <span data-ttu-id="f7b83-110">Určuje, že operace ORDER by měla být provedena podle kolace zadané v `collation_name`.</span><span class="sxs-lookup"><span data-stu-id="f7b83-110">Specifies that the ORDER BY operation should be performed according to the collation specified in `collation_name`.</span></span> <span data-ttu-id="f7b83-111">Klauzuli COLLATE lze použít pouze pro řetězcové výrazy.</span><span class="sxs-lookup"><span data-stu-id="f7b83-111">COLLATE is applicable only for string expressions.</span></span>  
  
 <span data-ttu-id="f7b83-112">ASC</span><span class="sxs-lookup"><span data-stu-id="f7b83-112">ASC</span></span>  
 <span data-ttu-id="f7b83-113">Určuje, že hodnoty v zadané vlastnosti by měly být seřazeny vzestupně, od nejnižší hodnoty po nejvyšší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f7b83-113">Specifies that the values in the specified property should be sorted in ascending order, from lowest value to highest value.</span></span> <span data-ttu-id="f7b83-114">Toto nastavení je výchozí.</span><span class="sxs-lookup"><span data-stu-id="f7b83-114">This is the default.</span></span>  
  
 <span data-ttu-id="f7b83-115">ŘETĚZEC</span><span class="sxs-lookup"><span data-stu-id="f7b83-115">DESC</span></span>  
 <span data-ttu-id="f7b83-116">Určuje, že hodnoty v zadané vlastnosti by měly být seřazené v sestupném pořadí, od nejvyšší hodnoty po nejnižší hodnotu.</span><span class="sxs-lookup"><span data-stu-id="f7b83-116">Specifies that the values in the specified property should be sorted in descending order, from highest value to lowest value.</span></span>  
  
 <span data-ttu-id="f7b83-117">OMEZENÍ @no__t – 0</span><span class="sxs-lookup"><span data-stu-id="f7b83-117">LIMIT `n`</span></span>  
 <span data-ttu-id="f7b83-118">Budou vybrány pouze první položky `n`.</span><span class="sxs-lookup"><span data-stu-id="f7b83-118">Only the first `n` items will be selected.</span></span>  
  
 <span data-ttu-id="f7b83-119">Přeskočit `n`</span><span class="sxs-lookup"><span data-stu-id="f7b83-119">SKIP `n`</span></span>  
 <span data-ttu-id="f7b83-120">Přeskočí první položky `n`.</span><span class="sxs-lookup"><span data-stu-id="f7b83-120">Skips the first `n` items.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f7b83-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f7b83-121">Remarks</span></span>  
 <span data-ttu-id="f7b83-122">Klauzule ORDER BY je logicky aplikována na výsledek klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="f7b83-122">The ORDER BY clause is logically applied to the result of the SELECT clause.</span></span> <span data-ttu-id="f7b83-123">Klauzule ORDER BY může odkazovat na položky v seznamu SELECT pomocí jejich aliasů.</span><span class="sxs-lookup"><span data-stu-id="f7b83-123">The ORDER BY clause can reference items in the select list by using their aliases.</span></span> <span data-ttu-id="f7b83-124">Klauzule ORDER BY může odkazovat také na jiné proměnné, které jsou aktuálně v oboru.</span><span class="sxs-lookup"><span data-stu-id="f7b83-124">The ORDER BY clause can also reference other variables that are currently in-scope.</span></span> <span data-ttu-id="f7b83-125">Pokud je však klauzule SELECT zadána s modifikátorem DISTINCT, klauzule ORDER BY může odkazovat pouze na aliasy z klauzule SELECT.</span><span class="sxs-lookup"><span data-stu-id="f7b83-125">However, if the SELECT clause has been specified with a DISTINCT modifier, the ORDER BY clause can only reference aliases from the SELECT clause.</span></span>  
  
 `SELECT c AS c1 FROM cs AS c ORDER BY c1.e1, c.e2`  
  
 <span data-ttu-id="f7b83-126">Každý výraz v klauzuli ORDER BY se musí vyhodnotit na určitý typ, který lze porovnat s seřazenou nerovností (menší než nebo větší než a tak dále).</span><span class="sxs-lookup"><span data-stu-id="f7b83-126">Each expression in the ORDER BY clause must evaluate to some type that can be compared for ordered inequality (less than or greater than, and so on).</span></span> <span data-ttu-id="f7b83-127">Tyto typy jsou všeobecně skalární primitivní prvky, jako jsou čísla, řetězce a data.</span><span class="sxs-lookup"><span data-stu-id="f7b83-127">These types are generally scalar primitives such as numbers, strings, and dates.</span></span> <span data-ttu-id="f7b83-128">RowTypes srovnatelných typů je také porovnatelný z pořadí.</span><span class="sxs-lookup"><span data-stu-id="f7b83-128">RowTypes of comparable types are also order comparable.</span></span>  
  
 <span data-ttu-id="f7b83-129">Pokud váš kód projde seřazenou sadou, která je jiná než pro projekci nejvyšší úrovně, není zaručeno, že se ve výstupu nezachová jeho objednávka.</span><span class="sxs-lookup"><span data-stu-id="f7b83-129">If your code iterates over an ordered set, other than for a top-level projection, the output is not guaranteed to have its order preserved.</span></span>  

<span data-ttu-id="f7b83-130">V následující ukázce je zaručeno, že bude zachováno pořadí:</span><span class="sxs-lookup"><span data-stu-id="f7b83-130">In the following sample, order is guaranteed to be preserved:</span></span>

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="f7b83-131">V následujícím dotazu se pořadí vnořeného dotazu ignoruje:</span><span class="sxs-lookup"><span data-stu-id="f7b83-131">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
 <span data-ttu-id="f7b83-132">Pokud chcete mít objednanou operaci SJEDNOCENí, SJEDNOCENí, vyloučení nebo průnik, použijte následující vzor:</span><span class="sxs-lookup"><span data-stu-id="f7b83-132">To have an ordered UNION, UNION ALL, EXCEPT, or INTERSECT operation, use the following pattern:</span></span>  
  
```sql  
SELECT ...  
FROM ( UNION/EXCEPT/INTERSECT operation )  
ORDER BY ...  
```  
  
## <a name="restricted-keywords"></a><span data-ttu-id="f7b83-133">Omezená klíčová slova</span><span class="sxs-lookup"><span data-stu-id="f7b83-133">Restricted keywords</span></span>  
 <span data-ttu-id="f7b83-134">Při použití v klauzuli `ORDER BY` musí být v uvozovkách uzavřená následující klíčová slova:</span><span class="sxs-lookup"><span data-stu-id="f7b83-134">The following keywords must be enclosed in quotation marks when used in an `ORDER BY` clause:</span></span>  
  
- <span data-ttu-id="f7b83-135">JÍŽDÍ</span><span class="sxs-lookup"><span data-stu-id="f7b83-135">CROSS</span></span>  
  
- <span data-ttu-id="f7b83-136">KOMPLETNÍ</span><span class="sxs-lookup"><span data-stu-id="f7b83-136">FULL</span></span>  
  
- <span data-ttu-id="f7b83-137">KEY</span><span class="sxs-lookup"><span data-stu-id="f7b83-137">KEY</span></span>  
  
- <span data-ttu-id="f7b83-138">ZBÝVÁ</span><span class="sxs-lookup"><span data-stu-id="f7b83-138">LEFT</span></span>  
  
- <span data-ttu-id="f7b83-139">ZA</span><span class="sxs-lookup"><span data-stu-id="f7b83-139">ORDER</span></span>  
  
- <span data-ttu-id="f7b83-140">VNĚJŠÍ</span><span class="sxs-lookup"><span data-stu-id="f7b83-140">OUTER</span></span>  
  
- <span data-ttu-id="f7b83-141">Kliknutím</span><span class="sxs-lookup"><span data-stu-id="f7b83-141">RIGHT</span></span>  
  
- <span data-ttu-id="f7b83-142">ROW</span><span class="sxs-lookup"><span data-stu-id="f7b83-142">ROW</span></span>  
  
- <span data-ttu-id="f7b83-143">OSA</span><span class="sxs-lookup"><span data-stu-id="f7b83-143">VALUE</span></span>  
  
## <a name="ordering-nested-queries"></a><span data-ttu-id="f7b83-144">Řazení vnořených dotazů</span><span class="sxs-lookup"><span data-stu-id="f7b83-144">Ordering Nested Queries</span></span>  
 <span data-ttu-id="f7b83-145">V Entity Framework vnořený výraz může být umístěn kdekoli v dotazu; pořadí vnořeného dotazu není zachováno.</span><span class="sxs-lookup"><span data-stu-id="f7b83-145">In the Entity Framework, a nested expression can be placed anywhere in the query; the order of a nested query is not preserved.</span></span>  

<span data-ttu-id="f7b83-146">Následující dotaz bude seřadit výsledky podle příjmení:</span><span class="sxs-lookup"><span data-stu-id="f7b83-146">The following query will order the results by the last name:</span></span>  

```sql  
SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName  
```  

<span data-ttu-id="f7b83-147">V následujícím dotazu se pořadí vnořeného dotazu ignoruje:</span><span class="sxs-lookup"><span data-stu-id="f7b83-147">In the following query, ordering of the nested query is ignored:</span></span>  

```sql  
SELECT C2.FirstName, C2.LastName  
    FROM (SELECT C1.FirstName, C1.LastName  
        FROM AdventureWorks.Contact as C1  
        ORDER BY C1.LastName) as C2  
```  
  
## <a name="example"></a><span data-ttu-id="f7b83-148">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7b83-148">Example</span></span>  
 <span data-ttu-id="f7b83-149">Následující dotaz [!INCLUDE[esql](../../../../../../includes/esql-md.md)] používá operátor ORDER BY k určení pořadí řazení používaného u objektů vrácených v příkazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="f7b83-149">The following [!INCLUDE[esql](../../../../../../includes/esql-md.md)] query uses the ORDER BY operator to specify the sort order used on objects returned in a SELECT statement.</span></span> <span data-ttu-id="f7b83-150">Dotaz je založen na modelu prodeje společnosti AdventureWorks.</span><span class="sxs-lookup"><span data-stu-id="f7b83-150">The query is based on the AdventureWorks Sales Model.</span></span> <span data-ttu-id="f7b83-151">Chcete-li zkompilovat a spustit tento dotaz, postupujte podle následujících kroků:</span><span class="sxs-lookup"><span data-stu-id="f7b83-151">To compile and run this query, follow these steps:</span></span>  
  
1. <span data-ttu-id="f7b83-152">Použijte postup v tématu [Postup: provedení dotazu, který vrátí výsledky StructuralType](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span><span class="sxs-lookup"><span data-stu-id="f7b83-152">Follow the procedure in [How to: Execute a Query that Returns StructuralType Results](../how-to-execute-a-query-that-returns-structuraltype-results.md).</span></span>  
  
2. <span data-ttu-id="f7b83-153">Předat následující dotaz jako argument metodě `ExecuteStructuralTypeQuery`:</span><span class="sxs-lookup"><span data-stu-id="f7b83-153">Pass the following query as an argument to the `ExecuteStructuralTypeQuery` method:</span></span>  
  
 [!code-sql[DP EntityServices Concepts#ORDERBY](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#orderby)]  
  
## <a name="see-also"></a><span data-ttu-id="f7b83-154">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f7b83-154">See also</span></span>

- [<span data-ttu-id="f7b83-155">Výrazy dotazu</span><span class="sxs-lookup"><span data-stu-id="f7b83-155">Query Expressions</span></span>](query-expressions-entity-sql.md)
- [<span data-ttu-id="f7b83-156">Reference k Entity SQL</span><span class="sxs-lookup"><span data-stu-id="f7b83-156">Entity SQL Reference</span></span>](entity-sql-reference.md)
- [<span data-ttu-id="f7b83-157">SKIP</span><span class="sxs-lookup"><span data-stu-id="f7b83-157">SKIP</span></span>](skip-entity-sql.md)
- [<span data-ttu-id="f7b83-158">LIMIT</span><span class="sxs-lookup"><span data-stu-id="f7b83-158">LIMIT</span></span>](limit-entity-sql.md)
- [<span data-ttu-id="f7b83-159">TOP</span><span class="sxs-lookup"><span data-stu-id="f7b83-159">TOP</span></span>](top-entity-sql.md)
