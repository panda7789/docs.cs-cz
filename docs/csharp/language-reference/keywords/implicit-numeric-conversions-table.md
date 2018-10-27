---
title: Tabulka implicitních číselných převodů (referenční dokumentace jazyka C#)
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: c3c0153a0ae3e07839822c8bb978b1a09277bd53
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188700"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="30440-102">Tabulka implicitních číselných převodů (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="30440-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="30440-103">V následující tabulce jsou uvedeny předdefinované implicitní převody mezi číselnými typy .NET.</span><span class="sxs-lookup"><span data-stu-id="30440-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="30440-104">From</span><span class="sxs-lookup"><span data-stu-id="30440-104">From</span></span>|<span data-ttu-id="30440-105">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="30440-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="30440-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="30440-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="30440-107">`short`, `int`, `long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="30440-108">byte</span><span class="sxs-lookup"><span data-stu-id="30440-108">byte</span></span>](byte.md)|<span data-ttu-id="30440-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="30440-110">short</span><span class="sxs-lookup"><span data-stu-id="30440-110">short</span></span>](short.md)|<span data-ttu-id="30440-111">`int`, `long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-111">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="30440-112">ushort</span><span class="sxs-lookup"><span data-stu-id="30440-112">ushort</span></span>](ushort.md)|<span data-ttu-id="30440-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-113">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="30440-114">int</span><span class="sxs-lookup"><span data-stu-id="30440-114">int</span></span>](int.md)|<span data-ttu-id="30440-115">`long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-115">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="30440-116">uint</span><span class="sxs-lookup"><span data-stu-id="30440-116">uint</span></span>](uint.md)|<span data-ttu-id="30440-117">`long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-117">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="30440-118">long</span><span class="sxs-lookup"><span data-stu-id="30440-118">long</span></span>](long.md)|<span data-ttu-id="30440-119">`float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-119">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="30440-120">char</span><span class="sxs-lookup"><span data-stu-id="30440-120">char</span></span>](char.md)|<span data-ttu-id="30440-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-121">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="30440-122">float</span><span class="sxs-lookup"><span data-stu-id="30440-122">float</span></span>](float.md)|`double`|  
|[<span data-ttu-id="30440-123">ulong</span><span class="sxs-lookup"><span data-stu-id="30440-123">ulong</span></span>](ulong.md)|<span data-ttu-id="30440-124">`float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="30440-124">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30440-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="30440-125">Remarks</span></span>  

- <span data-ttu-id="30440-126">Žádné [celočíselného typu](integral-types-table.md) implicitně převést na libovolný [s plovoucí desetinnou čárkou typu](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="30440-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="30440-127">Přesnost, ale nikoli velikost může být ztraceno v převody z `int`, `uint`, `long`, nebo `ulong` k `float` a z `long` nebo `ulong` k `double`.</span><span class="sxs-lookup"><span data-stu-id="30440-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="30440-128">Neexistují žádné implicitní převody na `char` typu.</span><span class="sxs-lookup"><span data-stu-id="30440-128">There are no implicit conversions to the `char` type.</span></span>  
  
- <span data-ttu-id="30440-129">Neexistují žádné implicitní převody mezi `float` a `double` typy a `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="30440-129">There are no implicit conversions between the `float` and `double` types and the `decimal` type.</span></span>  
  
- <span data-ttu-id="30440-130">Hodnota konstantní výraz typu `int` (například, Hodnota reprezentovaná celočíselný literál) lze převést na `sbyte`, `byte`, `short`, `ushort`, `uint`, nebo `ulong`, pokud má v rozsahu cílového typu:</span><span class="sxs-lookup"><span data-stu-id="30440-130">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="30440-131">Další informace o implicitních převodů, najdete v článku [implicitních převodů](~/_csharplang/spec/conversions.md#implicit-conversions) část [specifikace jazyka C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="30440-131">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="30440-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="30440-132">See also</span></span>

- [<span data-ttu-id="30440-133">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="30440-133">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="30440-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="30440-134">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="30440-135">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="30440-135">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="30440-136">Tabulka typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="30440-136">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="30440-137">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="30440-137">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="30440-138">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="30440-138">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="30440-139">Přetypování a převody typu</span><span class="sxs-lookup"><span data-stu-id="30440-139">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
