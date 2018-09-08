---
title: Matematické kanonické funkce
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: 0fc9f4942c3f76f139ab7e4400005f0bfe80204e
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44204679"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="9763e-102">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="9763e-102">Math Canonical Functions</span></span>

<span data-ttu-id="9763e-103">Entita SQL obsahuje následující matematické kanonické funkce:</span><span class="sxs-lookup"><span data-stu-id="9763e-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="9763e-104">Abs(Value)</span><span class="sxs-lookup"><span data-stu-id="9763e-104">Abs(value)</span></span>

<span data-ttu-id="9763e-105">Vrátí absolutní hodnotu `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="9763e-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="9763e-106">**Arguments**</span></span>

<span data-ttu-id="9763e-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, A `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9763e-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="9763e-108">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9763e-108">**Return Value**</span></span>

<span data-ttu-id="9763e-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-109">The type of `value`.</span></span>

<span data-ttu-id="9763e-110">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="9763e-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="9763e-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="9763e-111">Ceiling(value)</span></span>

<span data-ttu-id="9763e-112">Vrátí nejmenší celé číslo, které není menší než `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="9763e-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="9763e-113">**Arguments**</span></span>

<span data-ttu-id="9763e-114">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9763e-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="9763e-115">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9763e-115">**Return Value**</span></span>

<span data-ttu-id="9763e-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-116">The type of `value`.</span></span>

<span data-ttu-id="9763e-117">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="9763e-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="9763e-118">Floor(Value)</span><span class="sxs-lookup"><span data-stu-id="9763e-118">Floor(value)</span></span>

<span data-ttu-id="9763e-119">Vrátí největší celé číslo, které není větší než `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="9763e-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="9763e-120">**Arguments**</span></span>

<span data-ttu-id="9763e-121">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9763e-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="9763e-122">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9763e-122">**Return Value**</span></span>

<span data-ttu-id="9763e-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-123">The type of `value`.</span></span>

<span data-ttu-id="9763e-124">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="9763e-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="9763e-125">Napájení (hodnota, exponent)</span><span class="sxs-lookup"><span data-stu-id="9763e-125">Power(value, exponent)</span></span>

<span data-ttu-id="9763e-126">Vrátí výsledek zadaného `value` do zadaného `exponent`.</span><span class="sxs-lookup"><span data-stu-id="9763e-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="9763e-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="9763e-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="9763e-128">`Int32, Int64, Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9763e-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="9763e-129">`Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9763e-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="9763e-130">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9763e-130">**Return Value**</span></span>

<span data-ttu-id="9763e-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-131">The type of `value`.</span></span>

<span data-ttu-id="9763e-132">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="9763e-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="9763e-133">Round(Value)</span><span class="sxs-lookup"><span data-stu-id="9763e-133">Round(value)</span></span>

<span data-ttu-id="9763e-134">Vrátí celočíselnou část `value`, zaokrouhlený na nejbližší celé číslo.</span><span class="sxs-lookup"><span data-stu-id="9763e-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="9763e-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="9763e-135">**Arguments**</span></span>

<span data-ttu-id="9763e-136">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9763e-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="9763e-137">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9763e-137">**Return Value**</span></span>

<span data-ttu-id="9763e-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-138">The type of `value`.</span></span>

<span data-ttu-id="9763e-139">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="9763e-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="9763e-140">Round (hodnota číslic)</span><span class="sxs-lookup"><span data-stu-id="9763e-140">Round(value, digits)</span></span>

<span data-ttu-id="9763e-141">Vrátí `value`, zaokrouhleno na nejbližší zadaný `digits`.</span><span class="sxs-lookup"><span data-stu-id="9763e-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="9763e-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="9763e-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="9763e-143">`Double` nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9763e-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="9763e-144">`Int16` nebo `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9763e-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="9763e-145">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9763e-145">**Return Value**</span></span>

<span data-ttu-id="9763e-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-146">The type of `value`.</span></span>

<span data-ttu-id="9763e-147">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="9763e-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="9763e-148">Zkrátit (hodnota číslic)</span><span class="sxs-lookup"><span data-stu-id="9763e-148">Truncate(value, digits)</span></span>

<span data-ttu-id="9763e-149">Vrátí `value`, došlo ke zkrácení na nejbližší zadaný `digits`.</span><span class="sxs-lookup"><span data-stu-id="9763e-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="9763e-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="9763e-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="9763e-151">`Double` nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="9763e-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="9763e-152">`Int16` nebo `Int32`.</span><span class="sxs-lookup"><span data-stu-id="9763e-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="9763e-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="9763e-153">**Return Value**</span></span>

<span data-ttu-id="9763e-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="9763e-154">The type of `value`.</span></span>

<span data-ttu-id="9763e-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="9763e-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="9763e-156">Tyto funkce vrátí `null` Pokud tento parametr zadaný `null` vstupu.</span><span class="sxs-lookup"><span data-stu-id="9763e-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="9763e-157">Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="9763e-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="9763e-158">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="9763e-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9763e-159">Viz také</span><span class="sxs-lookup"><span data-stu-id="9763e-159">See Also</span></span>  
 [<span data-ttu-id="9763e-160">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="9763e-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
