---
title: Agregační kanonické funkce
ms.date: 03/30/2017
ms.assetid: 3bcff826-ca90-41b3-a791-04d6ff0e5085
ms.openlocfilehash: 3f4bb84c45e503fc0018e7869f3b41ddab4581a6
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251358"
---
# <a name="aggregate-canonical-functions"></a><span data-ttu-id="5866a-102">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5866a-102">Aggregate Canonical Functions</span></span>

<span data-ttu-id="5866a-103">Agregace jsou výrazy, které omezují řadu vstupních hodnot například na jedinou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5866a-103">Aggregates are expressions that reduce a series of input values into, for example, a single value.</span></span> <span data-ttu-id="5866a-104">Agregace se obvykle používají ve spojení s klauzulí GROUP BY výrazu SELECT a existují omezení, kde je lze použít.</span><span class="sxs-lookup"><span data-stu-id="5866a-104">Aggregates are normally used in conjunction with the GROUP BY clause of the SELECT expression, and there are constraints on where they can be used.</span></span>

## <a name="aggregate-entity-sql-canonical-functions"></a><span data-ttu-id="5866a-105">Agregační Entity SQL – kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5866a-105">Aggregate Entity SQL canonical functions</span></span>

<span data-ttu-id="5866a-106">Níže jsou uvedené agregační Entity SQL kanonické funkce.</span><span class="sxs-lookup"><span data-stu-id="5866a-106">The following are the aggregate Entity SQL canonical functions.</span></span>

### <a name="avgexpression"></a><span data-ttu-id="5866a-107">Prům (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-107">Avg(expression)</span></span>

<span data-ttu-id="5866a-108">Vrátí průměr hodnot, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="5866a-108">Returns the average of the non-null values.</span></span>

<span data-ttu-id="5866a-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-109">**Arguments**</span></span>

<span data-ttu-id="5866a-110">A `Int32` ,`Int64`, a`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="5866a-110">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="5866a-111">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-111">**Return Value**</span></span>

<span data-ttu-id="5866a-112">Typ `expression` `null` nebo `null` , pokud jsou všechny vstupní hodnoty hodnotami.</span><span class="sxs-lookup"><span data-stu-id="5866a-112">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="5866a-113">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-113">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_avg)]
[!code-sql[DP EntityServices Concepts#EDM_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_avg)]

### <a name="bigcountexpression"></a><span data-ttu-id="5866a-114">BigCount(expression)</span><span class="sxs-lookup"><span data-stu-id="5866a-114">BigCount(expression)</span></span>

<span data-ttu-id="5866a-115">Vrátí velikost agregace včetně null a duplicitních hodnot.</span><span class="sxs-lookup"><span data-stu-id="5866a-115">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="5866a-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-116">**Arguments**</span></span>

<span data-ttu-id="5866a-117">Libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="5866a-117">Any type.</span></span>

<span data-ttu-id="5866a-118">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-118">**Return Value**</span></span>

<span data-ttu-id="5866a-119">A `Int64`.</span><span class="sxs-lookup"><span data-stu-id="5866a-119">An `Int64`.</span></span>

<span data-ttu-id="5866a-120">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-120">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_bigcount)]
[!code-sql[DP EntityServices Concepts#EDM_BIGCOUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_bigcount)]

### <a name="countexpression"></a><span data-ttu-id="5866a-121">Count (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-121">Count(expression)</span></span>

<span data-ttu-id="5866a-122">Vrátí velikost agregace včetně null a duplicitních hodnot.</span><span class="sxs-lookup"><span data-stu-id="5866a-122">Returns the size of the aggregate including null and duplicate values.</span></span>

<span data-ttu-id="5866a-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-123">**Arguments**</span></span>

<span data-ttu-id="5866a-124">Libovolný typ.</span><span class="sxs-lookup"><span data-stu-id="5866a-124">Any type.</span></span>

<span data-ttu-id="5866a-125">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-125">**Return Value**</span></span>

<span data-ttu-id="5866a-126">A `Int32`.</span><span class="sxs-lookup"><span data-stu-id="5866a-126">An `Int32`.</span></span>

<span data-ttu-id="5866a-127">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-127">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_count)]
[!code-sql[DP EntityServices Concepts#EDM_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_count)]

### <a name="maxexpression"></a><span data-ttu-id="5866a-128">Max (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-128">Max(expression)</span></span>

<span data-ttu-id="5866a-129">Vrátí maximální hodnotu hodnot, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="5866a-129">Returns the maximum of the non-null values.</span></span>

<span data-ttu-id="5866a-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-130">**Arguments**</span></span>

<span data-ttu-id="5866a-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="5866a-131">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="5866a-132">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-132">**Return Value**</span></span>

<span data-ttu-id="5866a-133">Typ `expression` `null` nebo `null` , pokud jsou všechny vstupní hodnoty hodnotami.</span><span class="sxs-lookup"><span data-stu-id="5866a-133">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="5866a-134">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-134">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_max)]
[!code-sql[DP EntityServices Concepts#EDM_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_max)]

### <a name="minexpression"></a><span data-ttu-id="5866a-135">Min (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-135">Min(expression)</span></span>

<span data-ttu-id="5866a-136">Vrátí minimum hodnot, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="5866a-136">Returns the minimum of the non-null values.</span></span>

<span data-ttu-id="5866a-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-137">**Arguments**</span></span>

<span data-ttu-id="5866a-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span><span class="sxs-lookup"><span data-stu-id="5866a-138">A `Byte`, `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, `Decimal`, `DateTime`, `DateTimeOffset`, `Time`, `String`, `Binary`.</span></span>

