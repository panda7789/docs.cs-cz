---
title: Matematické funkce
ms.date: 03/30/2017
ms.assetid: b040c7cb-156d-40f2-9152-61065b18148c
ms.openlocfilehash: e6c58d781d7138f8295f2d0a2f0db110ad4b1dd6
ms.sourcegitcommit: 3ab9254890a52a50762995fa6d7d77a00348db7e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/20/2018
ms.locfileid: "46490358"
---
# <a name="mathematical-functions"></a><span data-ttu-id="4ec28-102">Matematické funkce</span><span class="sxs-lookup"><span data-stu-id="4ec28-102">Mathematical Functions</span></span>

<span data-ttu-id="4ec28-103">Zprostředkovatel dat .NET Framework pro SQL Server (SqlClient) poskytuje matematické funkce, které provádějí výpočty na vstupní hodnoty, které jsou k dispozici jako argumenty a vrací výsledek číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-103">The .NET Framework Data Provider for SQL Server (SqlClient) provides math functions that perform calculations on input values that are provided as arguments, and return a numeric value result.</span></span> <span data-ttu-id="4ec28-104">Tyto funkce jsou v oboru názvů systému SQL Server, která je k dispozici, když použijete SqlClient.</span><span class="sxs-lookup"><span data-stu-id="4ec28-104">These functions are in the SqlServer namespace, which is available when you use SqlClient.</span></span> <span data-ttu-id="4ec28-105">Vlastnost oboru názvů poskytovatele umožňuje zjistit, která předpona je používána tohoto poskytovatele pro konkrétní konstrukce, jako jsou typy a funkce Entity Framework. Následující tabulka popisuje SqlClient matematických funkcí.</span><span class="sxs-lookup"><span data-stu-id="4ec28-105">A provider's namespace property allows the Entity Framework to discover which prefix is used by this provider for specific constructs, such as types and functions.The following table describes the SqlClient math functions.</span></span>  
  
## <a name="absexpression"></a><span data-ttu-id="4ec28-106">Abs(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-106">ABS(expression)</span></span>

<span data-ttu-id="4ec28-107">Provede funkci absolutní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-107">Performs the absolute value function.</span></span>

<span data-ttu-id="4ec28-108">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-108">**Arguments**</span></span>

<span data-ttu-id="4ec28-109">`expression`: Celé `Int32`, `Int64`, `Double`, nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-109">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="4ec28-110">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-110">**Return Value**</span></span>

<span data-ttu-id="4ec28-111">Absolutní hodnota zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-111">The absolute value of the specified expression.</span></span>

<span data-ttu-id="4ec28-112">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-112">**Example**</span></span>

`SqlServer.ABS(-2)`

## <a name="acosexpression"></a><span data-ttu-id="4ec28-113">ACOS(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-113">ACOS(expression)</span></span>

<span data-ttu-id="4ec28-114">Vrátí hodnotu Arkus kosinus určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-114">Returns the arccosine value of the specified expression.</span></span>

<span data-ttu-id="4ec28-115">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-115">**Arguments**</span></span>

<span data-ttu-id="4ec28-116">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-116">`expression`: A `Double`.</span></span>

<span data-ttu-id="4ec28-117">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-117">**Return Value**</span></span>

<span data-ttu-id="4ec28-118">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-118">A `Double`.</span></span>

<span data-ttu-id="4ec28-119">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-119">**Example**</span></span>

`SqlServer.ACOS(.9)`

## <a name="asinexpression"></a><span data-ttu-id="4ec28-120">ASIN(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-120">ASIN(expression)</span></span>

<span data-ttu-id="4ec28-121">Vrátí hodnotu Arkus sinus určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-121">Returns the arcsine value of the specified expression.</span></span>

<span data-ttu-id="4ec28-122">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-122">**Arguments**</span></span>

<span data-ttu-id="4ec28-123">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-123">`expression`: A `Double`.</span></span>

<span data-ttu-id="4ec28-124">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-124">**Return Value**</span></span>

<span data-ttu-id="4ec28-125">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-125">A `Double`.</span></span>

<span data-ttu-id="4ec28-126">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-126">**Example**</span></span>

`SqlServer.ASIN(.9)`

## <a name="atanexpression"></a><span data-ttu-id="4ec28-127">Atan(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-127">ATAN(expression)</span></span>

