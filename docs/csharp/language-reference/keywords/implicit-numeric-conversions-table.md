---
title: Tabulka implicitních číselných převodů - C# odkaz
ms.custom: seodec18
ms.date: 09/05/2018
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: f05ba1ee4e926f9f4c1b6427ecc60b41b45b06e9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661448"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="f1870-102">Tabulka implicitních číselných převodů (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f1870-102">Implicit numeric conversions table (C# Reference)</span></span>

<span data-ttu-id="f1870-103">V následující tabulce jsou uvedeny předdefinované implicitní převody mezi číselnými typy .NET.</span><span class="sxs-lookup"><span data-stu-id="f1870-103">The following table shows the predefined implicit conversions between .NET numeric types.</span></span>
  
|<span data-ttu-id="f1870-104">From</span><span class="sxs-lookup"><span data-stu-id="f1870-104">From</span></span>|<span data-ttu-id="f1870-105">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="f1870-105">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="f1870-106">sbyte</span><span class="sxs-lookup"><span data-stu-id="f1870-106">sbyte</span></span>](sbyte.md)|<span data-ttu-id="f1870-107">`short`, `int`, `long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-107">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-108">byte</span><span class="sxs-lookup"><span data-stu-id="f1870-108">byte</span></span>](byte.md)|<span data-ttu-id="f1870-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-109">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-110">char</span><span class="sxs-lookup"><span data-stu-id="f1870-110">char</span></span>](char.md)|<span data-ttu-id="f1870-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-111">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-112">short</span><span class="sxs-lookup"><span data-stu-id="f1870-112">short</span></span>](short.md)|<span data-ttu-id="f1870-113">`int`, `long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-113">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-114">ushort</span><span class="sxs-lookup"><span data-stu-id="f1870-114">ushort</span></span>](ushort.md)|<span data-ttu-id="f1870-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-115">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-116">int</span><span class="sxs-lookup"><span data-stu-id="f1870-116">int</span></span>](int.md)|<span data-ttu-id="f1870-117">`long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-117">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-118">uint</span><span class="sxs-lookup"><span data-stu-id="f1870-118">uint</span></span>](uint.md)|<span data-ttu-id="f1870-119">`long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-119">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-120">long</span><span class="sxs-lookup"><span data-stu-id="f1870-120">long</span></span>](long.md)|<span data-ttu-id="f1870-121">`float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-121">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-122">ulong</span><span class="sxs-lookup"><span data-stu-id="f1870-122">ulong</span></span>](ulong.md)|<span data-ttu-id="f1870-123">`float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="f1870-123">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="f1870-124">float</span><span class="sxs-lookup"><span data-stu-id="f1870-124">float</span></span>](float.md)|`double`|  
  
## <a name="remarks"></a><span data-ttu-id="f1870-125">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f1870-125">Remarks</span></span>  

- <span data-ttu-id="f1870-126">Žádné [celočíselného typu](integral-types-table.md) implicitně převést na libovolný [s plovoucí desetinnou čárkou typu](floating-point-types-table.md).</span><span class="sxs-lookup"><span data-stu-id="f1870-126">Any [integral type](integral-types-table.md) is implicitly convertible to any [floating-point type](floating-point-types-table.md).</span></span>

- <span data-ttu-id="f1870-127">Přesnost, ale nikoli velikost může být ztraceno v převody z `int`, `uint`, `long`, nebo `ulong` k `float` a z `long` nebo `ulong` k `double`.</span><span class="sxs-lookup"><span data-stu-id="f1870-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`, `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
- <span data-ttu-id="f1870-128">Neexistují žádné implicitní převody na `char`, `byte`, a `sbyte` typy.</span><span class="sxs-lookup"><span data-stu-id="f1870-128">There are no implicit conversions to the `char`, `byte`, and `sbyte` types.</span></span>  

- <span data-ttu-id="f1870-129">Neexistují žádné implicitní převody z `double` a `decimal` typy.</span><span class="sxs-lookup"><span data-stu-id="f1870-129">There are no implicit conversions from the `double` and `decimal` types.</span></span>
  
- <span data-ttu-id="f1870-130">Neexistují žádné implicitní převody mezi `decimal` typ a `float` nebo `double` typy.</span><span class="sxs-lookup"><span data-stu-id="f1870-130">There are no implicit conversions between the `decimal` type and the `float` or `double` types.</span></span>  
  
- <span data-ttu-id="f1870-131">Hodnota konstantní výraz typu `int` (například, Hodnota reprezentovaná celočíselný literál) lze převést na `sbyte`, `byte`, `short`, `ushort`, `uint`, nebo `ulong`, pokud má v rozsahu cílového typu:</span><span class="sxs-lookup"><span data-stu-id="f1870-131">A value of a constant expression of type `int` (for example, a value represented by an integral literal) can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided it's within the range of the destination type:</span></span>

  ```csharp
  byte a = 13;    // Compiles
  byte b = 300;   // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

<span data-ttu-id="f1870-132">Další informace o implicitních převodů, najdete v článku [implicitních převodů](~/_csharplang/spec/conversions.md#implicit-conversions) část [specifikace jazyka C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f1870-132">For more information about implicit conversions, see the [Implicit conversions](~/_csharplang/spec/conversions.md#implicit-conversions) section of the [C# language specification](../language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f1870-133">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f1870-133">See also</span></span>

- [<span data-ttu-id="f1870-134">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f1870-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f1870-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="f1870-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f1870-136">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="f1870-136">Integral types table</span></span>](integral-types-table.md)
- [<span data-ttu-id="f1870-137">Tabulka typů s plovoucí desetinnou čárkou</span><span class="sxs-lookup"><span data-stu-id="f1870-137">Floating-point types table</span></span>](floating-point-types-table.md)
- [<span data-ttu-id="f1870-138">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="f1870-138">Built-in types table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="f1870-139">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="f1870-139">Explicit numeric conversions table</span></span>](explicit-numeric-conversions-table.md)
- [<span data-ttu-id="f1870-140">Přetypování a převody typu</span><span class="sxs-lookup"><span data-stu-id="f1870-140">Casting and type conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
