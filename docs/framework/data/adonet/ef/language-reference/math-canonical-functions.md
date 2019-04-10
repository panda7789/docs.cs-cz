---
title: Matematické kanonické funkce
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228767"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="78a08-102">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="78a08-102">Math Canonical Functions</span></span>

<span data-ttu-id="78a08-103">Entita SQL obsahuje následující matematické kanonické funkce:</span><span class="sxs-lookup"><span data-stu-id="78a08-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="78a08-104">Abs(Value)</span><span class="sxs-lookup"><span data-stu-id="78a08-104">Abs(value)</span></span>

<span data-ttu-id="78a08-105">Vrátí absolutní hodnotu `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-105">Returns the absolute value of `value`.</span></span>

**<span data-ttu-id="78a08-106">Arguments</span><span class="sxs-lookup"><span data-stu-id="78a08-106">Arguments</span></span>**

<span data-ttu-id="78a08-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, A `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="78a08-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="78a08-108">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78a08-108">Return Value</span></span>**

<span data-ttu-id="78a08-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-109">The type of `value`.</span></span>

**<span data-ttu-id="78a08-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="78a08-110">Example</span></span>**

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="78a08-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="78a08-111">Ceiling(value)</span></span>

<span data-ttu-id="78a08-112">Vrátí nejmenší celé číslo, které není menší než `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-112">Returns the smallest integer that is not less than `value`.</span></span>

**<span data-ttu-id="78a08-113">Arguments</span><span class="sxs-lookup"><span data-stu-id="78a08-113">Arguments</span></span>**

<span data-ttu-id="78a08-114">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="78a08-114">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="78a08-115">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78a08-115">Return Value</span></span>**

<span data-ttu-id="78a08-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-116">The type of `value`.</span></span>

**<span data-ttu-id="78a08-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="78a08-117">Example</span></span>**

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="78a08-118">Floor(Value)</span><span class="sxs-lookup"><span data-stu-id="78a08-118">Floor(value)</span></span>

<span data-ttu-id="78a08-119">Vrátí největší celé číslo, které není větší než `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-119">Returns the largest integer that is not greater than `value`.</span></span>

**<span data-ttu-id="78a08-120">Arguments</span><span class="sxs-lookup"><span data-stu-id="78a08-120">Arguments</span></span>**

<span data-ttu-id="78a08-121">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="78a08-121">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="78a08-122">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78a08-122">Return Value</span></span>**

<span data-ttu-id="78a08-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-123">The type of `value`.</span></span>

**<span data-ttu-id="78a08-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="78a08-124">Example</span></span>**

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="78a08-125">Napájení (hodnota, exponent)</span><span class="sxs-lookup"><span data-stu-id="78a08-125">Power(value, exponent)</span></span>

<span data-ttu-id="78a08-126">Vrátí výsledek zadaného `value` do zadaného `exponent`.</span><span class="sxs-lookup"><span data-stu-id="78a08-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

**<span data-ttu-id="78a08-127">Arguments</span><span class="sxs-lookup"><span data-stu-id="78a08-127">Arguments</span></span>**

|  |  |
|--|--|
|`value` | <span data-ttu-id="78a08-128">`Int32, Int64, Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="78a08-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="78a08-129">`Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="78a08-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

**<span data-ttu-id="78a08-130">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78a08-130">Return Value</span></span>**

<span data-ttu-id="78a08-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-131">The type of `value`.</span></span>

**<span data-ttu-id="78a08-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="78a08-132">Example</span></span>**

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="78a08-133">Round(Value)</span><span class="sxs-lookup"><span data-stu-id="78a08-133">Round(value)</span></span>

<span data-ttu-id="78a08-134">Vrátí celočíselnou část `value`, zaokrouhlený na nejbližší celé číslo.</span><span class="sxs-lookup"><span data-stu-id="78a08-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

**<span data-ttu-id="78a08-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="78a08-135">Arguments</span></span>**

<span data-ttu-id="78a08-136">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="78a08-136">A `Single`, `Double`, and `Decimal`.</span></span>

**<span data-ttu-id="78a08-137">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78a08-137">Return Value</span></span>**

<span data-ttu-id="78a08-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-138">The type of `value`.</span></span>

**<span data-ttu-id="78a08-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="78a08-139">Example</span></span>**

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="78a08-140">Round (hodnota číslic)</span><span class="sxs-lookup"><span data-stu-id="78a08-140">Round(value, digits)</span></span>

<span data-ttu-id="78a08-141">Vrátí `value`, zaokrouhleno na nejbližší zadaný `digits`.</span><span class="sxs-lookup"><span data-stu-id="78a08-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

**<span data-ttu-id="78a08-142">Arguments</span><span class="sxs-lookup"><span data-stu-id="78a08-142">Arguments</span></span>**

|  |  |
|--|--|
|`value`|`Double` <span data-ttu-id="78a08-143">or `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="78a08-143">or `Decimal`.</span></span>|
|`digits`|`Int16` <span data-ttu-id="78a08-144">or `Int32`.</span><span class="sxs-lookup"><span data-stu-id="78a08-144">or `Int32`.</span></span>|

**<span data-ttu-id="78a08-145">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78a08-145">Return Value</span></span>**

<span data-ttu-id="78a08-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-146">The type of `value`.</span></span>

**<span data-ttu-id="78a08-147">Příklad</span><span class="sxs-lookup"><span data-stu-id="78a08-147">Example</span></span>**

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="78a08-148">Zkrátit (hodnota číslic)</span><span class="sxs-lookup"><span data-stu-id="78a08-148">Truncate(value, digits)</span></span>

<span data-ttu-id="78a08-149">Vrátí `value`, došlo ke zkrácení na nejbližší zadaný `digits`.</span><span class="sxs-lookup"><span data-stu-id="78a08-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

**<span data-ttu-id="78a08-150">Arguments</span><span class="sxs-lookup"><span data-stu-id="78a08-150">Arguments</span></span>**

|  |  |
|--|--|
|`value`|`Double` <span data-ttu-id="78a08-151">or `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="78a08-151">or `Decimal`.</span></span>|
|`digits`|`Int16` <span data-ttu-id="78a08-152">or `Int32`.</span><span class="sxs-lookup"><span data-stu-id="78a08-152">or `Int32`.</span></span>|

**<span data-ttu-id="78a08-153">Návratová hodnota</span><span class="sxs-lookup"><span data-stu-id="78a08-153">Return Value</span></span>**

<span data-ttu-id="78a08-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="78a08-154">The type of `value`.</span></span>

**<span data-ttu-id="78a08-155">Příklad</span><span class="sxs-lookup"><span data-stu-id="78a08-155">Example</span></span>**

`Truncate(748.58,1)`  
  
 <span data-ttu-id="78a08-156">Tyto funkce vrátí `null` Pokud tento parametr zadaný `null` vstupu.</span><span class="sxs-lookup"><span data-stu-id="78a08-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="78a08-157">Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="78a08-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="78a08-158">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="78a08-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78a08-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="78a08-159">See also</span></span>

- [<span data-ttu-id="78a08-160">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="78a08-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
