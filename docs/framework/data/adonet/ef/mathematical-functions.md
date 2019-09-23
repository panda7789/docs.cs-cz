---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: 5e5658e28c7d806f7fd38f941bfa7254e7806e11
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182492"
---
# <a name="mathematical-functions"></a><span data-ttu-id="0899b-102">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="0899b-102">Mathematical Functions</span></span>

<span data-ttu-id="0899b-103">.NET Framework Zprostředkovatel dat for SQL Server (SqlClient) poskytuje matematické funkce, které provádějí výpočty na vstupních hodnotách, které jsou k dispozici jako argumenty, a vrátí výsledek číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0899b-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="0899b-104">Tyto funkce jsou v oboru názvů SqlServer, který je k dispozici při použití nástroje SqlClient.</span><span class="sxs-lookup"><span data-stu-id="0899b-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="0899b-105">Vlastnost Namespace poskytovatele umožňuje Entity Framework zjistit, která předpona je používána tímto poskytovatelem pro konkrétní konstrukce, jako jsou typy a funkce.</span><span class="sxs-lookup"><span data-stu-id="0899b-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="0899b-106">V následující tabulce jsou popsány matematické funkce SqlClient.</span><span class="sxs-lookup"><span data-stu-id="0899b-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="0899b-107">ABS (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-107">ABS(expression)</span></span>

<span data-ttu-id="0899b-108">Provede funkci absolutní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="0899b-108">Performs the absolute value function.</span></span>

<span data-ttu-id="0899b-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-109">**Arguments**</span></span>

<span data-ttu-id="0899b-110">`expression`: A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="0899b-111">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-111">**Return Value**</span></span>