<span data-ttu-id="4ec28-128">Vrátí hodnotu Arkus tangens zadaného číselný výraz.</span><span class="sxs-lookup"><span data-stu-id="4ec28-128">Returns the arctangent value of the specified numeric expression.</span></span>

<span data-ttu-id="4ec28-129">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-129">**Arguments**</span></span>

<span data-ttu-id="4ec28-130">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-130">`expression`: A `Double`.</span></span>

<span data-ttu-id="4ec28-131">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-131">**Return Value**</span></span>

<span data-ttu-id="4ec28-132">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-132">A `Double`.</span></span>

<span data-ttu-id="4ec28-133">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-133">**Example**</span></span>

`SqlServer.ATAN(9)`

## <a name="atn2expression-expression"></a><span data-ttu-id="4ec28-134">ATN2(Expression, Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-134">ATN2(expression, expression)</span></span>

<span data-ttu-id="4ec28-135">Vrací úhel v radiánech, jehož tangens odpovídá mezi zadaným dvou numerických výrazů.</span><span class="sxs-lookup"><span data-stu-id="4ec28-135">Returns the angle, in radians, whose tangent is between the two specified numeric expressions.</span></span>

<span data-ttu-id="4ec28-136">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-136">**Arguments**</span></span>

<span data-ttu-id="4ec28-137">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-137">`expression`: A `Double`.</span></span>

<span data-ttu-id="4ec28-138">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-138">**Return Value**</span></span>

<span data-ttu-id="4ec28-139">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-139">A `Double`.</span></span>

<span data-ttu-id="4ec28-140">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-140">**Example**</span></span>

`SqlServer.ATN2(9, 8)`
 
## <a name="ceilingexpression"></a><span data-ttu-id="4ec28-141">CEILING(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-141">CEILING(expression)</span></span>

<span data-ttu-id="4ec28-142">Převede zadaný výraz na nejmenší celé číslo, který je větší než nebo rovny.</span><span class="sxs-lookup"><span data-stu-id="4ec28-142">Converts the specified expression to the smallest integer that is greater than or equal to it.</span></span>

<span data-ttu-id="4ec28-143">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-143">**Arguments**</span></span>

<span data-ttu-id="4ec28-144">`expression`: Celé `Int32`, `Int64`, `Double`, nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-144">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="4ec28-145">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-145">**Return Value**</span></span>

<span data-ttu-id="4ec28-146">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-146">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>