<span data-ttu-id="5866a-139">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-139">**Return Value**</span></span>

<span data-ttu-id="5866a-140">Typ `expression` `null` nebo `null` , pokud jsou všechny vstupní hodnoty hodnotami.</span><span class="sxs-lookup"><span data-stu-id="5866a-140">The type of `expression`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="5866a-141">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-141">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_min)]
[!code-sql[DP EntityServices Concepts#EDM_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_min)]

### <a name="stdevexpression"></a><span data-ttu-id="5866a-142">StDev (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-142">StDev(expression)</span></span>

<span data-ttu-id="5866a-143">Vrací směrodatnou odchylku hodnot, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="5866a-143">Returns the standard deviation of the non-null values.</span></span>

<span data-ttu-id="5866a-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-144">**Arguments**</span></span>

<span data-ttu-id="5866a-145">A, `Int64`, ,.`Decimal` `Double` `Int32`</span><span class="sxs-lookup"><span data-stu-id="5866a-145">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="5866a-146">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-146">**Return Value**</span></span>

<span data-ttu-id="5866a-147">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="5866a-147">A `Double`.</span></span> <span data-ttu-id="5866a-148">`Null`, pokud jsou `null` všechny vstupní hodnoty hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5866a-148">`Null`, if all input values are `null` values.</span></span>

<span data-ttu-id="5866a-149">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-149">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdev)]
[!code-sql[DP EntityServices Concepts#EDM_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdev)]

### <a name="stdevpexpression"></a><span data-ttu-id="5866a-150">StDevP (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-150">StDevP(expression)</span></span>

<span data-ttu-id="5866a-151">Vrátí směrodatnou odchylku pro populace všech hodnot.</span><span class="sxs-lookup"><span data-stu-id="5866a-151">Returns the standard deviation for the population of all values.</span></span>

<span data-ttu-id="5866a-152">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-152">**Arguments**</span></span>

<span data-ttu-id="5866a-153">A, `Int64`, ,.`Decimal` `Double` `Int32`</span><span class="sxs-lookup"><span data-stu-id="5866a-153">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="5866a-154">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-154">**Return Value**</span></span>

<span data-ttu-id="5866a-155">A `Double`, nebo `null` Pokud jsou `null` všechny vstupní hodnoty hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5866a-155">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="5866a-156">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-156">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_stdevp)]
[!code-sql[DP EntityServices Concepts#EDM_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_stdevp)]

### <a name="sumexpression"></a><span data-ttu-id="5866a-157">Sum (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-157">Sum(expression)</span></span>

<span data-ttu-id="5866a-158">Vrátí součet hodnot, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="5866a-158">Returns the sum of the non-null values.</span></span>

<span data-ttu-id="5866a-159">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-159">**Arguments**</span></span>

<span data-ttu-id="5866a-160">A, `Int64`, ,.`Decimal` `Double` `Int32`</span><span class="sxs-lookup"><span data-stu-id="5866a-160">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="5866a-161">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-161">**Return Value**</span></span>

<span data-ttu-id="5866a-162">A `Double`, nebo `null` Pokud jsou `null` všechny vstupní hodnoty hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5866a-162">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="5866a-163">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-163">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_sum)]
[!code-sql[DP EntityServices Concepts#EDM_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_sum)]

### <a name="varexpression"></a><span data-ttu-id="5866a-164">Var (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-164">Var(expression)</span></span>

<span data-ttu-id="5866a-165">Vrátí odchylku všech hodnot, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="5866a-165">Returns the variance of all non-null values.</span></span>

<span data-ttu-id="5866a-166">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-166">**Arguments**</span></span>

<span data-ttu-id="5866a-167">A, `Int64`, ,.`Decimal` `Double` `Int32`</span><span class="sxs-lookup"><span data-stu-id="5866a-167">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="5866a-168">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-168">**Return Value**</span></span>

<span data-ttu-id="5866a-169">A `Double`, nebo `null` Pokud jsou `null` všechny vstupní hodnoty hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5866a-169">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="5866a-170">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-170">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_var)]
[!code-sql[DP EntityServices Concepts#EDM_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_var)]

### <a name="varpexpression"></a><span data-ttu-id="5866a-171">VarP (výraz)</span><span class="sxs-lookup"><span data-stu-id="5866a-171">VarP(expression)</span></span>

<span data-ttu-id="5866a-172">Vrátí odchylku pro populace všech hodnot, které nejsou null.</span><span class="sxs-lookup"><span data-stu-id="5866a-172">Returns the variance for the population of all non-null values.</span></span>

<span data-ttu-id="5866a-173">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="5866a-173">**Arguments**</span></span>

<span data-ttu-id="5866a-174">A, `Int64`, ,.`Decimal` `Double` `Int32`</span><span class="sxs-lookup"><span data-stu-id="5866a-174">An `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="5866a-175">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="5866a-175">**Return Value**</span></span>

<span data-ttu-id="5866a-176">A `Double`, nebo `null` Pokud jsou `null` všechny vstupní hodnoty hodnoty.</span><span class="sxs-lookup"><span data-stu-id="5866a-176">A `Double`, or `null` if all input values are `null` values.</span></span>

<span data-ttu-id="5866a-177">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="5866a-177">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_varp)]
[!code-sql[DP EntityServices Concepts#EDM_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_varp)]

<span data-ttu-id="5866a-178">Ekvivalentní funkce jsou k dispozici ve spravovaném zprostředkovateli klienta Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="5866a-178">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="5866a-179">Další informace najdete v tématu [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="5866a-179">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>

## <a name="collection-based-aggregates"></a><span data-ttu-id="5866a-180">Agregace založené na kolekcích</span><span class="sxs-lookup"><span data-stu-id="5866a-180">Collection-based aggregates</span></span>

<span data-ttu-id="5866a-181">Agregace založené na kolekcích (funkce kolekce) fungují na kolekcích a vracejí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5866a-181">Collection-based aggregates (collection functions) operate on collections and return a value.</span></span> <span data-ttu-id="5866a-182">Například pokud jsou objednávky kolekcí všech objednávek, můžete vypočítat nejbližší datum expedice následujícím výrazem:</span><span class="sxs-lookup"><span data-stu-id="5866a-182">For example if ORDERS is a collection of all orders, you can calculate the earliest ship date with the following expression:</span></span>

```sql
min(select value o.ShipDate from LOB.Orders as o)
```

<span data-ttu-id="5866a-183">Výrazy uvnitř agregace založené na kolekcích jsou vyhodnocovány v rámci aktuálního oboru rozlišení názvu okolí.</span><span class="sxs-lookup"><span data-stu-id="5866a-183">Expressions inside collection-based aggregates are evaluated within the current ambient name-resolution scope.</span></span>

## <a name="group-based-aggregates"></a><span data-ttu-id="5866a-184">Agregace založené na skupinách</span><span class="sxs-lookup"><span data-stu-id="5866a-184">Group-based aggregates</span></span>

<span data-ttu-id="5866a-185">Agregace založené na skupinách se počítají na základě skupiny definované klauzulí GROUP BY.</span><span class="sxs-lookup"><span data-stu-id="5866a-185">Group-based aggregates are calculated over a group as defined by the GROUP BY clause.</span></span> <span data-ttu-id="5866a-186">Pro každou skupinu ve výsledku se samostatné agregace vypočítávají pomocí prvků v každé skupině jako vstup agregačního výpočtu.</span><span class="sxs-lookup"><span data-stu-id="5866a-186">For each group in the result, a separate aggregate is calculated by using the elements in each group as input to the aggregate calculation.</span></span> <span data-ttu-id="5866a-187">Pokud je ve výrazu SELECT použita klauzule GROUP by, lze v klauzuli projekce nebo ORDER-by vyskytovat pouze názvy výrazů seskupení, agregace nebo konstantní výrazy.</span><span class="sxs-lookup"><span data-stu-id="5866a-187">When a group-by clause is used in a select expression, only grouping expression names, aggregates, or constant expressions can be present in the projection or order-by clause.</span></span>

<span data-ttu-id="5866a-188">Následující příklad vypočítá průměrné množství objednaného pro každý produkt:</span><span class="sxs-lookup"><span data-stu-id="5866a-188">The following example calculates the average quantity ordered for each product:</span></span>

```sql
select p, avg(ol.Quantity) from LOB.OrderLines as ol
  group by ol.Product as p
```

<span data-ttu-id="5866a-189">Je možné mít agregaci založenou na skupině bez explicitní klauzule GROUP by ve výrazu SELECT.</span><span class="sxs-lookup"><span data-stu-id="5866a-189">It's possible to have a group-based aggregate without an explicit group-by clause in the SELECT expression.</span></span> <span data-ttu-id="5866a-190">V tomto případě jsou všechny prvky považovány za jednu skupinu.</span><span class="sxs-lookup"><span data-stu-id="5866a-190">In this case, all elements are treated as a single group.</span></span> <span data-ttu-id="5866a-191">Jedná se o ekvivalent zadání seskupení na základě konstanty.</span><span class="sxs-lookup"><span data-stu-id="5866a-191">This is equivalent of specifying a grouping based on a constant.</span></span> <span data-ttu-id="5866a-192">Vezměte například následující výraz:</span><span class="sxs-lookup"><span data-stu-id="5866a-192">Take, for example, the following expression:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol
```

<span data-ttu-id="5866a-193">To je ekvivalentní následujícímu:</span><span class="sxs-lookup"><span data-stu-id="5866a-193">This is equivalent to the following:</span></span>

```sql
select avg(ol.Quantity) from LOB.OrderLines as ol group by 1
```

<span data-ttu-id="5866a-194">Výrazy uvnitř agregace založené na skupinách jsou vyhodnocovány v rámci oboru překladu názvů, který by byl viditelný pro výraz klauzule WHERE.</span><span class="sxs-lookup"><span data-stu-id="5866a-194">Expressions inside the group-based aggregate are evaluated within the name-resolution scope that would be visible to the WHERE clause expression.</span></span>

<span data-ttu-id="5866a-195">Stejně jako v jazyce Transact-SQL, agregace založené na skupinách mohou také určovat modifikátor ALL nebo DISTINCT.</span><span class="sxs-lookup"><span data-stu-id="5866a-195">As in Transact-SQL, group-based aggregates can also specify an ALL or DISTINCT modifier.</span></span> <span data-ttu-id="5866a-196">Je-li zadán modifikátor DISTINCT, jsou duplicity z agregované vstupní kolekce odstraněny před vypočítáním agregace.</span><span class="sxs-lookup"><span data-stu-id="5866a-196">If the DISTINCT modifier is specified, duplicates are eliminated from the aggregate input collection, before the aggregate is computed.</span></span> <span data-ttu-id="5866a-197">Pokud je zadán modifikátor ALL (nebo pokud není zadán modifikátor), není provedeno žádné duplicitní eliminace.</span><span class="sxs-lookup"><span data-stu-id="5866a-197">If the ALL modifier is specified (or if no modifier is specified), no duplicate elimination is performed.</span></span>

## <a name="see-also"></a><span data-ttu-id="5866a-198">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5866a-198">See also</span></span>

- [<span data-ttu-id="5866a-199">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="5866a-199">Canonical Functions</span></span>](canonical-functions.md)
