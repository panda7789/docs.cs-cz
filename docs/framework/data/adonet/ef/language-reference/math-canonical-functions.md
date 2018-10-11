---
title: Matematické kanonické funkce
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49087606"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="aef4d-102">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="aef4d-102">Math Canonical Functions</span></span>

<span data-ttu-id="aef4d-103">Entita SQL obsahuje následující matematické kanonické funkce:</span><span class="sxs-lookup"><span data-stu-id="aef4d-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="aef4d-104">Abs(Value)</span><span class="sxs-lookup"><span data-stu-id="aef4d-104">Abs(value)</span></span>

<span data-ttu-id="aef4d-105">Vrátí absolutní hodnotu `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="aef4d-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="aef4d-106">**Arguments**</span></span>

<span data-ttu-id="aef4d-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, A `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="aef4d-108">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="aef4d-108">**Return Value**</span></span>

<span data-ttu-id="aef4d-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-109">The type of `value`.</span></span>

<span data-ttu-id="aef4d-110">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="aef4d-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="aef4d-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="aef4d-111">Ceiling(value)</span></span>

<span data-ttu-id="aef4d-112">Vrátí nejmenší celé číslo, které není menší než `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="aef4d-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="aef4d-113">**Arguments**</span></span>

<span data-ttu-id="aef4d-114">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="aef4d-115">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="aef4d-115">**Return Value**</span></span>

<span data-ttu-id="aef4d-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-116">The type of `value`.</span></span>

<span data-ttu-id="aef4d-117">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="aef4d-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="aef4d-118">Floor(Value)</span><span class="sxs-lookup"><span data-stu-id="aef4d-118">Floor(value)</span></span>

<span data-ttu-id="aef4d-119">Vrátí největší celé číslo, které není větší než `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="aef4d-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="aef4d-120">**Arguments**</span></span>

<span data-ttu-id="aef4d-121">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="aef4d-122">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="aef4d-122">**Return Value**</span></span>

<span data-ttu-id="aef4d-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-123">The type of `value`.</span></span>

<span data-ttu-id="aef4d-124">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="aef4d-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="aef4d-125">Napájení (hodnota, exponent)</span><span class="sxs-lookup"><span data-stu-id="aef4d-125">Power(value, exponent)</span></span>

<span data-ttu-id="aef4d-126">Vrátí výsledek zadaného `value` do zadaného `exponent`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="aef4d-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="aef4d-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="aef4d-128">`Int32, Int64, Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="aef4d-129">`Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="aef4d-130">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="aef4d-130">**Return Value**</span></span>

<span data-ttu-id="aef4d-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-131">The type of `value`.</span></span>

<span data-ttu-id="aef4d-132">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="aef4d-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="aef4d-133">Round(Value)</span><span class="sxs-lookup"><span data-stu-id="aef4d-133">Round(value)</span></span>

<span data-ttu-id="aef4d-134">Vrátí celočíselnou část `value`, zaokrouhlený na nejbližší celé číslo.</span><span class="sxs-lookup"><span data-stu-id="aef4d-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="aef4d-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="aef4d-135">**Arguments**</span></span>

<span data-ttu-id="aef4d-136">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="aef4d-137">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="aef4d-137">**Return Value**</span></span>

<span data-ttu-id="aef4d-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-138">The type of `value`.</span></span>

<span data-ttu-id="aef4d-139">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="aef4d-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="aef4d-140">Round (hodnota číslic)</span><span class="sxs-lookup"><span data-stu-id="aef4d-140">Round(value, digits)</span></span>

<span data-ttu-id="aef4d-141">Vrátí `value`, zaokrouhleno na nejbližší zadaný `digits`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="aef4d-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="aef4d-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="aef4d-143">`Double` nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="aef4d-144">`Int16` nebo `Int32`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="aef4d-145">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="aef4d-145">**Return Value**</span></span>

<span data-ttu-id="aef4d-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-146">The type of `value`.</span></span>

<span data-ttu-id="aef4d-147">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="aef4d-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="aef4d-148">Zkrátit (hodnota číslic)</span><span class="sxs-lookup"><span data-stu-id="aef4d-148">Truncate(value, digits)</span></span>

<span data-ttu-id="aef4d-149">Vrátí `value`, došlo ke zkrácení na nejbližší zadaný `digits`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="aef4d-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="aef4d-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="aef4d-151">`Double` nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="aef4d-152">`Int16` nebo `Int32`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="aef4d-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="aef4d-153">**Return Value**</span></span>

<span data-ttu-id="aef4d-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="aef4d-154">The type of `value`.</span></span>

<span data-ttu-id="aef4d-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="aef4d-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="aef4d-156">Tyto funkce vrátí `null` Pokud tento parametr zadaný `null` vstupu.</span><span class="sxs-lookup"><span data-stu-id="aef4d-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="aef4d-157">Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="aef4d-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="aef4d-158">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="aef4d-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aef4d-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="aef4d-159">See Also</span></span>  
 [<span data-ttu-id="aef4d-160">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="aef4d-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