<span data-ttu-id="0899b-112">Absolutní hodnota zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="0899b-113">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="0899b-114">ACOS (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-114">ACOS(expression)</span></span>

<span data-ttu-id="0899b-115">Vrátí hodnotu Arkus kosinus určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="0899b-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-116">**Arguments**</span></span>

<span data-ttu-id="0899b-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="0899b-118">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-118">**Return Value**</span></span>

<span data-ttu-id="0899b-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-119">A `Double`.</span></span>

<span data-ttu-id="0899b-120">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="0899b-121">ASIN (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-121">ASIN(expression)</span></span>

<span data-ttu-id="0899b-122">Vrátí hodnotu Arkus sinus určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="0899b-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-123">**Arguments**</span></span>

<span data-ttu-id="0899b-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="0899b-125">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-125">**Return Value**</span></span>

<span data-ttu-id="0899b-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-126">A `Double`.</span></span>

<span data-ttu-id="0899b-127">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="0899b-128">ATAN (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-128">ATAN(expression)</span></span>

<span data-ttu-id="0899b-129">Vrací hodnotu arkustangens zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="0899b-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-130">**Arguments**</span></span>

<span data-ttu-id="0899b-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="0899b-132">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-132">**Return Value**</span></span>

<span data-ttu-id="0899b-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-133">A `Double`.</span></span>

<span data-ttu-id="0899b-134">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="0899b-135">ATN2 (výraz, výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="0899b-136">Vrátí úhel v radiánech, jejichž tangens je mezi dvěma zadanými číselnými výrazy.</span><span class="sxs-lookup"><span data-stu-id="0899b-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="0899b-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-137">**Arguments**</span></span>

<span data-ttu-id="0899b-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="0899b-139">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-139">**Return Value**</span></span>

<span data-ttu-id="0899b-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-140">A `Double`.</span></span>

<span data-ttu-id="0899b-141">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="0899b-142">STROP (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-142">CEILING(expression)</span></span>

<span data-ttu-id="0899b-143">Převede zadaný výraz na nejmenší celé číslo, které je větší než nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="0899b-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="0899b-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-144">**Arguments**</span></span>

<span data-ttu-id="0899b-145">`expression`: A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="0899b-146">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-146">**Return Value**</span></span>

<span data-ttu-id="0899b-147">A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="0899b-148">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="0899b-149">COS (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-149">COS(expression)</span></span>

<span data-ttu-id="0899b-150">Vypočítá trigonometrický kosinus zadaného úhlu v radiánech.</span><span class="sxs-lookup"><span data-stu-id="0899b-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="0899b-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-151">**Arguments**</span></span> 

<span data-ttu-id="0899b-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-153">**Return Value**</span></span> 

<span data-ttu-id="0899b-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-154">A `Double`.</span></span> 

<span data-ttu-id="0899b-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="0899b-156">COT (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-156">COT(expression)</span></span>

<span data-ttu-id="0899b-157">Vypočítá trigonometrický kotangens zadaného úhlu v radiánech.</span><span class="sxs-lookup"><span data-stu-id="0899b-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="0899b-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-158">**Arguments**</span></span> 

<span data-ttu-id="0899b-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-160">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-160">**Return Value**</span></span> 

<span data-ttu-id="0899b-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-161">A `Double`.</span></span> 

<span data-ttu-id="0899b-162">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="0899b-163">STUPNĚ (radiány)</span><span class="sxs-lookup"><span data-stu-id="0899b-163">DEGREES(radians)</span></span>

<span data-ttu-id="0899b-164">Vrátí odpovídající úhel ve stupních.</span><span class="sxs-lookup"><span data-stu-id="0899b-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="0899b-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-165">**Arguments**</span></span> 

<span data-ttu-id="0899b-166">`expression`: A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="0899b-167">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-167">**Return Value**</span></span> 

<span data-ttu-id="0899b-168">A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="0899b-169">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="0899b-170">EXP (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-170">EXP(expression)</span></span>

<span data-ttu-id="0899b-171">Vypočítá exponenciální hodnotu zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="0899b-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-172">**Arguments**</span></span> 

<span data-ttu-id="0899b-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-174">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-174">**Return Value**</span></span> 

<span data-ttu-id="0899b-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-175">A `Double`.</span></span> 

<span data-ttu-id="0899b-176">**Příklad**`SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="0899b-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="0899b-177">FLOOR (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-177">FLOOR(expression)</span></span>

<span data-ttu-id="0899b-178">Převede zadaný výraz na největší celé číslo menší nebo rovno.</span><span class="sxs-lookup"><span data-stu-id="0899b-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="0899b-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-179">**Arguments**</span></span> 

<span data-ttu-id="0899b-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-181">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-181">**Return Value**</span></span> 

<span data-ttu-id="0899b-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-182">A `Double`.</span></span> 

<span data-ttu-id="0899b-183">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="0899b-184">LOG (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-184">LOG(expression)</span></span>

<span data-ttu-id="0899b-185">Vypočítá přirozený logaritmus určeného `float` výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="0899b-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-186">**Arguments**</span></span> 

<span data-ttu-id="0899b-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-188">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-188">**Return Value**</span></span> 

<span data-ttu-id="0899b-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-189">A `Double`.</span></span> 

<span data-ttu-id="0899b-190">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="0899b-191">Log10 – (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-191">LOG10(expression)</span></span>

<span data-ttu-id="0899b-192">Vrátí logaritmus o základu 10 určeného `Double` výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="0899b-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-193">**Arguments**</span></span> 

<span data-ttu-id="0899b-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-195">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-195">**Return Value**</span></span> 

<span data-ttu-id="0899b-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-196">A `Double`.</span></span> 

<span data-ttu-id="0899b-197">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="0899b-198">PI()</span><span class="sxs-lookup"><span data-stu-id="0899b-198">PI()</span></span>

<span data-ttu-id="0899b-199">Vrátí konstantní hodnotu pí jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="0899b-200">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-200">**Return Value**</span></span> 

<span data-ttu-id="0899b-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-201">A `Double`.</span></span> 

<span data-ttu-id="0899b-202">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumeric_expression-power_expression"></a><span data-ttu-id="0899b-203">NAPÁJENÍ (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="0899b-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="0899b-204">Vypočítá hodnotu zadaného výrazu na zadanou mocninu.</span><span class="sxs-lookup"><span data-stu-id="0899b-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="0899b-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="0899b-206">A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="0899b-207">Který představuje mocninu, pro kterou chcete `numeric_expression`vyvolat. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="0899b-208">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-208">**Return Value**</span></span> 

<span data-ttu-id="0899b-209">Hodnota zadaná `numeric_expression` pro zadanou `power_expression`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0899b-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="0899b-210">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="0899b-211">RADIÁNy (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-211">RADIANS(expression)</span></span>

<span data-ttu-id="0899b-212">Převede stupně na radiány.</span><span class="sxs-lookup"><span data-stu-id="0899b-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="0899b-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-213">**Arguments**</span></span> 

<span data-ttu-id="0899b-214">`expression`: A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="0899b-215">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-215">**Return Value**</span></span> 

<span data-ttu-id="0899b-216">A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="0899b-217">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="0899b-218">RAND ([Seed])</span><span class="sxs-lookup"><span data-stu-id="0899b-218">RAND([seed])</span></span>

<span data-ttu-id="0899b-219">Vrátí náhodnou hodnotu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="0899b-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="0899b-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-220">**Arguments**</span></span> 

<span data-ttu-id="0899b-221">Hodnota počáteční hodnoty jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="0899b-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="0899b-222">Pokud není zadaná počáteční hodnota, přiřadí SQL Server databázovému stroji počáteční hodnotu náhodně.</span><span class="sxs-lookup"><span data-stu-id="0899b-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="0899b-223">U zadané počáteční hodnoty je vrácený výsledek vždycky stejný.</span><span class="sxs-lookup"><span data-stu-id="0899b-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="0899b-224">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-224">**Return Value**</span></span> 

<span data-ttu-id="0899b-225">Náhodná `Double` hodnota od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="0899b-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="0899b-226">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumeric_expression-lengthfunction"></a><span data-ttu-id="0899b-227">ROUND (numeric_expression; Length [; function])</span><span class="sxs-lookup"><span data-stu-id="0899b-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="0899b-228">Vrátí číselný výraz zaokrouhlený na zadanou délku nebo přesnost.</span><span class="sxs-lookup"><span data-stu-id="0899b-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="0899b-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="0899b-230">A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="0899b-231">Hodnota, která představuje přesnost, na `numeric_expression` kterou má být zaokrouhlena. `Int32`</span><span class="sxs-lookup"><span data-stu-id="0899b-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="0899b-232">Pokud `length` je kladné číslo, `numeric_expression` je zaokrouhleno na počet desetinných míst určených parametrem `length`.</span><span class="sxs-lookup"><span data-stu-id="0899b-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="0899b-233">V `length` případě, že je záporné `numeric_expression` číslo, je zaokrouhleno na levé straně desetinné čárky, jak je `length`uvedeno v.</span><span class="sxs-lookup"><span data-stu-id="0899b-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="0899b-234">Volitelný parametr.</span><span class="sxs-lookup"><span data-stu-id="0899b-234">Optional.</span></span> <span data-ttu-id="0899b-235">`Int32` Který představuje typ operace, která má být provedena.</span><span class="sxs-lookup"><span data-stu-id="0899b-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="0899b-236">Pokud je funkce vynechána nebo má hodnotu 0 (výchozí), `numeric_expression` je zaokrouhlena.</span><span class="sxs-lookup"><span data-stu-id="0899b-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="0899b-237">Pokud je zadána jiná hodnota než 0, `numeric_expression` je zkrácena.</span><span class="sxs-lookup"><span data-stu-id="0899b-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="0899b-238">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-238">**Return Value**</span></span> 

<span data-ttu-id="0899b-239">Hodnota zadaná `numeric_expression` pro zadanou `power_expression`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="0899b-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="0899b-240">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="0899b-241">SIGN (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-241">SIGN(expression)</span></span> 

<span data-ttu-id="0899b-242">Vrátí kladné znaménko (+ 1), nula (0) nebo negativní (-1) znak zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="0899b-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-243">**Arguments**</span></span> 

<span data-ttu-id="0899b-244">`expression`: `Int32`, `Int64`, nebo`Double``Decimal`</span><span class="sxs-lookup"><span data-stu-id="0899b-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="0899b-245">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-245">**Return Value**</span></span> 

<span data-ttu-id="0899b-246">A `Int32` ,`Int64`, nebo`Decimal`. `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="0899b-247">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="0899b-248">SIN (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-248">SIN(expression)</span></span>

<span data-ttu-id="0899b-249">Vypočítá trigonometrický sinus zadaného úhlu v radiánech a vrátí `Double` výraz.</span><span class="sxs-lookup"><span data-stu-id="0899b-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="0899b-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-250">**Arguments**</span></span> 

<span data-ttu-id="0899b-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-252">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-252">**Return Value**</span></span> 

<span data-ttu-id="0899b-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-253">A `Double`.</span></span> 

<span data-ttu-id="0899b-254">**Příklad**`SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="0899b-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="0899b-255">SQRT (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-255">SQRT(expression)</span></span>

<span data-ttu-id="0899b-256">Vrátí druhou odmocninu určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="0899b-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-257">**Arguments**</span></span> 

<span data-ttu-id="0899b-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-259">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-259">**Return Value**</span></span> 

<span data-ttu-id="0899b-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-260">A `Double`.</span></span> 

<span data-ttu-id="0899b-261">**Příklad**`SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="0899b-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="0899b-262">SQUARE (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-262">SQUARE(expression)</span></span>

<span data-ttu-id="0899b-263">Vrátí čtverci určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="0899b-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-264">**Arguments**</span></span> 

<span data-ttu-id="0899b-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="0899b-266">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-266">**Return Value**</span></span> 

<span data-ttu-id="0899b-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="0899b-267">A `Double`.</span></span> 

<span data-ttu-id="0899b-268">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="0899b-269">TAN (výraz)</span><span class="sxs-lookup"><span data-stu-id="0899b-269">TAN(expression)</span></span>

<span data-ttu-id="0899b-270">Vypočítá tangens zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="0899b-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="0899b-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="0899b-271">**Arguments**</span></span> 

<span data-ttu-id="0899b-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="0899b-272">`expression`: `Double`</span></span> 

<span data-ttu-id="0899b-273">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="0899b-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="0899b-274">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="0899b-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="0899b-275">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0899b-275">See also</span></span>

<span data-ttu-id="0899b-276">Další informace o matematických funkcích, které SqlClient podporuje, najdete v dokumentaci k verzi SQL Server, kterou jste zadali v manifestu zprostředkovatele SqlClient:</span><span class="sxs-lookup"><span data-stu-id="0899b-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="0899b-277">**SQL Server 2005:** [Matematické funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="0899b-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="0899b-278">**SQL Server 2008:** [Matematické funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="0899b-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="0899b-279">**SQL Server 2012 a novější:** [Matematické funkce (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span><span class="sxs-lookup"><span data-stu-id="0899b-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql)</span></span>

- [<span data-ttu-id="0899b-280">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="0899b-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
