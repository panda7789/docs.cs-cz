---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: b6f248382f069df59a55e85e9a764b0df700fb26
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759376"
---
# <a name="mathematical-functions"></a><span data-ttu-id="ff97f-102">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="ff97f-102">Mathematical Functions</span></span>

<span data-ttu-id="ff97f-103">Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje matematické funkce, které provádějí výpočty na vstupní hodnoty, které jsou k dispozici jako argumenty a vrací výsledek číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="ff97f-104">Tyto funkce jsou v oboru názvů systému SQL Server, která je k dispozici, když použijete SqlClient.</span><span class="sxs-lookup"><span data-stu-id="ff97f-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="ff97f-105">Vlastnost oboru názvů poskytovatele umožňuje zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ff97f-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.</span></span> <span data-ttu-id="ff97f-106">Následující tabulka popisuje SqlClient matematických funkcí.</span><span class="sxs-lookup"><span data-stu-id="ff97f-106">The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="ff97f-107">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-107">ABS(expression)</span></span>

<span data-ttu-id="ff97f-108">Provede funkci absolutní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-108">Performs the absolute value function.</span></span>

<span data-ttu-id="ff97f-109">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-109">**Arguments**</span></span>

<span data-ttu-id="ff97f-110">`expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-110">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ff97f-111">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-111">**Return Value**</span></span>

<span data-ttu-id="ff97f-112">Absolutní hodnota zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-112">The absolute value of the specified expression.</span></span>

<span data-ttu-id="ff97f-113">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-113">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="ff97f-114">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-114">ACOS(expression)</span></span>

<span data-ttu-id="ff97f-115">Vrátí hodnotu Arkus kosinus určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-115">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="ff97f-116">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-116">**Arguments**</span></span>

<span data-ttu-id="ff97f-117">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-117">`expression`: A `Double`.</span></span>

<span data-ttu-id="ff97f-118">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-118">**Return Value**</span></span>

<span data-ttu-id="ff97f-119">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-119">A `Double`.</span></span>

<span data-ttu-id="ff97f-120">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-120">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="ff97f-121">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-121">ASIN(expression)</span></span>

<span data-ttu-id="ff97f-122">Vrátí hodnotu Arkus sinus určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-122">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="ff97f-123">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-123">**Arguments**</span></span>

<span data-ttu-id="ff97f-124">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-124">`expression`: A `Double`.</span></span>

<span data-ttu-id="ff97f-125">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-125">**Return Value**</span></span>

<span data-ttu-id="ff97f-126">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-126">A `Double`.</span></span>

<span data-ttu-id="ff97f-127">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-127">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="ff97f-128">Atan(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-128">ATAN(expression)</span></span>

<span data-ttu-id="ff97f-129">Vrátí hodnotu Arkus tangens zadaného číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="ff97f-129">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="ff97f-130">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-130">**Arguments**</span></span>

<span data-ttu-id="ff97f-131">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-131">`expression`: A `Double`.</span></span>

<span data-ttu-id="ff97f-132">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-132">**Return Value**</span></span>

<span data-ttu-id="ff97f-133">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-133">A `Double`.</span></span>

<span data-ttu-id="ff97f-134">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-134">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="ff97f-135">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-135">ATN2(expression, expression)</span></span>

<span data-ttu-id="ff97f-136">Vrací úhel v radiánech, jehož tangens odpovídá mezi zadaným dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="ff97f-136">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="ff97f-137">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-137">**Arguments**</span></span>

<span data-ttu-id="ff97f-138">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-138">`expression`: A `Double`.</span></span>

<span data-ttu-id="ff97f-139">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-139">**Return Value**</span></span>

<span data-ttu-id="ff97f-140">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-140">A `Double`.</span></span>

<span data-ttu-id="ff97f-141">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-141">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="ff97f-142">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-142">CEILING(expression)</span></span>

<span data-ttu-id="ff97f-143">Převede zadaný výraz na nejmenší celé číslo, který je větší než nebo rovny.</span><span class="sxs-lookup"><span data-stu-id="ff97f-143">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="ff97f-144">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-144">**Arguments**</span></span>

<span data-ttu-id="ff97f-145">`expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-145">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ff97f-146">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-146">**Return Value**</span></span>

