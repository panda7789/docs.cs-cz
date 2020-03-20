---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 4512aaa2eeb3e715a1d6f7a8655912eb15162124
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79149762"
---
# <a name="mathematical-functions"></a><span data-ttu-id="06a31-102">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="06a31-102">Mathematical Functions</span></span>

<span data-ttu-id="06a31-103">Zprostředkovatel dat rozhraní .NET Framework pro SQL Server (SQLClient) poskytuje matematické funkce, které provádějí výpočty vstupních hodnot, které jsou k dispozici jako argumenty, a vrací výsledek číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="06a31-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="06a31-104">Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití příkazu SqlClient.</span><span class="sxs-lookup"><span data-stu-id="06a31-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="06a31-105">Vlastnost oboru názvů zprostředkovatele umožňuje entity Framework zjistit, která předpona je používána tímto zprostředkovatelem pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="06a31-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="06a31-106">Následující tabulka popisuje matematické funkce SqlClient.</span><span class="sxs-lookup"><span data-stu-id="06a31-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="06a31-107">ABS(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-107">ABS(expression)</span></span>

<span data-ttu-id="06a31-108">Provede funkci absolutní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="06a31-108">Performs the absolute value function.</span></span>

<span data-ttu-id="06a31-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-109">**Arguments**</span></span>

<span data-ttu-id="06a31-110">`expression`: `Int32`An `Int64` `Double`, `Decimal`, , nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="06a31-111">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-111">**Return Value**</span></span>

<span data-ttu-id="06a31-112">Absolutní hodnota zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="06a31-113">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="06a31-114">ACOS(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-114">ACOS(expression)</span></span>

<span data-ttu-id="06a31-115">Vrátí hodnotu arccosine zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="06a31-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-116">**Arguments**</span></span>

<span data-ttu-id="06a31-117">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-118">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-118">**Return Value**</span></span>

<span data-ttu-id="06a31-119">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-119">A `Double`.</span></span>

<span data-ttu-id="06a31-120">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="06a31-121">ASIN(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-121">ASIN(expression)</span></span>

<span data-ttu-id="06a31-122">Vrátí hodnotu arcininu zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="06a31-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-123">**Arguments**</span></span>

<span data-ttu-id="06a31-124">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-125">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-125">**Return Value**</span></span>

<span data-ttu-id="06a31-126">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-126">A `Double`.</span></span>

<span data-ttu-id="06a31-127">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="06a31-128">ATAN(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-128">ATAN(expression)</span></span>

<span data-ttu-id="06a31-129">Vrátí hodnotu arctangent zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="06a31-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-130">**Arguments**</span></span>

<span data-ttu-id="06a31-131">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-132">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-132">**Return Value**</span></span>

<span data-ttu-id="06a31-133">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-133">A `Double`.</span></span>

<span data-ttu-id="06a31-134">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="06a31-135">ATN2(výraz, výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="06a31-136">Vrátí úhel v radiánech, jehož tečna je mezi dvěma určenými číselnými výrazy.</span><span class="sxs-lookup"><span data-stu-id="06a31-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="06a31-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-137">**Arguments**</span></span>

<span data-ttu-id="06a31-138">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-139">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-139">**Return Value**</span></span>

<span data-ttu-id="06a31-140">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-140">A `Double`.</span></span>

<span data-ttu-id="06a31-141">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`

## <a name="ceilingexpression"></a><span data-ttu-id="06a31-142">STROP (výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-142">CEILING(expression)</span></span>

<span data-ttu-id="06a31-143">Převede zadaný výraz na nejmenší celé číslo, které je větší nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="06a31-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="06a31-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-144">**Arguments**</span></span>

<span data-ttu-id="06a31-145">`expression`: `Int32`An `Int64` `Double`, `Decimal`, , nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="06a31-146">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-146">**Return Value**</span></span>

<span data-ttu-id="06a31-147">An `Int32` `Int64`, `Double`, `Decimal`, nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="06a31-148">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-148">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="06a31-149">COS(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-149">COS(expression)</span></span>

<span data-ttu-id="06a31-150">Vypočítá goniometrický kosinus zadaného úhlu v radiánech.</span><span class="sxs-lookup"><span data-stu-id="06a31-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span>

<span data-ttu-id="06a31-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-151">**Arguments**</span></span>

<span data-ttu-id="06a31-152">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-152">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-153">**Return Value**</span></span>

<span data-ttu-id="06a31-154">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-154">A `Double`.</span></span>

<span data-ttu-id="06a31-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-155">**Example**</span></span>

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="06a31-156">COT(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-156">COT(expression)</span></span>

<span data-ttu-id="06a31-157">Vypočítá goniometrický kotanans stanoveného úhlu v radiánech.</span><span class="sxs-lookup"><span data-stu-id="06a31-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span>

<span data-ttu-id="06a31-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-158">**Arguments**</span></span>

<span data-ttu-id="06a31-159">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-159">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-160">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-160">**Return Value**</span></span>

<span data-ttu-id="06a31-161">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-161">A `Double`.</span></span>

<span data-ttu-id="06a31-162">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-162">**Example**</span></span>

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="06a31-163">DEGREES (radiáty)</span><span class="sxs-lookup"><span data-stu-id="06a31-163">DEGREES(radians)</span></span>

<span data-ttu-id="06a31-164">Vrátí odpovídající úhel ve stupních.</span><span class="sxs-lookup"><span data-stu-id="06a31-164">Returns the corresponding angle in degrees.</span></span>

<span data-ttu-id="06a31-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-165">**Arguments**</span></span>

<span data-ttu-id="06a31-166">`expression`: `Int32`An `Int64` `Double`, `Decimal`, , nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="06a31-167">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-167">**Return Value**</span></span>

<span data-ttu-id="06a31-168">An `Int32` `Int64`, `Double`, `Decimal`, nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="06a31-169">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-169">**Example**</span></span>

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="06a31-170">EXP(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-170">EXP(expression)</span></span>

<span data-ttu-id="06a31-171">Vypočítá exponenciální hodnotu zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-171">Calculates the exponential value of a specified numeric expression.</span></span>

<span data-ttu-id="06a31-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-172">**Arguments**</span></span>

<span data-ttu-id="06a31-173">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-173">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-174">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-174">**Return Value**</span></span>

<span data-ttu-id="06a31-175">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-175">A `Double`.</span></span>

<span data-ttu-id="06a31-176">**Příklad**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="06a31-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="06a31-177">FLOOR(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-177">FLOOR(expression)</span></span>

<span data-ttu-id="06a31-178">Převede zadaný výraz na největší celé číslo, které je menší nebo rovné.</span><span class="sxs-lookup"><span data-stu-id="06a31-178">Converts the specified expression to the largest integer less than or equal to it.</span></span>

<span data-ttu-id="06a31-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-179">**Arguments**</span></span>

<span data-ttu-id="06a31-180">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-180">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-181">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-181">**Return Value**</span></span>

<span data-ttu-id="06a31-182">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-182">A `Double`.</span></span>

<span data-ttu-id="06a31-183">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-183">**Example**</span></span>

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="06a31-184">LOG(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-184">LOG(expression)</span></span>

<span data-ttu-id="06a31-185">Vypočítá přirozený logaritmus zadaného `float` výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-185">Calculates the natural logarithm of the specified `float` expression.</span></span>

<span data-ttu-id="06a31-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-186">**Arguments**</span></span>

<span data-ttu-id="06a31-187">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-187">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-188">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-188">**Return Value**</span></span>

<span data-ttu-id="06a31-189">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-189">A `Double`.</span></span>

<span data-ttu-id="06a31-190">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-190">**Example**</span></span>

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="06a31-191">LOG10(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-191">LOG10(expression)</span></span>

<span data-ttu-id="06a31-192">Vrátí logaritmus zadaný `Double` výraz-10.</span><span class="sxs-lookup"><span data-stu-id="06a31-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span>

<span data-ttu-id="06a31-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-193">**Arguments**</span></span>

<span data-ttu-id="06a31-194">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-194">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-195">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-195">**Return Value**</span></span>

<span data-ttu-id="06a31-196">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-196">A `Double`.</span></span>

<span data-ttu-id="06a31-197">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-197">**Example**</span></span>

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="06a31-198">PI()</span><span class="sxs-lookup"><span data-stu-id="06a31-198">PI()</span></span>

<span data-ttu-id="06a31-199">Vrátí konstantní hodnotu pí `Double`jako .</span><span class="sxs-lookup"><span data-stu-id="06a31-199">Returns the constant value of pi as a `Double`.</span></span>

<span data-ttu-id="06a31-200">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-200">**Return Value**</span></span>

<span data-ttu-id="06a31-201">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-201">A `Double`.</span></span>

<span data-ttu-id="06a31-202">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-202">**Example**</span></span>

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="06a31-203">POWER (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="06a31-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="06a31-204">Vypočítá hodnotu zadaného výrazu na zadaný výkon.</span><span class="sxs-lookup"><span data-stu-id="06a31-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="06a31-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-205">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="06a31-206">An `Int32` `Int64`, `Double`, `Decimal`, nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="06a31-207">A, `Double` který představuje moc, `numeric_expression`na kterou chcete zvýšit .</span><span class="sxs-lookup"><span data-stu-id="06a31-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>|

<span data-ttu-id="06a31-208">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-208">**Return Value**</span></span>

<span data-ttu-id="06a31-209">Hodnota zadaného `numeric_expression` na zadaný `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="06a31-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="06a31-210">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-210">**Example**</span></span>

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="06a31-211">RADIANS(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-211">RADIANS(expression)</span></span>

<span data-ttu-id="06a31-212">Převede stupně na radiány.</span><span class="sxs-lookup"><span data-stu-id="06a31-212">Converts degrees to radians.</span></span>

<span data-ttu-id="06a31-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-213">**Arguments**</span></span>

<span data-ttu-id="06a31-214">`expression`: `Int32`An `Int64` `Double`, `Decimal`, , nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="06a31-215">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-215">**Return Value**</span></span>

<span data-ttu-id="06a31-216">An `Int32` `Int64`, `Double`, `Decimal`, nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="06a31-217">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-217">**Example**</span></span>

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="06a31-218">RAND([semeno])</span><span class="sxs-lookup"><span data-stu-id="06a31-218">RAND([seed])</span></span>

<span data-ttu-id="06a31-219">Vrátí hodnotu náhodné od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="06a31-219">Returns a random value from 0 through 1.</span></span>

<span data-ttu-id="06a31-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-220">**Arguments**</span></span>

<span data-ttu-id="06a31-221">Hodnota osiva `Int32`jako .</span><span class="sxs-lookup"><span data-stu-id="06a31-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="06a31-222">Pokud není zadán osiva, SQL Server Database Engine přiřadí hodnotu osiva náhodně.</span><span class="sxs-lookup"><span data-stu-id="06a31-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="06a31-223">Pro zadanou hodnotu osiva je vrácený výsledek vždy stejný.</span><span class="sxs-lookup"><span data-stu-id="06a31-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="06a31-224">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-224">**Return Value**</span></span>

<span data-ttu-id="06a31-225">Náhodná `Double` hodnota od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="06a31-225">A random `Double` value from 0 through 1.</span></span>

<span data-ttu-id="06a31-226">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-226">**Example**</span></span>

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="06a31-227">ROUND(numeric_expression, délka[,funkce])</span><span class="sxs-lookup"><span data-stu-id="06a31-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="06a31-228">Vrátí číselný výraz zaokrouhlený na zadanou délku nebo přesnost.</span><span class="sxs-lookup"><span data-stu-id="06a31-228">Returns a numeric expression, rounded to the specified length or precision.</span></span>

<span data-ttu-id="06a31-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-229">**Arguments**</span></span>

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="06a31-230">An `Int32` `Int64`, `Double`, `Decimal`, nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>
|`length`| <span data-ttu-id="06a31-231">A `Int32` který představuje přesnost, na kterou `numeric_expression` má být zaokrouhlena.</span><span class="sxs-lookup"><span data-stu-id="06a31-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="06a31-232">Pokud `length` je kladné `numeric_expression` číslo, je zaokrouhleno `length`na počet desetinných míst určených .</span><span class="sxs-lookup"><span data-stu-id="06a31-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="06a31-233">Pokud `length` je záporné číslo, `numeric_expression` je zaokrouhleno na levé `length`straně desetinné čárky, jak je určeno .</span><span class="sxs-lookup"><span data-stu-id="06a31-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="06a31-234">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="06a31-234">Optional.</span></span> <span data-ttu-id="06a31-235">A, `Int32` který představuje typ operace, která má být vyvedena.</span><span class="sxs-lookup"><span data-stu-id="06a31-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="06a31-236">Pokud je funkce vynechána nebo má hodnotu 0 (výchozí), `numeric_expression` je zaokrouhlena.</span><span class="sxs-lookup"><span data-stu-id="06a31-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="06a31-237">Pokud je zadána jiná `numeric_expression` hodnota než 0, je zkrácen.</span><span class="sxs-lookup"><span data-stu-id="06a31-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="06a31-238">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-238">**Return Value**</span></span>

<span data-ttu-id="06a31-239">Hodnota zadaného `numeric_expression` na zadaný `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="06a31-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="06a31-240">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-240">**Example**</span></span>

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="06a31-241">SIGN(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-241">SIGN(expression)</span></span>

<span data-ttu-id="06a31-242">Vrátí kladný znak (+1), nula (0) nebo záporný znak (-1) zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span>

<span data-ttu-id="06a31-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-243">**Arguments**</span></span>

<span data-ttu-id="06a31-244">`expression`: `Int32` `Int64`, `Double`, , , nebo`Decimal`</span><span class="sxs-lookup"><span data-stu-id="06a31-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span>

<span data-ttu-id="06a31-245">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-245">**Return Value**</span></span>

<span data-ttu-id="06a31-246">An `Int32` `Int64`, `Double`, `Decimal`, nebo .</span><span class="sxs-lookup"><span data-stu-id="06a31-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="06a31-247">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-247">**Example**</span></span>

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="06a31-248">SIN(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-248">SIN(expression)</span></span>

<span data-ttu-id="06a31-249">Vypočítá goniometrické sinus zadaného úhlu v radiánech a vrátí `Double` výraz.</span><span class="sxs-lookup"><span data-stu-id="06a31-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span>

<span data-ttu-id="06a31-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-250">**Arguments**</span></span>

<span data-ttu-id="06a31-251">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-251">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-252">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-252">**Return Value**</span></span>

<span data-ttu-id="06a31-253">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-253">A `Double`.</span></span>

<span data-ttu-id="06a31-254">**Příklad**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="06a31-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="06a31-255">SQRT(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-255">SQRT(expression)</span></span>

<span data-ttu-id="06a31-256">Vrátí druhou odmocninu zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-256">Returns the square root of the specified expression.</span></span>

<span data-ttu-id="06a31-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-257">**Arguments**</span></span>

<span data-ttu-id="06a31-258">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-258">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-259">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-259">**Return Value**</span></span>

<span data-ttu-id="06a31-260">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-260">A `Double`.</span></span>

<span data-ttu-id="06a31-261">**Příklad**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="06a31-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="06a31-262">ČTVEREC(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-262">SQUARE(expression)</span></span>

<span data-ttu-id="06a31-263">Vrátí druhou mocninu zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-263">Returns the square of the specified expression.</span></span>

<span data-ttu-id="06a31-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-264">**Arguments**</span></span>

<span data-ttu-id="06a31-265">`expression`: `Double`A .</span><span class="sxs-lookup"><span data-stu-id="06a31-265">`expression`: A `Double`.</span></span>

<span data-ttu-id="06a31-266">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-266">**Return Value**</span></span>

<span data-ttu-id="06a31-267">Úloha `Double`.</span><span class="sxs-lookup"><span data-stu-id="06a31-267">A `Double`.</span></span>

<span data-ttu-id="06a31-268">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-268">**Example**</span></span>

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="06a31-269">TAN(výraz)</span><span class="sxs-lookup"><span data-stu-id="06a31-269">TAN(expression)</span></span>

<span data-ttu-id="06a31-270">Vypočítá tečnu zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="06a31-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="06a31-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="06a31-271">**Arguments**</span></span>

<span data-ttu-id="06a31-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="06a31-272">`expression`: `Double`</span></span>

<span data-ttu-id="06a31-273">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="06a31-273">**Return Value**</span></span>

`Double`

<span data-ttu-id="06a31-274">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="06a31-274">**Example**</span></span>

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="06a31-275">Viz také</span><span class="sxs-lookup"><span data-stu-id="06a31-275">See also</span></span>

- [<span data-ttu-id="06a31-276">Matematické funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="06a31-276">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="06a31-277">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="06a31-277">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