<span data-ttu-id="4ec28-147">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-147">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_ceiling)]
[!code-sql[DP EntityServices Concepts#SQLSERVER_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_ceiling)]

## <a name="cosexpression"></a><span data-ttu-id="4ec28-148">Cos(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-148">COS(expression)</span></span>

<span data-ttu-id="4ec28-149">Vypočítá trigonometrických kosinus úhlu určeného v radiánech.</span><span class="sxs-lookup"><span data-stu-id="4ec28-149">Calculates the trigonometric cosine of the specified angle in radians.</span></span> 

<span data-ttu-id="4ec28-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-150">**Arguments**</span></span> 

<span data-ttu-id="4ec28-151">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-151">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-152">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-152">**Return Value**</span></span> 

<span data-ttu-id="4ec28-153">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-153">A `Double`.</span></span> 

<span data-ttu-id="4ec28-154">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-154">**Example**</span></span> 

`SqlServer.COS(45)`

## <a name="cotexpression"></a><span data-ttu-id="4ec28-155">COT(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-155">COT(expression)</span></span>

<span data-ttu-id="4ec28-156">Vypočítá trigonometrických kotangens úhlu určeného v radiánech.</span><span class="sxs-lookup"><span data-stu-id="4ec28-156">Calculates the trigonometric cotangent of the specified angle in radians.</span></span> 

<span data-ttu-id="4ec28-157">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-157">**Arguments**</span></span> 

<span data-ttu-id="4ec28-158">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-158">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-159">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-159">**Return Value**</span></span> 

<span data-ttu-id="4ec28-160">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-160">A `Double`.</span></span> 

<span data-ttu-id="4ec28-161">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-161">**Example**</span></span> 

`SqlServer.COT(60)`
  
## <a name="degreesradians"></a><span data-ttu-id="4ec28-162">DEGREES(RADIANS)</span><span class="sxs-lookup"><span data-stu-id="4ec28-162">DEGREES(radians)</span></span>

<span data-ttu-id="4ec28-163">Vrátí odpovídající úhel ve stupních.</span><span class="sxs-lookup"><span data-stu-id="4ec28-163">Returns the corresponding angle in degrees.</span></span> 

<span data-ttu-id="4ec28-164">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-164">**Arguments**</span></span> 

<span data-ttu-id="4ec28-165">`expression`: Celé `Int32`, `Int64`, `Double`, nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-165">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="4ec28-166">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-166">**Return Value**</span></span> 

<span data-ttu-id="4ec28-167">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-167">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="4ec28-168">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-168">**Example**</span></span> 

`SqlServer.DEGREES(3.1)`

## <a name="expexpression"></a><span data-ttu-id="4ec28-169">Exp(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-169">EXP(expression)</span></span>

<span data-ttu-id="4ec28-170">Vypočítá exponenciální hodnotu zadaného číselného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-170">Calculates the exponential value of a specified numeric expression.</span></span> 

<span data-ttu-id="4ec28-171">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-171">**Arguments**</span></span> 

<span data-ttu-id="4ec28-172">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-172">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-173">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-173">**Return Value**</span></span> 

<span data-ttu-id="4ec28-174">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-174">A `Double`.</span></span> 

<span data-ttu-id="4ec28-175">**Příklad** `SqlServer.EXP(1)`</span><span class="sxs-lookup"><span data-stu-id="4ec28-175">**Example** `SqlServer.EXP(1)`</span></span>

## <a name="floorexpression"></a><span data-ttu-id="4ec28-176">Floor(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-176">FLOOR(expression)</span></span>

<span data-ttu-id="4ec28-177">Převede zadaný výraz na největší celé číslo menší než nebo rovna k němu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-177">Converts the specified expression to the largest integer less than or equal to it.</span></span> 

<span data-ttu-id="4ec28-178">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-178">**Arguments**</span></span> 

<span data-ttu-id="4ec28-179">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-179">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-180">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-180">**Return Value**</span></span> 

<span data-ttu-id="4ec28-181">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-181">A `Double`.</span></span> 

<span data-ttu-id="4ec28-182">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-182">**Example**</span></span> 

[!code-csharp[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#sqlserver_floor)] 
[!code-sql[DP EntityServices Concepts#SQLSERVER_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#sqlserver_floor)]

## <a name="logexpression"></a><span data-ttu-id="4ec28-183">LOG(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-183">LOG(expression)</span></span>

<span data-ttu-id="4ec28-184">Vypočítá přirozený logaritmus zadaného `float` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-184">Calculates the natural logarithm of the specified `float` expression.</span></span> 

<span data-ttu-id="4ec28-185">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-185">**Arguments**</span></span> 

<span data-ttu-id="4ec28-186">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-186">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-187">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-187">**Return Value**</span></span> 

<span data-ttu-id="4ec28-188">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-188">A `Double`.</span></span> 

<span data-ttu-id="4ec28-189">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-189">**Example**</span></span> 

`SqlServer.LOG(100)`

## <a name="log10expression"></a><span data-ttu-id="4ec28-190">LOG10(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-190">LOG10(expression)</span></span>

<span data-ttu-id="4ec28-191">Vrátí logaritmus o základu 10 zadaného `Double` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-191">Returns the base-10 logarithm of the specified `Double` expression.</span></span> 

<span data-ttu-id="4ec28-192">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-192">**Arguments**</span></span> 

<span data-ttu-id="4ec28-193">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-193">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-194">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-194">**Return Value**</span></span> 

<span data-ttu-id="4ec28-195">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-195">A `Double`.</span></span> 

<span data-ttu-id="4ec28-196">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-196">**Example**</span></span> 

`SqlServer.LOG10(100)`

## <a name="pi"></a><span data-ttu-id="4ec28-197">PI()</span><span class="sxs-lookup"><span data-stu-id="4ec28-197">PI()</span></span>

<span data-ttu-id="4ec28-198">Vrátí konstantní hodnotu čísla pí jako `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-198">Returns the constant value of pi as a `Double`.</span></span> 

<span data-ttu-id="4ec28-199">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-199">**Return Value**</span></span> 

<span data-ttu-id="4ec28-200">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-200">A `Double`.</span></span> 

<span data-ttu-id="4ec28-201">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-201">**Example**</span></span> 

`SqlServer.PI()`

## <a name="powernumericexpression-powerexpression"></a><span data-ttu-id="4ec28-202">NAPÁJENÍ (numeric_expression, power_expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-202">POWER(numeric_expression, power_expression)</span></span>

<span data-ttu-id="4ec28-203">Vypočítá hodnotu zadaného výrazu na zadanou mocninu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-203">Calculates the value of a specified expression to a specified power.</span></span>

<span data-ttu-id="4ec28-204">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-204">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="4ec28-205">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-205">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span>|
|`power_expression`| <span data-ttu-id="4ec28-206">A `Double` , která představuje schopnost, který se má použít `numeric_expression`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-206">A `Double` that represents the power to which to raise the `numeric_expression`.</span></span>| 

<span data-ttu-id="4ec28-207">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-207">**Return Value**</span></span> 

<span data-ttu-id="4ec28-208">Hodnota zadaného `numeric_expression` do zadaného `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-208">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span> 

<span data-ttu-id="4ec28-209">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-209">**Example**</span></span> 

`SqlServer.POWER(2,7)`

## <a name="radiansexpression"></a><span data-ttu-id="4ec28-210">RADIANS(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-210">RADIANS(expression)</span></span>

<span data-ttu-id="4ec28-211">Převede stupně na radiány.</span><span class="sxs-lookup"><span data-stu-id="4ec28-211">Converts degrees to radians.</span></span> 

<span data-ttu-id="4ec28-212">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-212">**Arguments**</span></span> 

<span data-ttu-id="4ec28-213">`expression`: Celé `Int32`, `Int64`, `Double`, nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-213">`expression`: An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="4ec28-214">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-214">**Return Value**</span></span> 

<span data-ttu-id="4ec28-215">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-215">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="4ec28-216">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-216">**Example**</span></span> 

`SqlServer.RADIANS(360.0)`

## <a name="randseed"></a><span data-ttu-id="4ec28-217">RAND([seed])</span><span class="sxs-lookup"><span data-stu-id="4ec28-217">RAND([seed])</span></span>

<span data-ttu-id="4ec28-218">Vrací náhodnou hodnotu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="4ec28-218">Returns a random value from 0 through 1.</span></span> 

<span data-ttu-id="4ec28-219">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-219">**Arguments**</span></span> 

<span data-ttu-id="4ec28-220">Počáteční hodnoty jako `Int32`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-220">The seed value as an `Int32`.</span></span> <span data-ttu-id="4ec28-221">Pokud počáteční hodnotu nezadáte, přiřadí databázový stroj SQL serveru náhodně počáteční hodnoty.</span><span class="sxs-lookup"><span data-stu-id="4ec28-221">If the seed is not specified, the SQL Server Database Engine assigns a seed value at random.</span></span> <span data-ttu-id="4ec28-222">Pro zadaný počáteční hodnoty vrácený výsledek je vždy stejný.</span><span class="sxs-lookup"><span data-stu-id="4ec28-222">For a specified seed value, the result returned is always the same.</span></span>

<span data-ttu-id="4ec28-223">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-223">**Return Value**</span></span> 

<span data-ttu-id="4ec28-224">Náhodnou `Double` hodnotu od 0 do 1.</span><span class="sxs-lookup"><span data-stu-id="4ec28-224">A random `Double` value from 0 through 1.</span></span> 

<span data-ttu-id="4ec28-225">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-225">**Example**</span></span> 

`SqlServer.RAND()`
  
## <a name="roundnumericexpression-lengthfunction"></a><span data-ttu-id="4ec28-226">Round(Numeric_Expression, length[,Function])</span><span class="sxs-lookup"><span data-stu-id="4ec28-226">ROUND(numeric_expression, length[,function])</span></span>

<span data-ttu-id="4ec28-227">Vrátí hodnotu číselného výrazu, zaokrouhlí se zadané délky nebo přesnosti.</span><span class="sxs-lookup"><span data-stu-id="4ec28-227">Returns a numeric expression, rounded to the specified length or precision.</span></span> 

<span data-ttu-id="4ec28-228">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-228">**Arguments**</span></span> 

|  |  |
|--|--|
|`numeric_expression`| <span data-ttu-id="4ec28-229">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-229">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 
|`length`| <span data-ttu-id="4ec28-230">`Int32` , Která představuje přesnost, ke kterému `numeric_expression` má být zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="4ec28-230">An `Int32` that represents the precision to which `numeric_expression` is to be rounded.</span></span> <span data-ttu-id="4ec28-231">Když `length` je kladné číslo, `numeric_expression` se zaokrouhlí na počet desetinných míst určené `length`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-231">When `length` is a positive number, `numeric_expression` is rounded to the number of decimal positions specified by `length`.</span></span> <span data-ttu-id="4ec28-232">Když `length` je záporné číslo, `numeric_expression` poloměr zaoblení nalevo od desetinné čárky, jak jsou určené `length`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-232">When `length` is a negative number, `numeric_expression` is rounded on the left side of the decimal point, as specified by `length`.</span></span>|
|`function` | <span data-ttu-id="4ec28-233">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="4ec28-233">Optional.</span></span> <span data-ttu-id="4ec28-234">`Int32` , Který představuje typ operace k provedení.</span><span class="sxs-lookup"><span data-stu-id="4ec28-234">An `Int32` that represents the type of operation to perform.</span></span> <span data-ttu-id="4ec28-235">Pokud funkce je vynechán nebo má hodnotu 0 (výchozí), `numeric_expression` zaokrouhleno.</span><span class="sxs-lookup"><span data-stu-id="4ec28-235">When function is omitted or has a value of 0 (default), `numeric_expression` is rounded.</span></span> <span data-ttu-id="4ec28-236">Když je hodnota jiná než je zadána hodnota 0, `numeric_expression` je oříznutá.</span><span class="sxs-lookup"><span data-stu-id="4ec28-236">When a value other than 0 is specified, `numeric_expression` is truncated.</span></span> |

<span data-ttu-id="4ec28-237">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-237">**Return Value**</span></span> 

<span data-ttu-id="4ec28-238">Hodnota zadaného `numeric_expression` do zadaného `power_expression`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-238">The value of the specified `numeric_expression` to the specified `power_expression`.</span></span>

<span data-ttu-id="4ec28-239">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-239">**Example**</span></span> 

`SqlServer.ROUND(748.58, -3)`

## <a name="signexpression"></a><span data-ttu-id="4ec28-240">Sign(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-240">SIGN(expression)</span></span> 

<span data-ttu-id="4ec28-241">Vrátí kladné (+ 1), nula (0) nebo záporné znaménko (-1), z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-241">Returns the positive (+1), zero (0), or negative (-1) sign of the specified expression.</span></span> 

<span data-ttu-id="4ec28-242">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-242">**Arguments**</span></span> 

<span data-ttu-id="4ec28-243">`expression`: `Int32`, `Int64`, `Double`, nebo `Decimal`</span><span class="sxs-lookup"><span data-stu-id="4ec28-243">`expression`: `Int32`, `Int64`, `Double`, or `Decimal`</span></span> 

<span data-ttu-id="4ec28-244">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-244">**Return Value**</span></span> 

<span data-ttu-id="4ec28-245">`Int32`, `Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-245">An `Int32`, `Int64`, `Double`, or `Decimal`.</span></span> 

<span data-ttu-id="4ec28-246">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-246">**Example**</span></span> 

`SqlServer.SIGN(-10)`

## <a name="sinexpression"></a><span data-ttu-id="4ec28-247">Sin(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-247">SIN(expression)</span></span>

<span data-ttu-id="4ec28-248">Vypočítá trigonometrických sinus úhlu určeného v radiánech a vrátí `Double` výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-248">Calculates the trigonometric sine of the specified angle in radians, and returns a `Double` expression.</span></span> 

<span data-ttu-id="4ec28-249">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-249">**Arguments**</span></span> 

<span data-ttu-id="4ec28-250">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-250">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-251">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-251">**Return Value**</span></span> 

<span data-ttu-id="4ec28-252">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-252">A `Double`.</span></span> 

<span data-ttu-id="4ec28-253">**Příklad** `SqlServer.SIN(20)`</span><span class="sxs-lookup"><span data-stu-id="4ec28-253">**Example** `SqlServer.SIN(20)`</span></span>

## <a name="sqrtexpression"></a><span data-ttu-id="4ec28-254">Sqrt(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-254">SQRT(expression)</span></span>

<span data-ttu-id="4ec28-255">Vrátí druhou odmocninu z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-255">Returns the square root of the specified expression.</span></span> 

<span data-ttu-id="4ec28-256">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-256">**Arguments**</span></span> 

<span data-ttu-id="4ec28-257">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-257">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-258">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-258">**Return Value**</span></span> 

<span data-ttu-id="4ec28-259">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-259">A `Double`.</span></span> 

<span data-ttu-id="4ec28-260">**Příklad** `SqlServer.SQRT(3600)`</span><span class="sxs-lookup"><span data-stu-id="4ec28-260">**Example** `SqlServer.SQRT(3600)`</span></span>

## <a name="squareexpression"></a><span data-ttu-id="4ec28-261">Square(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-261">SQUARE(expression)</span></span>

<span data-ttu-id="4ec28-262">Vrátí druhou mocninu, z určeného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-262">Returns the square of the specified expression.</span></span> 

<span data-ttu-id="4ec28-263">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-263">**Arguments**</span></span> 

<span data-ttu-id="4ec28-264">`expression`: ODPOVĚĎ `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-264">`expression`: A `Double`.</span></span> 

<span data-ttu-id="4ec28-265">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-265">**Return Value**</span></span> 

<span data-ttu-id="4ec28-266">A `Double`.</span><span class="sxs-lookup"><span data-stu-id="4ec28-266">A `Double`.</span></span> 

<span data-ttu-id="4ec28-267">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-267">**Example**</span></span> 

`SqlServer.SQUARE(25)`

## <a name="tanexpression"></a><span data-ttu-id="4ec28-268">Tan(Expression)</span><span class="sxs-lookup"><span data-stu-id="4ec28-268">TAN(expression)</span></span>

<span data-ttu-id="4ec28-269">Vypočítá jeho tangens zadaného výrazu.</span><span class="sxs-lookup"><span data-stu-id="4ec28-269">Calculates the tangent of a specified expression.</span></span>

<span data-ttu-id="4ec28-270">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ec28-270">**Arguments**</span></span> 

<span data-ttu-id="4ec28-271">`expression`: `Double`</span><span class="sxs-lookup"><span data-stu-id="4ec28-271">`expression`: `Double`</span></span> 

<span data-ttu-id="4ec28-272">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ec28-272">**Return Value**</span></span> 

`Double` 

<span data-ttu-id="4ec28-273">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ec28-273">**Example**</span></span> 

`SqlServer.TAN(45.0)`
  
## <a name="see-also"></a><span data-ttu-id="4ec28-274">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ec28-274">See also</span></span>

<span data-ttu-id="4ec28-275">Další informace o matematických funkcí, které SqlClient podporuje najdete v dokumentaci pro verzi systému SQL Server, který jste zadali v manifestu zprostředkovatele, SqlClient:</span><span class="sxs-lookup"><span data-stu-id="4ec28-275">For more information about the mathematical functions that SqlClient supports, see the documentation for the SQL Server version that you specified in the SqlClient provider manifest:</span></span>  
  
<span data-ttu-id="4ec28-276">**SQL Server 2005:** [matematické funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span><span class="sxs-lookup"><span data-stu-id="4ec28-276">**SQL Server 2005:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2005/ms177516(v=sql.90))</span></span>  
<span data-ttu-id="4ec28-277">**SQL Server 2008:** [matematické funkce (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span><span class="sxs-lookup"><span data-stu-id="4ec28-277">**SQL Server 2008:** [Mathematical Functions (Transact-SQL)](https://docs.microsoft.com/previous-versions/sql/sql-server-2008/ms177516(v=sql.100))</span></span>  
<span data-ttu-id="4ec28-278">**SQL Server 2012 a novější:** [matematické funkce (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span><span class="sxs-lookup"><span data-stu-id="4ec28-278">**SQL Server 2012 and later:** [Mathematical Functions (Transact-SQL)](/sql/t-sql/functions/mathematical-functions-transact-sql?view=sql-server-2017)</span></span>   

 [<span data-ttu-id="4ec28-279">SqlClient pro funkce Entity Framework</span><span class="sxs-lookup"><span data-stu-id="4ec28-279">SqlClient for Entity Framework Functions</span></span>](sqlclient-for-ef-functions.md)