<span data-ttu-id="ff97f-147">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-147">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="ff97f-148">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-148">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="ff97f-149">Cos(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-149">COS(expression)</span></span>

<span data-ttu-id="ff97f-150">Vypočítá trigonometrických kosinus úhlu určeného v radiánech.</span><span class="sxs-lookup"><span data-stu-id="ff97f-150">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="ff97f-151">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-151">**Arguments**</span></span> 

<span data-ttu-id="ff97f-152">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-152">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-153">**Return Value**</span></span> 

<span data-ttu-id="ff97f-154">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-154">A `Double`.</span></span> 

<span data-ttu-id="ff97f-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-155">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="ff97f-156">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-156">COT(expression)</span></span>

<span data-ttu-id="ff97f-157">Vypočítá trigonometrických kotangens úhlu určeného v radiánech.</span><span class="sxs-lookup"><span data-stu-id="ff97f-157">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="ff97f-158">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-158">**Arguments**</span></span> 

<span data-ttu-id="ff97f-159">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-159">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-160">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-160">**Return Value**</span></span> 

<span data-ttu-id="ff97f-161">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-161">A `Double`.</span></span> 

<span data-ttu-id="ff97f-162">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-162">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="ff97f-163">DEGREES(RADIANS)</span><span class="sxs-lookup"><span data-stu-id="ff97f-163">DEGREES(radians)</span></span>

<span data-ttu-id="ff97f-164">Vrátí odpovídající úhel ve stupních.</span><span class="sxs-lookup"><span data-stu-id="ff97f-164">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="ff97f-165">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-165">**Arguments**</span></span> 

<span data-ttu-id="ff97f-166">`expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-166">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ff97f-167">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-167">**Return Value**</span></span> 

<span data-ttu-id="ff97f-168">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-168">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ff97f-169">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-169">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="ff97f-170">Exp(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-170">EXP(expression)</span></span>

<span data-ttu-id="ff97f-171">Vypočítá exponenciální hodnotu zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-171">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="ff97f-172">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-172">**Arguments**</span></span> 

<span data-ttu-id="ff97f-173">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-173">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-174">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-174">**Return Value**</span></span> 

<span data-ttu-id="ff97f-175">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-175">A `Double`.</span></span> 

<span data-ttu-id="ff97f-176">**Příklad** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="ff97f-176">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="ff97f-177">Floor(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-177">FLOOR(expression)</span></span>

<span data-ttu-id="ff97f-178">Převede zadaný výraz na největší celé číslo menší než nebo rovna k němu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-178">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="ff97f-179">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-179">**Arguments**</span></span> 

<span data-ttu-id="ff97f-180">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-180">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-181">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-181">**Return Value**</span></span> 

<span data-ttu-id="ff97f-182">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-182">A `Double`.</span></span> 

<span data-ttu-id="ff97f-183">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-183">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="ff97f-184">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-184">LOG(expression)</span></span>

<span data-ttu-id="ff97f-185">Vypočítá přirozený logaritmus zadaného `float` výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-185">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="ff97f-186">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-186">**Arguments**</span></span> 

<span data-ttu-id="ff97f-187">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-187">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-188">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-188">**Return Value**</span></span> 

<span data-ttu-id="ff97f-189">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-189">A `Double`.</span></span> 

<span data-ttu-id="ff97f-190">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-190">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="ff97f-191">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-191">LOG10(expression)</span></span>

<span data-ttu-id="ff97f-192">Vrátí logaritmus o základu 10 zadaného `Double` výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-192">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="ff97f-193">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-193">**Arguments**</span></span> 

<span data-ttu-id="ff97f-194">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-194">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-195">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-195">**Return Value**</span></span> 

<span data-ttu-id="ff97f-196">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-196">A `Double`.</span></span> 

<span data-ttu-id="ff97f-197">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-197">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="ff97f-198">PI()</span><span class="sxs-lookup"><span data-stu-id="ff97f-198">PI()</span></span>

<span data-ttu-id="ff97f-199">Vrátí konstantní hodnotu čísla pí jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-199">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="ff97f-200">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-200">**Return Value**</span></span> 

<span data-ttu-id="ff97f-201">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-201">A `Double`.</span></span> 

<span data-ttu-id="ff97f-202">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-202">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="ff97f-203">NAPÁJENÍ (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-203">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="ff97f-204">Vypočítá hodnotu zadaného výrazu na zadanou mocninu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-204">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="ff97f-205">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-205">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="ff97f-206">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-206">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="ff97f-207">A `Double` , která představuje schopnost, který se má použít `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-207">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="ff97f-208">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-208">**Return Value**</span></span> 

<span data-ttu-id="ff97f-209">Hodnota zadaného `numeric_expression` do zadaného `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-209">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="ff97f-210">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-210">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="ff97f-211">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-211">RADIANS(expression)</span></span>

<span data-ttu-id="ff97f-212">Převede stupně na radiány.</span><span class="sxs-lookup"><span data-stu-id="ff97f-212">Converts degrees to radians.</span></span> 

<span data-ttu-id="ff97f-213">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-213">**Arguments**</span></span> 

<span data-ttu-id="ff97f-214">`expression`: `Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-214">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ff97f-215">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-215">**Return Value**</span></span> 

<span data-ttu-id="ff97f-216">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-216">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ff97f-217">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-217">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="ff97f-218">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="ff97f-218">RAND([seed])</span></span>

<span data-ttu-id="ff97f-219">Vrací náhodnou hodnotu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="ff97f-219">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="ff97f-220">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-220">**Arguments**</span></span> 

<span data-ttu-id="ff97f-221">Počáteční hodnoty jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-221">The seed value as an `Int32`.</span></span> <span data-ttu-id="ff97f-222">Pokud počáteční hodnotu nezadáte, přiřadí databázový stroj SQL serveru náhodně počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="ff97f-222">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="ff97f-223">Pro zadaný počáteční hodnoty vrácený výsledek je vždy stejný.</span><span class="sxs-lookup"><span data-stu-id="ff97f-223">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="ff97f-224">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-224">**Return Value**</span></span> 

<span data-ttu-id="ff97f-225">Náhodnou `Double` hodnotu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="ff97f-225">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="ff97f-226">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-226">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="ff97f-227">Round(Numeric_Expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="ff97f-227">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="ff97f-228">Vrátí hodnotu číselného výrazu, zaokrouhlí se zadané délky nebo přesnosti.</span><span class="sxs-lookup"><span data-stu-id="ff97f-228">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="ff97f-229">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-229">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="ff97f-230">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-230">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="ff97f-231">`Int32` , Která představuje přesnost, ke kterému `numeric_expression` má být zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="ff97f-231">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="ff97f-232">Když `length` je kladné číslo, `numeric_expression` se zaokrouhlí na počet desetinných míst určené `length`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-232">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="ff97f-233">Když `length` je záporné číslo, `numeric_expression` poloměr zaoblení nalevo od desetinné čárky, jak jsou určené `length`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-233">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="ff97f-234">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="ff97f-234">Optional.</span></span> <span data-ttu-id="ff97f-235">`Int32` , Který představuje typ operace k provedení.</span><span class="sxs-lookup"><span data-stu-id="ff97f-235">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="ff97f-236">Pokud funkce je vynechán nebo má hodnotu 0 (výchozí), `numeric_expression` zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="ff97f-236">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="ff97f-237">Když je hodnota jiná než je zadána hodnota 0, `numeric_expression` je oříznutá.</span><span class="sxs-lookup"><span data-stu-id="ff97f-237">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="ff97f-238">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-238">**Return Value**</span></span> 

<span data-ttu-id="ff97f-239">Hodnota zadaného `numeric_expression` do zadaného `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-239">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="ff97f-240">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-240">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="ff97f-241">Sign(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-241">SIGN(expression)</span></span> 

<span data-ttu-id="ff97f-242">Vrátí kladné (+ 1), nula (0) nebo záporné znaménko (-1), z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-242">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="ff97f-243">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-243">**Arguments**</span></span> 

<span data-ttu-id="ff97f-244">`expression`: `Int32`, `Int64`, `Double`, nebo `Decimal`</span><span class="sxs-lookup"><span data-stu-id="ff97f-244">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="ff97f-245">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-245">**Return Value**</span></span> 

<span data-ttu-id="ff97f-246">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-246">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="ff97f-247">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-247">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="ff97f-248">Sin(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-248">SIN(expression)</span></span>

<span data-ttu-id="ff97f-249">Vypočítá trigonometrických sinus úhlu určeného v radiánech a vrátí `Double` výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-249">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="ff97f-250">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-250">**Arguments**</span></span> 

<span data-ttu-id="ff97f-251">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-251">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-252">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-252">**Return Value**</span></span> 

<span data-ttu-id="ff97f-253">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-253">A `Double`.</span></span> 

<span data-ttu-id="ff97f-254">**Příklad** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="ff97f-254">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="ff97f-255">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-255">SQRT(expression)</span></span>

<span data-ttu-id="ff97f-256">Vrátí druhou odmocninu z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-256">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="ff97f-257">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-257">**Arguments**</span></span> 

<span data-ttu-id="ff97f-258">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-258">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-259">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-259">**Return Value**</span></span> 

<span data-ttu-id="ff97f-260">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-260">A `Double`.</span></span> 

<span data-ttu-id="ff97f-261">**Příklad** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="ff97f-261">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="ff97f-262">Square(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-262">SQUARE(expression)</span></span>

<span data-ttu-id="ff97f-263">Vrátí druhou mocninu, z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-263">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="ff97f-264">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-264">**Arguments**</span></span> 

<span data-ttu-id="ff97f-265">`expression`: A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-265">`expression`: A `Double`.</span></span> 

<span data-ttu-id="ff97f-266">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-266">**Return Value**</span></span> 

<span data-ttu-id="ff97f-267">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="ff97f-267">A `Double`.</span></span> 

<span data-ttu-id="ff97f-268">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-268">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="ff97f-269">Tan(Expression)</span><span class="sxs-lookup"><span data-stu-id="ff97f-269">TAN(expression)</span></span>

<span data-ttu-id="ff97f-270">Vypočítá jeho tangens zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="ff97f-270">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="ff97f-271">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="ff97f-271">**Arguments**</span></span> 

<span data-ttu-id="ff97f-272">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="ff97f-272">`expression`: `Double`</span></span> 

<span data-ttu-id="ff97f-273">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="ff97f-273">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="ff97f-274">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="ff97f-274">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="ff97f-275">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ff97f-275">See also</span></span>

<span data-ttu-id="ff97f-276">Další informace o matematických funkcí, které SqlClient podporuje najdete v dokumentaci pro verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:</span><span class="sxs-lookup"><span data-stu-id="ff97f-276">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>

- <span data-ttu-id="ff97f-277">**SQL Server 2005:** [Matematické funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="ff97f-277">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>
- <span data-ttu-id="ff97f-278">**SQL Server 2008:** [Matematické funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="ff97f-278">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>
- <span data-ttu-id="ff97f-279">**SQL Server 2012 a novější:** [Matematické funkce (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="ff97f-279">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>

- [<span data-ttu-id="ff97f-280">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="ff97f-280">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
