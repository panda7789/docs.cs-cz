---
title: Tabulka implicitních číselných převodů (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 2d417a2020656f300de0517526742679388f262e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33217191"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="45ef1-102">Tabulka implicitních číselných převodů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="45ef1-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="45ef1-103">V následující tabulce jsou předdefinované implicitní číselné převody.</span><span class="sxs-lookup"><span data-stu-id="45ef1-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="45ef1-104">Implicitní převody může dojít v mnoha situacích, včetně metoda vyvolání a přiřazení příkazy.</span><span class="sxs-lookup"><span data-stu-id="45ef1-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="45ef1-105">From</span><span class="sxs-lookup"><span data-stu-id="45ef1-105">From</span></span>|<span data-ttu-id="45ef1-106">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="45ef1-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="45ef1-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="45ef1-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="45ef1-108">`short`, `int`, `long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="45ef1-109">byte</span><span class="sxs-lookup"><span data-stu-id="45ef1-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="45ef1-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="45ef1-111">short</span><span class="sxs-lookup"><span data-stu-id="45ef1-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="45ef1-112">`int`, `long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="45ef1-113">ushort</span><span class="sxs-lookup"><span data-stu-id="45ef1-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="45ef1-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="45ef1-115">int</span><span class="sxs-lookup"><span data-stu-id="45ef1-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="45ef1-116">`long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="45ef1-117">uint</span><span class="sxs-lookup"><span data-stu-id="45ef1-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="45ef1-118">`long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="45ef1-119">long</span><span class="sxs-lookup"><span data-stu-id="45ef1-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="45ef1-120">`float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="45ef1-121">char</span><span class="sxs-lookup"><span data-stu-id="45ef1-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="45ef1-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="45ef1-123">float</span><span class="sxs-lookup"><span data-stu-id="45ef1-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="45ef1-124">ulong</span><span class="sxs-lookup"><span data-stu-id="45ef1-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="45ef1-125">`float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="45ef1-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="45ef1-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="45ef1-126">Remarks</span></span>  
  
-   <span data-ttu-id="45ef1-127">Přesnost, ale není rozsahem může dojít ke ztrátě, při převodu z `int`, `uint`, `long`, nebo `ulong` k `float` a z `long` nebo `ulong` k `double`.</span><span class="sxs-lookup"><span data-stu-id="45ef1-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="45ef1-128">Neexistují žádná implicitní převod `char` typu.</span><span class="sxs-lookup"><span data-stu-id="45ef1-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="45ef1-129">Neexistují žádná implicitní převody mezi typy s plovoucí desetinnou čárkou a `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="45ef1-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="45ef1-130">Konstantní výraz typu `int` lze převést na `sbyte`, `byte`, `short`, `ushort`, `uint`, nebo `ulong`, pokud konstantní výraz hodnotu v rozsahu cílového typ.</span><span class="sxs-lookup"><span data-stu-id="45ef1-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="45ef1-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="45ef1-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45ef1-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="45ef1-132">See Also</span></span>  
 [<span data-ttu-id="45ef1-133">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="45ef1-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="45ef1-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="45ef1-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="45ef1-135">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="45ef1-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [<span data-ttu-id="45ef1-136">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="45ef1-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="45ef1-137">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="45ef1-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
 [<span data-ttu-id="45ef1-138">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="45ef1-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
