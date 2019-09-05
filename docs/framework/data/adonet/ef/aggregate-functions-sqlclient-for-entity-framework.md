---
title: Agregační funkce (SqlClient pro Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: cf476192cf049f230c1956e390d215ad4abaa821
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251709"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="e33dd-102">Agregační funkce (SqlClient pro Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="e33dd-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="e33dd-103">.NET Framework Zprostředkovatel dat pro SQL Server (SqlClient) poskytuje agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="e33dd-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="e33dd-104">Agregační funkce provádějí výpočty se sadou vstupních hodnot a vracejí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="e33dd-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="e33dd-105">Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití nástroje SqlClient.</span><span class="sxs-lookup"><span data-stu-id="e33dd-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="e33dd-106">Vlastnost Namespace poskytovatele umožňuje Entity Framework zjistit, která předpona je používána tímto poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="e33dd-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="e33dd-107">Níže jsou uvedené agregační funkce SqlClient.</span><span class="sxs-lookup"><span data-stu-id="e33dd-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="e33dd-108">Prům (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-108">AVG(expression)</span></span>

<span data-ttu-id="e33dd-109">Vrátí průměr hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e33dd-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="e33dd-110">Hodnoty null jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="e33dd-110">Null values are ignored.</span></span>

<span data-ttu-id="e33dd-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-111">**Arguments**</span></span>

<span data-ttu-id="e33dd-112">A `Int32` ,`Int64`, a`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="e33dd-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="e33dd-113">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-113">**Return Value**</span></span>

<span data-ttu-id="e33dd-114">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-114">The type of `expression`.</span></span>

<span data-ttu-id="e33dd-115">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="e33dd-116">CHECKSUM_AGG (kolekce)</span><span class="sxs-lookup"><span data-stu-id="e33dd-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="e33dd-117">Vrátí kontrolní součet hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e33dd-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="e33dd-118">Hodnoty null jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="e33dd-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="e33dd-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-119">**Arguments**</span></span>
 
 <span data-ttu-id="e33dd-120">Kolekce (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="e33dd-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="e33dd-121">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-121">**Return Value**</span></span>
 
 <span data-ttu-id="e33dd-122">A `Int32`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-122">An `Int32`.</span></span>
 
 <span data-ttu-id="e33dd-123">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="e33dd-124">COUNT (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-124">COUNT(expression)</span></span>

<span data-ttu-id="e33dd-125">Vrátí počet položek v kolekci jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="e33dd-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-126">**Arguments**</span></span>

<span data-ttu-id="e33dd-127">Kolekce\<t >, kde t je jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="e33dd-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="e33dd-128">`Guid`(nevráceno v SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="e33dd-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="e33dd-129">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-129">**Return Value**</span></span>

<span data-ttu-id="e33dd-130">A `Int32`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-130">An `Int32`.</span></span>

<span data-ttu-id="e33dd-131">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="e33dd-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="e33dd-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="count_bigexpression"></a><span data-ttu-id="e33dd-133">COUNT_BIG (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="e33dd-134">Vrátí počet položek v kolekci jako `bigint`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="e33dd-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-135">**Arguments**</span></span>
 
 <span data-ttu-id="e33dd-136">Kolekce (T), kde T je jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="e33dd-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="e33dd-137">`Guid`(nevráceno v SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="e33dd-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="e33dd-138">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-138">**Return Value**</span></span>

<span data-ttu-id="e33dd-139">A `Int64`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-139">An `Int64`.</span></span>

<span data-ttu-id="e33dd-140">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="e33dd-141">MAX (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-141">MAX(expression)</span></span>

<span data-ttu-id="e33dd-142">Vrátí maximální hodnotu kolekce.</span><span class="sxs-lookup"><span data-stu-id="e33dd-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="e33dd-143">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-143">**Arguments**</span></span>

<span data-ttu-id="e33dd-144">Kolekce (T), kde T je jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="e33dd-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="e33dd-145">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-145">**Return Value**</span></span>

<span data-ttu-id="e33dd-146">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-146">The type of `expression`.</span></span>

<span data-ttu-id="e33dd-147">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="e33dd-148">MIN (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-148">MIN(expression)</span></span>

<span data-ttu-id="e33dd-149">Vrátí minimální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e33dd-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="e33dd-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-150">**Arguments**</span></span>

<span data-ttu-id="e33dd-151">Kolekce (T), kde T je jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="e33dd-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="e33dd-152">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-152">**Return Value**</span></span>

<span data-ttu-id="e33dd-153">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-153">The type of `expression`.</span></span>

<span data-ttu-id="e33dd-154">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="e33dd-155">STDEV (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-155">STDEV(expression)</span></span>

<span data-ttu-id="e33dd-156">Vrátí statistickou směrodatnou odchylku všech hodnot v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="e33dd-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="e33dd-157">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-157">**Arguments**</span></span>

<span data-ttu-id="e33dd-158">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="e33dd-158">A Collection(`Double`).</span></span>

<span data-ttu-id="e33dd-159">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-159">**Return Value**</span></span>

<span data-ttu-id="e33dd-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-160">A `Double`.</span></span>

<span data-ttu-id="e33dd-161">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="e33dd-162">STDEVP (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-162">STDEVP(expression)</span></span>

<span data-ttu-id="e33dd-163">Vrátí statistickou směrodatnou odchylku pro populace všech hodnot v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="e33dd-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="e33dd-164">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-164">**Arguments**</span></span>

<span data-ttu-id="e33dd-165">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="e33dd-165">A Collection(`Double`).</span></span>

<span data-ttu-id="e33dd-166">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-166">**Return Value**</span></span>

<span data-ttu-id="e33dd-167">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-167">A `Double`.</span></span>

<span data-ttu-id="e33dd-168">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="e33dd-169">SUM (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-169">SUM(expression)</span></span>

<span data-ttu-id="e33dd-170">Vrátí součet všech hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="e33dd-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="e33dd-171">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-171">**Arguments**</span></span>

<span data-ttu-id="e33dd-172">Kolekce (T), kde T je jeden z následujících typů `Int32`:, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="e33dd-173">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-173">**Return Value**</span></span>

<span data-ttu-id="e33dd-174">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-174">The type of `expression`.</span></span>

<span data-ttu-id="e33dd-175">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="e33dd-176">VAR (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-176">VAR(expression)</span></span>

<span data-ttu-id="e33dd-177">Vrátí statistickou odchylku všech hodnot v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="e33dd-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="e33dd-178">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-178">**Arguments**</span></span>

<span data-ttu-id="e33dd-179">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="e33dd-179">A Collection(`Double`).</span></span>

<span data-ttu-id="e33dd-180">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-180">**Return Value**</span></span>

<span data-ttu-id="e33dd-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-181">A `Double`.</span></span>

<span data-ttu-id="e33dd-182">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="e33dd-183">VARP (výraz)</span><span class="sxs-lookup"><span data-stu-id="e33dd-183">VARP(expression)</span></span>

<span data-ttu-id="e33dd-184">Vrátí statistickou odchylku pro populace pro všechny hodnoty v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="e33dd-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="e33dd-185">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="e33dd-185">**Arguments**</span></span>

<span data-ttu-id="e33dd-186">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="e33dd-186">A Collection(`Double`).</span></span>

<span data-ttu-id="e33dd-187">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="e33dd-187">**Return Value**</span></span>

<span data-ttu-id="e33dd-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="e33dd-188">A `Double`.</span></span>

<span data-ttu-id="e33dd-189">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="e33dd-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="e33dd-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e33dd-190">See also</span></span>

<span data-ttu-id="e33dd-191">Další informace o agregačních funkcích, které podporuje SqlClient, najdete v dokumentaci k verzi SQL Server, kterou jste zadali v manifestu zprostředkovatele SqlClient:</span><span class="sxs-lookup"><span data-stu-id="e33dd-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="e33dd-192">**SQL Server 2005:** [Agregační funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="e33dd-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="e33dd-193">**SQL Server 2008 a novější:** [Agregační funkce (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="e33dd-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- [<span data-ttu-id="e33dd-194">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="e33dd-194">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="e33dd-195">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="e33dd-195">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
