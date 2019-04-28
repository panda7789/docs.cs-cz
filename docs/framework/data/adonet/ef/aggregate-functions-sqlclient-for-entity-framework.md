---
title: Agregační funkce (SqlClient pro Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: f2f2b557cd9f126ddd513a0f42d3ac95114c3822
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61606766"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="d96ce-102">Agregační funkce (SqlClient pro Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="d96ce-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="d96ce-103">Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="d96ce-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="d96ce-104">Agregační funkce provádění výpočtů na sadě vstupní hodnoty a vrátí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d96ce-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="d96ce-105">Tyto funkce jsou v oboru názvů systému SQL Server, která je k dispozici, když použijete SqlClient.</span><span class="sxs-lookup"><span data-stu-id="d96ce-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="d96ce-106">Vlastnost oboru názvů poskytovatele umožňuje zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d96ce-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="d96ce-107">Následují SqlClient agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="d96ce-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="d96ce-108">AVG(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-108">AVG(expression)</span></span>

<span data-ttu-id="d96ce-109">Vrátí průměr hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d96ce-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="d96ce-110">Hodnoty Null se ignorují.</span><span class="sxs-lookup"><span data-stu-id="d96ce-110">Null values are ignored.</span></span>

<span data-ttu-id="d96ce-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-111">**Arguments**</span></span>

<span data-ttu-id="d96ce-112">`Int32`, `Int64`, `Double`, A `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="d96ce-113">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-113">**Return Value**</span></span>

<span data-ttu-id="d96ce-114">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-114">The type of `expression`.</span></span>

<span data-ttu-id="d96ce-115">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-115">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_avg)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksumaggcollection"></a><span data-ttu-id="d96ce-116">CHECKSUM_AGG(Collection)</span><span class="sxs-lookup"><span data-stu-id="d96ce-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="d96ce-117">Vrátí součet hodnoty v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d96ce-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="d96ce-118">Hodnoty Null se ignorují.</span><span class="sxs-lookup"><span data-stu-id="d96ce-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="d96ce-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-119">**Arguments**</span></span>
 
 <span data-ttu-id="d96ce-120">Kolekce (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="d96ce-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="d96ce-121">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-121">**Return Value**</span></span>
 
 <span data-ttu-id="d96ce-122">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-122">An `Int32`.</span></span>
 
 <span data-ttu-id="d96ce-123">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-123">**Example**</span></span>
 
 [!code-csharp[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_checksum)]
 [!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="d96ce-124">Count(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-124">COUNT(expression)</span></span>

<span data-ttu-id="d96ce-125">Vrátí počet položek v kolekci jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="d96ce-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-126">**Arguments**</span></span>

<span data-ttu-id="d96ce-127">Kolekce\<T >, kde T je jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="d96ce-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="d96ce-128">`Guid` (nevrací se v systému SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="d96ce-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="d96ce-129">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-129">**Return Value**</span></span>

<span data-ttu-id="d96ce-130">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-130">An `Int32`.</span></span>

<span data-ttu-id="d96ce-131">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-131">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_count)]
<span data-ttu-id="d96ce-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span><span class="sxs-lookup"><span data-stu-id="d96ce-132">[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)</span></span>
 
## <a name="countbigexpression"></a><span data-ttu-id="d96ce-133">COUNT_BIG(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-133">COUNT_BIG(expression)</span></span>
 
 <span data-ttu-id="d96ce-134">Vrátí počet položek v kolekci jako `bigint`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-134">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="d96ce-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-135">**Arguments**</span></span>
 
 <span data-ttu-id="d96ce-136">Collection(T) kde T je jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="d96ce-136">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="d96ce-137">`Guid` (nevrací se v systému SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="d96ce-137">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="d96ce-138">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-138">**Return Value**</span></span>

<span data-ttu-id="d96ce-139">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-139">An `Int64`.</span></span>

<span data-ttu-id="d96ce-140">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-140">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_countbig)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="d96ce-141">Max(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-141">MAX(expression)</span></span>

<span data-ttu-id="d96ce-142">Vrátí maximální hodnotu kolekce.</span><span class="sxs-lookup"><span data-stu-id="d96ce-142">Returns the maximum value the collection.</span></span>

<span data-ttu-id="d96ce-143">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-143">**Arguments**</span></span>

<span data-ttu-id="d96ce-144">Collection(T) kde T je jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="d96ce-144">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="d96ce-145">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-145">**Return Value**</span></span>

<span data-ttu-id="d96ce-146">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-146">The type of `expression`.</span></span>

<span data-ttu-id="d96ce-147">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-147">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_max)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="d96ce-148">MIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-148">MIN(expression)</span></span>

<span data-ttu-id="d96ce-149">Vrátí minimální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d96ce-149">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="d96ce-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-150">**Arguments**</span></span>

<span data-ttu-id="d96ce-151">Collection(T) kde T je jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="d96ce-151">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="d96ce-152">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-152">**Return Value**</span></span>

<span data-ttu-id="d96ce-153">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-153">The type of `expression`.</span></span>

<span data-ttu-id="d96ce-154">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-154">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_min)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="d96ce-155">StDev(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-155">STDEV(expression)</span></span>

<span data-ttu-id="d96ce-156">Vrátí statistické směrodatnou odchylku všech hodnot v zadaným výrazem.</span><span class="sxs-lookup"><span data-stu-id="d96ce-156">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="d96ce-157">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-157">**Arguments**</span></span>

<span data-ttu-id="d96ce-158">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="d96ce-158">A Collection(`Double`).</span></span>

<span data-ttu-id="d96ce-159">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-159">**Return Value**</span></span>

<span data-ttu-id="d96ce-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-160">A `Double`.</span></span>

<span data-ttu-id="d96ce-161">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-161">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdev)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="d96ce-162">StDevP(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-162">STDEVP(expression)</span></span>

<span data-ttu-id="d96ce-163">Vrátí statistické směrodatnou odchylku základního souboru pro všechny hodnoty v zadaným výrazem.</span><span class="sxs-lookup"><span data-stu-id="d96ce-163">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="d96ce-164">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-164">**Arguments**</span></span>

<span data-ttu-id="d96ce-165">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="d96ce-165">A Collection(`Double`).</span></span>

<span data-ttu-id="d96ce-166">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-166">**Return Value**</span></span>

<span data-ttu-id="d96ce-167">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-167">A `Double`.</span></span>

<span data-ttu-id="d96ce-168">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-168">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_stdevp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="d96ce-169">SUM(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-169">SUM(expression)</span></span>

<span data-ttu-id="d96ce-170">Vrátí součet všech hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="d96ce-170">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="d96ce-171">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-171">**Arguments**</span></span>

<span data-ttu-id="d96ce-172">Collection(T), kde T je jedním z následujících typů: `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-172">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="d96ce-173">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-173">**Return Value**</span></span>

<span data-ttu-id="d96ce-174">Typ `expression`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-174">The type of `expression`.</span></span>

<span data-ttu-id="d96ce-175">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-175">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_sum)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="d96ce-176">VAR(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-176">VAR(expression)</span></span>

<span data-ttu-id="d96ce-177">Vrátí statistické odchylku všech hodnot v zadaným výrazem.</span><span class="sxs-lookup"><span data-stu-id="d96ce-177">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="d96ce-178">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-178">**Arguments**</span></span>

<span data-ttu-id="d96ce-179">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="d96ce-179">A Collection(`Double`).</span></span>

<span data-ttu-id="d96ce-180">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-180">**Return Value**</span></span>

<span data-ttu-id="d96ce-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-181">A `Double`.</span></span>

<span data-ttu-id="d96ce-182">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-182">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_var)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="d96ce-183">VarP(Expression)</span><span class="sxs-lookup"><span data-stu-id="d96ce-183">VARP(expression)</span></span>

<span data-ttu-id="d96ce-184">Vrátí statistické odchylku základního souboru pro všechny hodnoty v zadaným výrazem.</span><span class="sxs-lookup"><span data-stu-id="d96ce-184">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="d96ce-185">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="d96ce-185">**Arguments**</span></span>

<span data-ttu-id="d96ce-186">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="d96ce-186">A Collection(`Double`).</span></span>

<span data-ttu-id="d96ce-187">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="d96ce-187">**Return Value**</span></span>

<span data-ttu-id="d96ce-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="d96ce-188">A `Double`.</span></span>

<span data-ttu-id="d96ce-189">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="d96ce-189">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_varp)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="d96ce-190">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d96ce-190">See also</span></span>

<span data-ttu-id="d96ce-191">Další informace o použití agregačních funkcí, které SqlClient podporuje najdete v dokumentaci pro verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:</span><span class="sxs-lookup"><span data-stu-id="d96ce-191">For more information about the aggregate functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="d96ce-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="d96ce-192">**SQL Server 2005:** [Aggregate Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms173454(v=sql.90))</span></span>
- <span data-ttu-id="d96ce-193">**SQL Server 2008 nebo novější:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="d96ce-193">**SQL Server 2008 and later:** [Aggregate Functions (Transact-SQL)](/sql/t-sql/functions/aggregate-functions-transact-sql)</span></span>

- [<span data-ttu-id="d96ce-194">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="d96ce-194">Entity SQL Language</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md)
- [<span data-ttu-id="d96ce-195">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="d96ce-195">Aggregate Canonical Functions</span></span>](../../../../../docs/framework/data/adonet/ef/language-reference/aggregate-canonical-functions.md)
