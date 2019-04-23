---
title: Matematické kanonické funkce
ms.date: 03/30/2017
ms.assetid: 6f6cddc6-b561-4ebe-84b6-841ef5b4113b
ms.openlocfilehash: f575785bb198251ef50ba3563e736946253c9526
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59228767"
---
# <a name="math-canonical-functions"></a><span data-ttu-id="01514-102">Matematické kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="01514-102">Math Canonical Functions</span></span>

<span data-ttu-id="01514-103">Entita SQL obsahuje následující matematické kanonické funkce:</span><span class="sxs-lookup"><span data-stu-id="01514-103">Entity SQL includes the following math canonical functions:</span></span>
  
## <a name="absvalue"></a><span data-ttu-id="01514-104">Abs(Value)</span><span class="sxs-lookup"><span data-stu-id="01514-104">Abs(value)</span></span>

<span data-ttu-id="01514-105">Vrátí absolutní hodnotu `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-105">Returns the absolute value of `value`.</span></span>

<span data-ttu-id="01514-106">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="01514-106">**Arguments**</span></span>

<span data-ttu-id="01514-107">`Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, A `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="01514-107">An `Int16`, `Int32`, `Int64`, `Byte`, `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="01514-108">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="01514-108">**Return Value**</span></span>

<span data-ttu-id="01514-109">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-109">The type of `value`.</span></span>

<span data-ttu-id="01514-110">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="01514-110">**Example**</span></span>

`Abs(-2)`

## <a name="ceilingvalue"></a><span data-ttu-id="01514-111">CEILING(Value)</span><span class="sxs-lookup"><span data-stu-id="01514-111">Ceiling(value)</span></span>

<span data-ttu-id="01514-112">Vrátí nejmenší celé číslo, které není menší než `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-112">Returns the smallest integer that is not less than `value`.</span></span>

<span data-ttu-id="01514-113">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="01514-113">**Arguments**</span></span>

<span data-ttu-id="01514-114">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="01514-114">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="01514-115">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="01514-115">**Return Value**</span></span>

<span data-ttu-id="01514-116">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-116">The type of `value`.</span></span>

<span data-ttu-id="01514-117">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="01514-117">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_ceiling)]
[!code-sql[DP EntityServices Concepts#EDM_CEILING](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_ceiling)]

## <a name="floorvalue"></a><span data-ttu-id="01514-118">Floor(Value)</span><span class="sxs-lookup"><span data-stu-id="01514-118">Floor(value)</span></span>

<span data-ttu-id="01514-119">Vrátí největší celé číslo, které není větší než `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-119">Returns the largest integer that is not greater than `value`.</span></span>

<span data-ttu-id="01514-120">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="01514-120">**Arguments**</span></span>

<span data-ttu-id="01514-121">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="01514-121">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="01514-122">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="01514-122">**Return Value**</span></span>

<span data-ttu-id="01514-123">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-123">The type of `value`.</span></span>

<span data-ttu-id="01514-124">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="01514-124">**Example**</span></span>

