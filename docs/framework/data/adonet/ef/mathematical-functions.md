---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 664d1a4f67ecced6713f83bf3dd11931c9b4dc18
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700004"
---
# <a name="mathematical-functions"></a><span data-ttu-id="cd000-102">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="cd000-102">Mathematical Functions</span></span>

<span data-ttu-id="cd000-103">.NET Framework Zprostředkovatel dat for SQL Server (SqlClient) poskytuje matematické funkce, které provádějí výpočty na vstupních hodnotách, které jsou k dispozici jako argumenty, a vrátí výsledek číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cd000-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="cd000-104">Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití nástroje SqlClient.</span><span class="sxs-lookup"><span data-stu-id="cd000-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="cd000-105">Vlastnost Namespace poskytovatele umožňuje Entity Framework zjistit, která předpona je používána tímto poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="cd000-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="cd000-106">V následující tabulce jsou popsány matematické funkce SqlClient.</span><span class="sxs-lookup"><span data-stu-id="cd000-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="cd000-107">ABS (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-107">ABS(expression)</span></span>

<span data-ttu-id="cd000-108">Provede funkci absolutní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="cd000-108">Performs the absolute value function.</span></span>

<span data-ttu-id="cd000-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-109">**Arguments**</span></span>

<span data-ttu-id="cd000-110">`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="cd000-111">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-111">**Return Value**</span></span>

<span data-ttu-id="cd000-112">Absolutní hodnota zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="cd000-113">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="cd000-114">ACOS (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-114">ACOS(expression)</span></span>

<span data-ttu-id="cd000-115">Vrátí hodnotu Arkus kosinus určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="cd000-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-116">**Arguments**</span></span>

<span data-ttu-id="cd000-117">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="cd000-118">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-118">**Return Value**</span></span>

<span data-ttu-id="cd000-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-119">A `Double`.</span></span>

<span data-ttu-id="cd000-120">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="cd000-121">ASIN (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-121">ASIN(expression)</span></span>

<span data-ttu-id="cd000-122">Vrátí hodnotu Arkus sinus určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="cd000-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-123">**Arguments**</span></span>

<span data-ttu-id="cd000-124">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="cd000-125">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-125">**Return Value**</span></span>

<span data-ttu-id="cd000-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-126">A `Double`.</span></span>

<span data-ttu-id="cd000-127">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="cd000-128">ATAN (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-128">ATAN(expression)</span></span>

<span data-ttu-id="cd000-129">Vrací hodnotu arkustangens zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="cd000-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-130">**Arguments**</span></span>

<span data-ttu-id="cd000-131">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="cd000-132">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-132">**Return Value**</span></span>

<span data-ttu-id="cd000-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-133">A `Double`.</span></span>

<span data-ttu-id="cd000-134">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="cd000-135">ATN2 (výraz, výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="cd000-136">Vrátí úhel v radiánech, jejichž tangens je mezi dvěma zadanými číselnými výrazy.</span><span class="sxs-lookup"><span data-stu-id="cd000-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="cd000-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-137">**Arguments**</span></span>

<span data-ttu-id="cd000-138">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="cd000-139">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-139">**Return Value**</span></span>

<span data-ttu-id="cd000-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-140">A `Double`.</span></span>

<span data-ttu-id="cd000-141">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="cd000-142">STROP (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-142">CEILING(expression)</span></span>

<span data-ttu-id="cd000-143">Převede zadaný výraz na nejmenší celé číslo, které je větší než nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="cd000-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="cd000-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-144">**Arguments**</span></span>

<span data-ttu-id="cd000-145">`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="cd000-146">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-146">**Return Value**</span></span>

<span data-ttu-id="cd000-147">`Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="cd000-148">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-148">**Example**</span></span> 

[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="cd000-149">COS (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-149">COS(expression)</span></span>

<span data-ttu-id="cd000-150">Vypočítá trigonometrický kosinus zadaného úhlu v radiánech.</span><span class="sxs-lookup"><span data-stu-id="cd000-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="cd000-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-151">**Arguments**</span></span> 

<span data-ttu-id="cd000-152">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-153">**Return Value**</span></span> 

<span data-ttu-id="cd000-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-154">A `Double`.</span></span> 

<span data-ttu-id="cd000-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="cd000-156">COT (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-156">COT(expression)</span></span>

<span data-ttu-id="cd000-157">Vypočítá trigonometrický kotangens zadaného úhlu v radiánech.</span><span class="sxs-lookup"><span data-stu-id="cd000-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="cd000-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-158">**Arguments**</span></span> 

<span data-ttu-id="cd000-159">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-160">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-160">**Return Value**</span></span> 

<span data-ttu-id="cd000-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-161">A `Double`.</span></span> 

<span data-ttu-id="cd000-162">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="cd000-163">STUPNĚ (radiány)</span><span class="sxs-lookup"><span data-stu-id="cd000-163">DEGREES(radians)</span></span>

<span data-ttu-id="cd000-164">Vrátí odpovídající úhel ve stupních.</span><span class="sxs-lookup"><span data-stu-id="cd000-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="cd000-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-165">**Arguments**</span></span> 

<span data-ttu-id="cd000-166">`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd000-167">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-167">**Return Value**</span></span> 

