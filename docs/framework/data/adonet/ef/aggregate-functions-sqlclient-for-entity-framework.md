---
title: Agregační funkce (SqlClient pro entity framework)
ms.date: 03/30/2017
ms.assetid: 03303f01-b591-4efc-9875-f9c608edff0b
ms.openlocfilehash: 1fad25f2229b4fa810cf82a96dcb8c50a9de3070
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150646"
---
# <a name="aggregate-functions-sqlclient-for-entity-framework"></a><span data-ttu-id="a8ffd-102">Agregační funkce (SqlClient pro entity framework)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-102">Aggregate Functions (SqlClient for Entity Framework)</span></span>
<span data-ttu-id="a8ffd-103">Zprostředkovatel dat rozhraní .NET Framework pro SQL Server (SQLClient) poskytuje agregační funkce.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides aggregate functions.</span></span> <span data-ttu-id="a8ffd-104">Agregační funkce provádějí výpočty na sadě vstupních hodnot a vracejí hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-104">Aggregate functions perform calculations on a set of input values and return a value.</span></span> <span data-ttu-id="a8ffd-105">Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití příkazu SqlClient.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-105">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="a8ffd-106">Vlastnost oboru názvů zprostředkovatele umožňuje entity Framework zjistit, která předpona je používána tímto zprostředkovatelem pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-106">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span>  
  
 <span data-ttu-id="a8ffd-107">Následují agregační funkce SqlClient.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-107">The following are the SqlClient aggregate functions.</span></span>  

## <a name="avgexpression"></a><span data-ttu-id="a8ffd-108">AVG(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-108">AVG(expression)</span></span>

<span data-ttu-id="a8ffd-109">Vrátí průměr hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-109">Returns the average of the values in a collection.</span></span> <span data-ttu-id="a8ffd-110">Hodnoty Null jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-110">Null values are ignored.</span></span>

<span data-ttu-id="a8ffd-111">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-111">**Arguments**</span></span>

<span data-ttu-id="a8ffd-112">An `Int32` `Int64`, `Double`, `Decimal`a .</span><span class="sxs-lookup"><span data-stu-id="a8ffd-112">An `Int32`, `Int64`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="a8ffd-113">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-113">**Return Value**</span></span>

<span data-ttu-id="a8ffd-114">Typ . `expression`</span><span class="sxs-lookup"><span data-stu-id="a8ffd-114">The type of `expression`.</span></span>

<span data-ttu-id="a8ffd-115">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-115">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_AVG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_avg)]

## <a name="checksum_aggcollection"></a><span data-ttu-id="a8ffd-116">CHECKSUM_AGG(sběr)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-116">CHECKSUM_AGG(collection)</span></span>

 <span data-ttu-id="a8ffd-117">Vrátí kontrolní součet hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-117">Returns the checksum of the values in a collection.</span></span> <span data-ttu-id="a8ffd-118">Hodnoty Null jsou ignorovány.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-118">Null values are ignored.</span></span>

 <span data-ttu-id="a8ffd-119">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-119">**Arguments**</span></span>

 <span data-ttu-id="a8ffd-120">Sbírka(`Int32`).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-120">A Collection(`Int32`).</span></span>

 <span data-ttu-id="a8ffd-121">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-121">**Return Value**</span></span>

 <span data-ttu-id="a8ffd-122">A `Int32`.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-122">An `Int32`.</span></span>

 <span data-ttu-id="a8ffd-123">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-123">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CHECKSUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_checksum)]

## <a name="countexpression"></a><span data-ttu-id="a8ffd-124">COUNT(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-124">COUNT(expression)</span></span>

<span data-ttu-id="a8ffd-125">Vrátí počet položek v kolekci `Int32`jako .</span><span class="sxs-lookup"><span data-stu-id="a8ffd-125">Returns the number of items in a collection as an `Int32`.</span></span>

<span data-ttu-id="a8ffd-126">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-126">**Arguments**</span></span>

<span data-ttu-id="a8ffd-127">A\<Kolekce T>, kde T je jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-127">A Collection\<T>, where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="a8ffd-128">`Guid`(není vrácena v SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-128">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="a8ffd-129">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-129">**Return Value**</span></span>