[!code-csharp[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/csharp/VS_Snippets_Data/dp entityservices concepts/cs/entitysql.cs#edm_floor)]
[!code-sql[DP EntityServices Concepts#EDM_FLOOR](~/samples/snippets/tsql/VS_Snippets_Data/dp entityservices concepts/tsql/entitysql.sql#edm_floor)]

## <a name="powervalue-exponent"></a><span data-ttu-id="01514-125">Napájení (hodnota, exponent)</span><span class="sxs-lookup"><span data-stu-id="01514-125">Power(value, exponent)</span></span>

<span data-ttu-id="01514-126">Vrátí výsledek zadaného `value` do zadaného `exponent`.</span><span class="sxs-lookup"><span data-stu-id="01514-126">Returns the result of the specified `value` to the specified `exponent`.</span></span>

<span data-ttu-id="01514-127">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="01514-127">**Arguments**</span></span>

|  |  |
|--|--|
|`value` | <span data-ttu-id="01514-128">`Int32, Int64, Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="01514-128">An `Int32, Int64, Double`, or `Decimal`.</span></span> |
|`exponent` | <span data-ttu-id="01514-129">`Int64`, `Double`, Nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="01514-129">An `Int64`, `Double`, or `Decimal`.</span></span> |

<span data-ttu-id="01514-130">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="01514-130">**Return Value**</span></span>

<span data-ttu-id="01514-131">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-131">The type of `value`.</span></span>

<span data-ttu-id="01514-132">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="01514-132">**Example**</span></span>

`Power(748.58,2)`

## <a name="roundvalue"></a><span data-ttu-id="01514-133">Round(Value)</span><span class="sxs-lookup"><span data-stu-id="01514-133">Round(value)</span></span>

<span data-ttu-id="01514-134">Vrátí celočíselnou část `value`, zaokrouhlený na nejbližší celé číslo.</span><span class="sxs-lookup"><span data-stu-id="01514-134">Returns the integer portion of `value`, rounded to the nearest integer.</span></span>

<span data-ttu-id="01514-135">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="01514-135">**Arguments**</span></span>

<span data-ttu-id="01514-136">A `Single`, `Double`, a `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="01514-136">A `Single`, `Double`, and `Decimal`.</span></span>

<span data-ttu-id="01514-137">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="01514-137">**Return Value**</span></span>

<span data-ttu-id="01514-138">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-138">The type of `value`.</span></span>

<span data-ttu-id="01514-139">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="01514-139">**Example**</span></span>

`Round(748.58)`

## <a name="roundvalue-digits"></a><span data-ttu-id="01514-140">Round (hodnota číslic)</span><span class="sxs-lookup"><span data-stu-id="01514-140">Round(value, digits)</span></span>

<span data-ttu-id="01514-141">Vrátí `value`, zaokrouhleno na nejbližší zadaný `digits`.</span><span class="sxs-lookup"><span data-stu-id="01514-141">Returns the `value`, rounded to the nearest specified `digits`.</span></span>

<span data-ttu-id="01514-142">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="01514-142">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="01514-143">`Double` nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="01514-143">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="01514-144">`Int16` nebo `Int32`.</span><span class="sxs-lookup"><span data-stu-id="01514-144">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="01514-145">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="01514-145">**Return Value**</span></span>

<span data-ttu-id="01514-146">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-146">The type of `value`.</span></span>

<span data-ttu-id="01514-147">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="01514-147">**Example**</span></span>

`Round(748.58,1)`

## <a name="truncatevalue-digits"></a><span data-ttu-id="01514-148">Zkrátit (hodnota číslic)</span><span class="sxs-lookup"><span data-stu-id="01514-148">Truncate(value, digits)</span></span>

<span data-ttu-id="01514-149">Vrátí `value`, došlo ke zkrácení na nejbližší zadaný `digits`.</span><span class="sxs-lookup"><span data-stu-id="01514-149">Returns the `value`, truncated to the nearest specified `digits`.</span></span>

<span data-ttu-id="01514-150">**Argumenty**</span><span class="sxs-lookup"><span data-stu-id="01514-150">**Arguments**</span></span>

|  |  |
|--|--|
|`value`|<span data-ttu-id="01514-151">`Double` nebo `Decimal`.</span><span class="sxs-lookup"><span data-stu-id="01514-151">`Double` or `Decimal`.</span></span>|
|`digits`|<span data-ttu-id="01514-152">`Int16` nebo `Int32`.</span><span class="sxs-lookup"><span data-stu-id="01514-152">`Int16` or `Int32`.</span></span>|

<span data-ttu-id="01514-153">**Návratová hodnota**</span><span class="sxs-lookup"><span data-stu-id="01514-153">**Return Value**</span></span>

<span data-ttu-id="01514-154">Typ `value`.</span><span class="sxs-lookup"><span data-stu-id="01514-154">The type of `value`.</span></span>

<span data-ttu-id="01514-155">**Příklad**</span><span class="sxs-lookup"><span data-stu-id="01514-155">**Example**</span></span>

`Truncate(748.58,1)`  
  
 <span data-ttu-id="01514-156">Tyto funkce vrátí `null` Pokud tento parametr zadaný `null` vstupu.</span><span class="sxs-lookup"><span data-stu-id="01514-156">These functions will return `null` if given `null` input.</span></span>  
  
 <span data-ttu-id="01514-157">Ekvivalentní funkce je k dispozici ve zprostředkovateli spravovaného klienta Microsoft SQL.</span><span class="sxs-lookup"><span data-stu-id="01514-157">Equivalent functionality is available in the Microsoft SQL Client Managed Provider.</span></span> <span data-ttu-id="01514-158">Další informace najdete v tématu [SqlClient pro funkce Entity Framework](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span><span class="sxs-lookup"><span data-stu-id="01514-158">For more information, see [SqlClient for Entity Framework Functions](../../../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-functions.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01514-159">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01514-159">See also</span></span>

- [<span data-ttu-id="01514-160">Kanonické funkce</span><span class="sxs-lookup"><span data-stu-id="01514-160">Canonical Functions</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/canonical-functions.md)