<span data-ttu-id="cd000-168">`Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd000-169">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="cd000-170">EXP (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-170">EXP(expression)</span></span>

<span data-ttu-id="cd000-171">Vypočítá exponenciální hodnotu zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="cd000-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-172">**Arguments**</span></span> 

<span data-ttu-id="cd000-173">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-174">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-174">**Return Value**</span></span> 

<span data-ttu-id="cd000-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-175">A `Double`.</span></span> 

<span data-ttu-id="cd000-176">**Příklad** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="cd000-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="cd000-177">FLOOR (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-177">FLOOR(expression)</span></span>

<span data-ttu-id="cd000-178">Převede zadaný výraz na největší celé číslo menší nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="cd000-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="cd000-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-179">**Arguments**</span></span> 

<span data-ttu-id="cd000-180">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-181">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-181">**Return Value**</span></span> 

<span data-ttu-id="cd000-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-182">A `Double`.</span></span> 

<span data-ttu-id="cd000-183">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-183">**Example**</span></span> 

[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="cd000-184">LOG (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-184">LOG(expression)</span></span>

<span data-ttu-id="cd000-185">Vypočítá přirozený logaritmus zadaného výrazu `float`.</span><span class="sxs-lookup"><span data-stu-id="cd000-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="cd000-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-186">**Arguments**</span></span> 

<span data-ttu-id="cd000-187">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-188">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-188">**Return Value**</span></span> 

<span data-ttu-id="cd000-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-189">A `Double`.</span></span> 

<span data-ttu-id="cd000-190">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="cd000-191">Log10 – (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-191">LOG10(expression)</span></span>

<span data-ttu-id="cd000-192">Vrátí logaritmus se základem 10 zadaného výrazu `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="cd000-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-193">**Arguments**</span></span> 

<span data-ttu-id="cd000-194">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-195">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-195">**Return Value**</span></span> 

<span data-ttu-id="cd000-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-196">A `Double`.</span></span> 

<span data-ttu-id="cd000-197">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="cd000-198">PI()</span><span class="sxs-lookup"><span data-stu-id="cd000-198">PI()</span></span>

<span data-ttu-id="cd000-199">Vrací konstantní hodnotu hodnoty PI jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="cd000-200">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-200">**Return Value**</span></span> 

<span data-ttu-id="cd000-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-201">A `Double`.</span></span> 

<span data-ttu-id="cd000-202">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="cd000-203">NAPÁJENÍ (numeric_expression power_expression)</span><span class="sxs-lookup"><span data-stu-id="cd000-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="cd000-204">Vypočítá hodnotu zadaného výrazu na zadanou mocninu.</span><span class="sxs-lookup"><span data-stu-id="cd000-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="cd000-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="cd000-206">`Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="cd000-207">`Double`, který představuje mocninu, pro kterou chcete `numeric_expression`vyvolat.</span><span class="sxs-lookup"><span data-stu-id="cd000-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="cd000-208">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-208">**Return Value**</span></span> 

<span data-ttu-id="cd000-209">Hodnota zadaného `numeric_expression` zadaná `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="cd000-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="cd000-210">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="cd000-211">RADIÁNy (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-211">RADIANS(expression)</span></span>

<span data-ttu-id="cd000-212">Převede stupně na radiány.</span><span class="sxs-lookup"><span data-stu-id="cd000-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="cd000-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-213">**Arguments**</span></span> 

<span data-ttu-id="cd000-214">`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd000-215">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-215">**Return Value**</span></span> 

