---
title: Matematické kanonické funkce
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 9417ff9836912017c9d88bb24a18849aaac2836a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70250311"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="4ba7b-102">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="4ba7b-102">Math Canonical Functions</span></span>

<span data-ttu-id="4ba7b-103">Entity SQL obsahuje následující matematické kanonické funkce:</span><span class="sxs-lookup"><span data-stu-id="4ba7b-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="4ba7b-104">ABS (hodnota)</span><span class="sxs-lookup"><span data-stu-id="4ba7b-104">Abs(value)</span></span>

<span data-ttu-id="4ba7b-105">Vrátí absolutní hodnotu `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="4ba7b-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-106">**Arguments**</span></span>

<span data-ttu-id="4ba7b-107">`Int16`A `Int32` ,,`Int64`, ,`Single`,a. `Double` `Byte` `Decimal`</span><span class="sxs-lookup"><span data-stu-id="4ba7b-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4ba7b-108">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-108">**Return Value**</span></span>

<span data-ttu-id="4ba7b-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-109">The type of `value`.</span></span>

<span data-ttu-id="4ba7b-110">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="4ba7b-111">Strop (hodnota)</span><span class="sxs-lookup"><span data-stu-id="4ba7b-111">Ceiling(value)</span></span>

<span data-ttu-id="4ba7b-112">Vrátí nejmenší celé číslo, které není menší než `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="4ba7b-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-113">**Arguments**</span></span>

<span data-ttu-id="4ba7b-114">A `Single`, `Double`a .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="4ba7b-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4ba7b-115">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-115">**Return Value**</span></span>

<span data-ttu-id="4ba7b-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-116">The type of `value`.</span></span>

<span data-ttu-id="4ba7b-117">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="4ba7b-118">Floor (hodnota)</span><span class="sxs-lookup"><span data-stu-id="4ba7b-118">Floor(value)</span></span>

<span data-ttu-id="4ba7b-119">Vrátí největší celé číslo, které není větší než `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="4ba7b-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-120">**Arguments**</span></span>

<span data-ttu-id="4ba7b-121">A `Single`, `Double`a .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="4ba7b-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4ba7b-122">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-122">**Return Value**</span></span>

<span data-ttu-id="4ba7b-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-123">The type of `value`.</span></span>

<span data-ttu-id="4ba7b-124">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="4ba7b-125">Napájení (hodnota, exponent)</span><span class="sxs-lookup"><span data-stu-id="4ba7b-125">Power(value, exponent)</span></span>

<span data-ttu-id="4ba7b-126">Vrátí výsledek zadaný `value` na určenou `exponent`hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="4ba7b-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="4ba7b-128">A `Int32, Int64, Double`, nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="4ba7b-129">A `Int64`, `Double`nebo .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="4ba7b-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="4ba7b-130">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-130">**Return Value**</span></span>

<span data-ttu-id="4ba7b-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-131">The type of `value`.</span></span>

<span data-ttu-id="4ba7b-132">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="4ba7b-133">Round (hodnota)</span><span class="sxs-lookup"><span data-stu-id="4ba7b-133">Round(value)</span></span>

<span data-ttu-id="4ba7b-134">Vrátí celočíselnou část `value`zaokrouhlenou na nejbližší celé číslo.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="4ba7b-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-135">**Arguments**</span></span>

<span data-ttu-id="4ba7b-136">A `Single`, `Double`a .`Decimal`</span><span class="sxs-lookup"><span data-stu-id="4ba7b-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="4ba7b-137">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-137">**Return Value**</span></span>

<span data-ttu-id="4ba7b-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-138">The type of `value`.</span></span>

<span data-ttu-id="4ba7b-139">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="4ba7b-140">Round (hodnota; číslice)</span><span class="sxs-lookup"><span data-stu-id="4ba7b-140">Round(value, digits)</span></span>

<span data-ttu-id="4ba7b-141">Vrátí zaokrouhlit na nejbližší určený `digits`. `value`</span><span class="sxs-lookup"><span data-stu-id="4ba7b-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="4ba7b-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="4ba7b-143">`Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="4ba7b-144">`Int16`nebo `Int32`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="4ba7b-145">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-145">**Return Value**</span></span>

<span data-ttu-id="4ba7b-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-146">The type of `value`.</span></span>

<span data-ttu-id="4ba7b-147">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="4ba7b-148">Zkrátit (hodnota, číslice)</span><span class="sxs-lookup"><span data-stu-id="4ba7b-148">Truncate(value, digits)</span></span>

<span data-ttu-id="4ba7b-149">Vrátí hodnotu `digits`, která je zkrácena na nejbližší určenou. `value`</span><span class="sxs-lookup"><span data-stu-id="4ba7b-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="4ba7b-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="4ba7b-151">`Double`nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="4ba7b-152">`Int16`nebo `Int32`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="4ba7b-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-153">**Return Value**</span></span>

<span data-ttu-id="4ba7b-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-154">The type of `value`.</span></span>

<span data-ttu-id="4ba7b-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="4ba7b-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="4ba7b-156">Tyto funkce budou v `null` případě zadaného `null` vstupu vráceny.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="4ba7b-157">Ekvivalentní funkce jsou k dispozici ve spravovaném zprostředkovateli klienta Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="4ba7b-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="4ba7b-158">Další informace najdete v tématu [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="4ba7b-158">For more information, see [SqlClient for Entity Framework Functions](../sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ba7b-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4ba7b-159">See also</span></span>

- [<span data-ttu-id="4ba7b-160">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="4ba7b-160">Canonical Functions</span></span>](canonical-functions.md)
