---
title: Agregační funkce (SqlClient pro Entity Framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 3dbd4c0a24a5fc41153ea16747325e824669b0e5
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700048"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="6a6ba-102">Agregační funkce (SqlClient pro Entity Framework)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="6a6ba-103">.NET Framework Zprostředkovatel dat pro SQL Server (SqlClient) poskytuje agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="6a6ba-104">Agregační funkce provádějí výpočty se sadou vstupních hodnot a vracejí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="6a6ba-105">Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití nástroje SqlClient.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="6a6ba-106">Vlastnost Namespace poskytovatele umožňuje Entity Framework zjistit, která předpona je používána tímto poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="6a6ba-107">Níže jsou uvedené agregační funkce SqlClient.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="6a6ba-108">Prům (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-108">AVG(expression)</span></span>

<span data-ttu-id="6a6ba-109">Vrátí průměr hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="6a6ba-110">Hodnoty null jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-110">Null values are ignored.</span></span>

<span data-ttu-id="6a6ba-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-111">**Arguments**</span></span>

<span data-ttu-id="6a6ba-112">`Int32`, `Int64`, `Double`a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="6a6ba-113">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-113">**Return Value**</span></span>

<span data-ttu-id="6a6ba-114">Typ připojení `expression`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-114">The type of `expression`.</span></span>

<span data-ttu-id="6a6ba-115">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="6a6ba-116">CHECKSUM_AGG (kolekce)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-116">CHECKSUM_AGG(collection)</span></span>
 
 <span data-ttu-id="6a6ba-117">Vrátí kontrolní součet hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="6a6ba-118">Hodnoty null jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-118">Null values are ignored.</span></span>
 
 <span data-ttu-id="6a6ba-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-119">**Arguments**</span></span>
 
 <span data-ttu-id="6a6ba-120">Kolekce (`Int32`).</span><span class="sxs-lookup"><span data-stu-id="6a6ba-120">A Collection(`Int32`).</span></span>
 
 <span data-ttu-id="6a6ba-121">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-121">**Return Value**</span></span>
 
 <span data-ttu-id="6a6ba-122">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-122">An `Int32`.</span></span>
 
 <span data-ttu-id="6a6ba-123">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-123">**Example**</span></span>
 
[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]
   
## <a name="countexpression"></a><span data-ttu-id="6a6ba-124">COUNT (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-124">COUNT(expression)</span></span>

<span data-ttu-id="6a6ba-125">Vrátí počet položek v kolekci jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="6a6ba-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-126">**Arguments**</span></span>

<span data-ttu-id="6a6ba-127">Kolekce\<T >, kde T je jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="6a6ba-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="6a6ba-128">`Guid` (nevráceno v SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="6a6ba-129">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-129">**Return Value**</span></span>

<span data-ttu-id="6a6ba-130">`Int32`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-130">An `Int32`.</span></span>

<span data-ttu-id="6a6ba-131">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]
 
## <a name="count_bigexpression"></a><span data-ttu-id="6a6ba-132">COUNT_BIG (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-132">COUNT_BIG(expression)</span></span>
 