<span data-ttu-id="a8ffd-130">A `Int32`.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-130">An `Int32`.</span></span>

<span data-ttu-id="a8ffd-131">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-131">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNT](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_count)]

## <a name="count_bigexpression"></a><span data-ttu-id="a8ffd-132">COUNT_BIG(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-132">COUNT_BIG(expression)</span></span>

<span data-ttu-id="a8ffd-133">Vrátí počet položek v kolekci `bigint`jako .</span><span class="sxs-lookup"><span data-stu-id="a8ffd-133">Returns the number of items in a collection as a `bigint`.</span></span>

 <span data-ttu-id="a8ffd-134">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-134">**Arguments**</span></span>

 <span data-ttu-id="a8ffd-135">A Collection(T), kde T je jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-135">A Collection(T), where T is one of the following types:</span></span>

 |   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`|<span data-ttu-id="a8ffd-136">`Guid`(není vrácena v SQL Server 2000)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-136">`Guid` (not returned in SQL Server 2000)</span></span>|

<span data-ttu-id="a8ffd-137">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-137">**Return Value**</span></span>

<span data-ttu-id="a8ffd-138">A `Int64`.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-138">An `Int64`.</span></span>

<span data-ttu-id="a8ffd-139">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-139">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_COUNTBIG](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_countbig)]

## <a name="maxexpression"></a><span data-ttu-id="a8ffd-140">MAX(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-140">MAX(expression)</span></span>

<span data-ttu-id="a8ffd-141">Vrátí maximální hodnotu kolekce.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-141">Returns the maximum value the collection.</span></span>

<span data-ttu-id="a8ffd-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-142">**Arguments**</span></span>

<span data-ttu-id="a8ffd-143">A Collection(T), kde T je jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-143">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="a8ffd-144">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-144">**Return Value**</span></span>

<span data-ttu-id="a8ffd-145">Typ . `expression`</span><span class="sxs-lookup"><span data-stu-id="a8ffd-145">The type of `expression`.</span></span>

<span data-ttu-id="a8ffd-146">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-146">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MAX](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_max)]

## <a name="minexpression"></a><span data-ttu-id="a8ffd-147">MIN(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-147">MIN(expression)</span></span>

<span data-ttu-id="a8ffd-148">Vrátí minimální hodnotu v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-148">Returns the minimum value in a collection.</span></span>

<span data-ttu-id="a8ffd-149">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-149">**Arguments**</span></span>

<span data-ttu-id="a8ffd-150">A Collection(T), kde T je jedním z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="a8ffd-150">A Collection(T), where T is one of the following types:</span></span>

|   |   |   |   |
|---|---|---|---|
|`Boolean`|`Double`|`DateTime`|`DateTimeOffset`|
|`Time`|`String`|`Binary`||

<span data-ttu-id="a8ffd-151">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-151">**Return Value**</span></span>

<span data-ttu-id="a8ffd-152">Typ . `expression`</span><span class="sxs-lookup"><span data-stu-id="a8ffd-152">The type of `expression`.</span></span>

<span data-ttu-id="a8ffd-153">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-153">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_MIN](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_min)]

## <a name="stdevexpression"></a><span data-ttu-id="a8ffd-154">STDEV(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-154">STDEV(expression)</span></span>

<span data-ttu-id="a8ffd-155">Vrátí statistickou směrodatnou odchylku všech hodnot v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-155">Returns the statistical standard deviation of all values in the specified expression.</span></span>

<span data-ttu-id="a8ffd-156">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-156">**Arguments**</span></span>

<span data-ttu-id="a8ffd-157">Sbírka(`Double`).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-157">A Collection(`Double`).</span></span>

<span data-ttu-id="a8ffd-158">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-158">**Return Value**</span></span>

<span data-ttu-id="a8ffd-159">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-159">A `Double`.</span></span>

<span data-ttu-id="a8ffd-160">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-160">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEV](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdev)]

## <a name="stdevpexpression"></a><span data-ttu-id="a8ffd-161">STDEVP(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-161">STDEVP(expression)</span></span>

<span data-ttu-id="a8ffd-162">Vrátí statistickou směrodatnou odchylku pro základní soubor pro všechny hodnoty v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-162">Returns the statistical standard deviation for the population for all values in the specified expression.</span></span>

<span data-ttu-id="a8ffd-163">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-163">**Arguments**</span></span>

<span data-ttu-id="a8ffd-164">Sbírka(`Double`).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-164">A Collection(`Double`).</span></span>

<span data-ttu-id="a8ffd-165">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-165">**Return Value**</span></span>

<span data-ttu-id="a8ffd-166">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-166">A `Double`.</span></span>

<span data-ttu-id="a8ffd-167">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-167">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_STDEVP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_stdevp)]

## <a name="sumexpression"></a><span data-ttu-id="a8ffd-168">SUMA(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-168">SUM(expression)</span></span>

<span data-ttu-id="a8ffd-169">Vrátí součet všech hodnot v kolekci.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-169">Returns the sum of all the values in the collection.</span></span>

<span data-ttu-id="a8ffd-170">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-170">**Arguments**</span></span>

<span data-ttu-id="a8ffd-171">A Collection(T), kde T je jedním `Int32` `Int64`z `Double` `Decimal`následujících typů: , , , .</span><span class="sxs-lookup"><span data-stu-id="a8ffd-171">A Collection(T) where T is one of the following types: `Int32`, `Int64`, `Double`, `Decimal`.</span></span>

<span data-ttu-id="a8ffd-172">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-172">**Return Value**</span></span>

<span data-ttu-id="a8ffd-173">Typ . `expression`</span><span class="sxs-lookup"><span data-stu-id="a8ffd-173">The type of `expression`.</span></span>

<span data-ttu-id="a8ffd-174">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-174">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_SUM](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_sum)]

## <a name="varexpression"></a><span data-ttu-id="a8ffd-175">VAR(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-175">VAR(expression)</span></span>

<span data-ttu-id="a8ffd-176">Vrátí statistickou odchylku všech hodnot v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-176">Returns the statistical variance of all values in the specified expression.</span></span>

<span data-ttu-id="a8ffd-177">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-177">**Arguments**</span></span>

<span data-ttu-id="a8ffd-178">Sbírka(`Double`).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-178">A Collection(`Double`).</span></span>

<span data-ttu-id="a8ffd-179">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-179">**Return Value**</span></span>

<span data-ttu-id="a8ffd-180">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-180">A `Double`.</span></span>

<span data-ttu-id="a8ffd-181">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-181">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VAR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_var)]

## <a name="varpexpression"></a><span data-ttu-id="a8ffd-182">VARP(výraz)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-182">VARP(expression)</span></span>

<span data-ttu-id="a8ffd-183">Vrátí statistickou odchylku pro základní soubor pro všechny hodnoty v zadaném výrazu.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-183">Returns the statistical variance for the population for all values in the specified expression.</span></span>

<span data-ttu-id="a8ffd-184">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-184">**Arguments**</span></span>

<span data-ttu-id="a8ffd-185">Sbírka(`Double`).</span><span class="sxs-lookup"><span data-stu-id="a8ffd-185">A Collection(`Double`).</span></span>

<span data-ttu-id="a8ffd-186">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-186">**Return Value**</span></span>

<span data-ttu-id="a8ffd-187">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="a8ffd-187">A `Double`.</span></span>

<span data-ttu-id="a8ffd-188">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="a8ffd-188">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_VARP](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_varp)]
  
## <a name="see-also"></a><span data-ttu-id="a8ffd-189">Viz také</span><span class="sxs-lookup"><span data-stu-id="a8ffd-189">See also</span></span>

- [<span data-ttu-id="a8ffd-190">Agregační funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="a8ffd-190">Aggregate Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/aggregate-functions-transact-sql)
- [<span data-ttu-id="a8ffd-191">Jazyk Entity SQL</span><span class="sxs-lookup"><span data-stu-id="a8ffd-191">Entity SQL Language</span></span>](./language-reference/entity-sql-language.md)
- [<span data-ttu-id="a8ffd-192">Agregační kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="a8ffd-192">Aggregate Canonical Functions</span></span>](./language-reference/aggregate-canonical-functions.md)