<span data-ttu-id="cd000-216">`Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd000-217">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="cd000-218">RAND ([Seed])</span><span class="sxs-lookup"><span data-stu-id="cd000-218">RAND([seed])</span></span>

<span data-ttu-id="cd000-219">Vrátí náhodnou hodnotu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="cd000-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="cd000-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-220">**Arguments**</span></span> 

<span data-ttu-id="cd000-221">Hodnota počáteční hodnoty jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="cd000-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="cd000-222">Pokud není zadaná počáteční hodnota, přiřadí SQL Server databázovému stroji počáteční hodnotu náhodně.</span><span class="sxs-lookup"><span data-stu-id="cd000-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="cd000-223">U zadané počáteční hodnoty je vrácený výsledek vždycky stejný.</span><span class="sxs-lookup"><span data-stu-id="cd000-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="cd000-224">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-224">**Return Value**</span></span> 

<span data-ttu-id="cd000-225">Hodnota náhodného `Double` od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="cd000-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="cd000-226">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="cd000-227">ROUND (numeric_expression; Length [; function])</span><span class="sxs-lookup"><span data-stu-id="cd000-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="cd000-228">Vrátí číselný výraz zaokrouhlený na zadanou délku nebo přesnost.</span><span class="sxs-lookup"><span data-stu-id="cd000-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="cd000-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="cd000-230">`Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="cd000-231">`Int32` reprezentující přesnost, na kterou má být `numeric_expression` zaokrouhlen.</span><span class="sxs-lookup"><span data-stu-id="cd000-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="cd000-232">Když je `length` kladné číslo, `numeric_expression` se zaokrouhluje na počet desetinných míst určených `length`.</span><span class="sxs-lookup"><span data-stu-id="cd000-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="cd000-233">Když je `length` záporné číslo, `numeric_expression` se zaokrouhluje na levou stranu desetinné čárky, jak je určeno `length`.</span><span class="sxs-lookup"><span data-stu-id="cd000-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="cd000-234">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="cd000-234">Optional.</span></span> <span data-ttu-id="cd000-235">`Int32`, který představuje typ operace, která má být provedena.</span><span class="sxs-lookup"><span data-stu-id="cd000-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="cd000-236">Pokud je funkce vynechána nebo má hodnotu 0 (výchozí), `numeric_expression` je zaokrouhlena.</span><span class="sxs-lookup"><span data-stu-id="cd000-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="cd000-237">Pokud je zadána jiná hodnota než 0, `numeric_expression` je zkrácena.</span><span class="sxs-lookup"><span data-stu-id="cd000-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="cd000-238">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-238">**Return Value**</span></span> 

<span data-ttu-id="cd000-239">Hodnota zadaného `numeric_expression` zadaná `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="cd000-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="cd000-240">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="cd000-241">SIGN (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-241">SIGN(expression)</span></span> 

<span data-ttu-id="cd000-242">Vrátí kladné znaménko (+ 1), nula (0) nebo negativní (-1) znak zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="cd000-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-243">**Arguments**</span></span> 

<span data-ttu-id="cd000-244">`expression`: `Int32`, `Int64`, `Double`nebo `Decimal`</span><span class="sxs-lookup"><span data-stu-id="cd000-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="cd000-245">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-245">**Return Value**</span></span> 

<span data-ttu-id="cd000-246">`Int32`, `Int64`, `Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="cd000-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="cd000-247">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="cd000-248">SIN (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-248">SIN(expression)</span></span>

<span data-ttu-id="cd000-249">Vypočítá trigonometrický sinus zadaného úhlu v radiánech a vrátí výraz `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="cd000-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-250">**Arguments**</span></span> 

<span data-ttu-id="cd000-251">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-252">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-252">**Return Value**</span></span> 

<span data-ttu-id="cd000-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-253">A `Double`.</span></span> 

<span data-ttu-id="cd000-254">**Příklad** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="cd000-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="cd000-255">SQRT (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-255">SQRT(expression)</span></span>

<span data-ttu-id="cd000-256">Vrátí druhou odmocninu určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="cd000-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-257">**Arguments**</span></span> 

<span data-ttu-id="cd000-258">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-259">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-259">**Return Value**</span></span> 

<span data-ttu-id="cd000-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-260">A `Double`.</span></span> 

<span data-ttu-id="cd000-261">**Příklad** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="cd000-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="cd000-262">SQUARE (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-262">SQUARE(expression)</span></span>

<span data-ttu-id="cd000-263">Vrátí čtverci určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="cd000-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-264">**Arguments**</span></span> 

<span data-ttu-id="cd000-265">`expression`: `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="cd000-266">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-266">**Return Value**</span></span> 

<span data-ttu-id="cd000-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="cd000-267">A `Double`.</span></span> 

<span data-ttu-id="cd000-268">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="cd000-269">TAN (výraz)</span><span class="sxs-lookup"><span data-stu-id="cd000-269">TAN(expression)</span></span>

<span data-ttu-id="cd000-270">Vypočítá tangens zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="cd000-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="cd000-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="cd000-271">**Arguments**</span></span> 

<span data-ttu-id="cd000-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="cd000-272">`expression`: `Double`</span></span> 

<span data-ttu-id="cd000-273">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="cd000-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="cd000-274">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="cd000-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="cd000-275">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd000-275">See also</span></span>

- [<span data-ttu-id="cd000-276">Matematické funkce (Transact-SQL)</span><span class="sxs-lookup"><span data-stu-id="cd000-276">Mathematical Functions (Transact-SQL)</span></span>](/sql/t-sql/functions/mathematical-functions-transact-sql)
- [<span data-ttu-id="cd000-277">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="cd000-277">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