<span data-ttu-id="6a6ba-133">Vrátí počet položek v kolekci jako `bigint`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-133">Returns the number of items in a collection as a `bigint`.</span></span>
 
 <span data-ttu-id="6a6ba-134">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-134">**Arguments**</span></span>
 
 <span data-ttu-id="6a6ba-135">Kolekce (T), kde T je jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="6a6ba-135">A Collection(T), where T is one of the following types:</span></span>
 
 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="6a6ba-136">`Guid` (nevráceno v SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="6a6ba-137">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-137">**Return Value**</span></span>

<span data-ttu-id="6a6ba-138">`Int64`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-138">An `Int64`.</span></span>

<span data-ttu-id="6a6ba-139">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="6a6ba-140">MAX (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-140">MAX(expression)</span></span>

<span data-ttu-id="6a6ba-141">Vrátí maximální hodnotu kolekce.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="6a6ba-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-142">**Arguments**</span></span>

<span data-ttu-id="6a6ba-143">Kolekce (T), kde T je jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="6a6ba-143">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="6a6ba-144">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-144">**Return Value**</span></span>

<span data-ttu-id="6a6ba-145">Typ připojení `expression`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-145">The type of `expression`.</span></span>

<span data-ttu-id="6a6ba-146">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="6a6ba-147">MIN (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-147">MIN(expression)</span></span>

<span data-ttu-id="6a6ba-148">Vrátí minimální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="6a6ba-149">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-149">**Arguments**</span></span>

<span data-ttu-id="6a6ba-150">Kolekce (T), kde T je jeden z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="6a6ba-150">A Collection(T), where T is one of the following types:</span></span> 

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="6a6ba-151">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-151">**Return Value**</span></span>

<span data-ttu-id="6a6ba-152">Typ připojení `expression`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-152">The type of `expression`.</span></span>

<span data-ttu-id="6a6ba-153">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="6a6ba-154">STDEV (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-154">STDEV(expression)</span></span>

<span data-ttu-id="6a6ba-155">Vrátí statistickou směrodatnou odchylku všech hodnot v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="6a6ba-156">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-156">**Arguments**</span></span>

<span data-ttu-id="6a6ba-157">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="6a6ba-157">A Collection(`Double`).</span></span>

<span data-ttu-id="6a6ba-158">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-158">**Return Value**</span></span>

<span data-ttu-id="6a6ba-159">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-159">A `Double`.</span></span>

<span data-ttu-id="6a6ba-160">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="6a6ba-161">STDEVP (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-161">STDEVP(expression)</span></span>

<span data-ttu-id="6a6ba-162">Vrátí statistickou směrodatnou odchylku pro populace všech hodnot v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="6a6ba-163">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-163">**Arguments**</span></span>

<span data-ttu-id="6a6ba-164">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="6a6ba-164">A Collection(`Double`).</span></span>

<span data-ttu-id="6a6ba-165">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-165">**Return Value**</span></span>

<span data-ttu-id="6a6ba-166">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-166">A `Double`.</span></span>

<span data-ttu-id="6a6ba-167">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="6a6ba-168">SUM (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-168">SUM(expression)</span></span>

<span data-ttu-id="6a6ba-169">Vrátí součet všech hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="6a6ba-170">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-170">**Arguments**</span></span>

<span data-ttu-id="6a6ba-171">Kolekce (T), kde T je jeden z následujících typů: `Int32`, `Int64`, `Double`, `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="6a6ba-172">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-172">**Return Value**</span></span>

<span data-ttu-id="6a6ba-173">Typ připojení `expression`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-173">The type of `expression`.</span></span>

<span data-ttu-id="6a6ba-174">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="6a6ba-175">VAR (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-175">VAR(expression)</span></span>

<span data-ttu-id="6a6ba-176">Vrátí statistickou odchylku všech hodnot v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="6a6ba-177">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-177">**Arguments**</span></span>

<span data-ttu-id="6a6ba-178">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="6a6ba-178">A Collection(`Double`).</span></span>

<span data-ttu-id="6a6ba-179">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-179">**Return Value**</span></span>

<span data-ttu-id="6a6ba-180">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-180">A `Double`.</span></span>

<span data-ttu-id="6a6ba-181">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="6a6ba-182">VARP (výraz)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-182">VARP(expression)</span></span>

<span data-ttu-id="6a6ba-183">Vrátí statistickou odchylku pro populace pro všechny hodnoty v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="6a6ba-184">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-184">**Arguments**</span></span>

<span data-ttu-id="6a6ba-185">Kolekce (`Double`).</span><span class="sxs-lookup"><span data-stu-id="6a6ba-185">A Collection(`Double`).</span></span>

<span data-ttu-id="6a6ba-186">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-186">**Return Value**</span></span>

<span data-ttu-id="6a6ba-187">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="6a6ba-187">A `Double`.</span></span>

<span data-ttu-id="6a6ba-188">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="6a6ba-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)] 
  
## <a name="see-also"></a><span data-ttu-id="6a6ba-189">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6a6ba-189">See also</span></span>

- [<span data-ttu-id="6a6ba-190">Agregační funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="6a6ba-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="6a6ba-191">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="6a6ba-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="6a6ba-192">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="6a6ba-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
