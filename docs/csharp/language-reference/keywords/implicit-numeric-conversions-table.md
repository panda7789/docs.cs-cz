---
title: Tabulka implicitních číselných převodů (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#], implicit numeric
- implicit numeric conversions [C#]
- numeric conversions [C#], implicit
- types [C#], implicit numeric conversions
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
ms.openlocfilehash: 4bbc6086dc5fd3838ef9361762c3068ca44efd0e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44047978"
---
# <a name="implicit-numeric-conversions-table-c-reference"></a><span data-ttu-id="e722a-102">Tabulka implicitních číselných převodů (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e722a-102">Implicit Numeric Conversions Table (C# Reference)</span></span>
<span data-ttu-id="e722a-103">V následující tabulce jsou uvedeny předdefinované implicitních číselných převodů.</span><span class="sxs-lookup"><span data-stu-id="e722a-103">The following table shows the predefined implicit numeric conversions.</span></span> <span data-ttu-id="e722a-104">Implicitní převod může dojít v mnoha situacích, včetně příkazů metody vyvolání a přiřazení.</span><span class="sxs-lookup"><span data-stu-id="e722a-104">Implicit conversions might occur in many situations, including method invoking and assignment statements.</span></span>  
  
|<span data-ttu-id="e722a-105">From</span><span class="sxs-lookup"><span data-stu-id="e722a-105">From</span></span>|<span data-ttu-id="e722a-106">Chcete-li</span><span class="sxs-lookup"><span data-stu-id="e722a-106">To</span></span>|  
|----------|--------|  
|[<span data-ttu-id="e722a-107">sbyte</span><span class="sxs-lookup"><span data-stu-id="e722a-107">sbyte</span></span>](../../../csharp/language-reference/keywords/sbyte.md)|<span data-ttu-id="e722a-108">`short`, `int`, `long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-108">`short`, `int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="e722a-109">byte</span><span class="sxs-lookup"><span data-stu-id="e722a-109">byte</span></span>](../../../csharp/language-reference/keywords/byte.md)|<span data-ttu-id="e722a-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-110">`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="e722a-111">short</span><span class="sxs-lookup"><span data-stu-id="e722a-111">short</span></span>](../../../csharp/language-reference/keywords/short.md)|<span data-ttu-id="e722a-112">`int`, `long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-112">`int`, `long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="e722a-113">ushort</span><span class="sxs-lookup"><span data-stu-id="e722a-113">ushort</span></span>](../../../csharp/language-reference/keywords/ushort.md)|<span data-ttu-id="e722a-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-114">`int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="e722a-115">int</span><span class="sxs-lookup"><span data-stu-id="e722a-115">int</span></span>](../../../csharp/language-reference/keywords/int.md)|<span data-ttu-id="e722a-116">`long`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-116">`long`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="e722a-117">uint</span><span class="sxs-lookup"><span data-stu-id="e722a-117">uint</span></span>](../../../csharp/language-reference/keywords/uint.md)|<span data-ttu-id="e722a-118">`long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-118">`long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="e722a-119">long</span><span class="sxs-lookup"><span data-stu-id="e722a-119">long</span></span>](../../../csharp/language-reference/keywords/long.md)|<span data-ttu-id="e722a-120">`float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-120">`float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="e722a-121">char</span><span class="sxs-lookup"><span data-stu-id="e722a-121">char</span></span>](../../../csharp/language-reference/keywords/char.md)|<span data-ttu-id="e722a-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-122">`ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double`, or `decimal`</span></span>|  
|[<span data-ttu-id="e722a-123">float</span><span class="sxs-lookup"><span data-stu-id="e722a-123">float</span></span>](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[<span data-ttu-id="e722a-124">ulong</span><span class="sxs-lookup"><span data-stu-id="e722a-124">ulong</span></span>](../../../csharp/language-reference/keywords/ulong.md)|<span data-ttu-id="e722a-125">`float`, `double`, nebo `decimal`</span><span class="sxs-lookup"><span data-stu-id="e722a-125">`float`, `double`, or `decimal`</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e722a-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e722a-126">Remarks</span></span>  
  
-   <span data-ttu-id="e722a-127">Přesnost, ale nikoli velikost může být ztraceno v převody z `int`, `uint`, `long`, nebo `ulong` k `float` a z `long` nebo `ulong` k `double`.</span><span class="sxs-lookup"><span data-stu-id="e722a-127">Precision but not magnitude might be lost in the conversions from `int`, `uint`,  `long`, or `ulong` to `float` and from `long` or `ulong` to `double`.</span></span>  
  
-   <span data-ttu-id="e722a-128">Neexistují žádné implicitní převody na `char` typu.</span><span class="sxs-lookup"><span data-stu-id="e722a-128">There are no implicit conversions to the `char` type.</span></span>  
  
-   <span data-ttu-id="e722a-129">Neexistují žádné implicitní převody mezi typy s plovoucí desetinnou čárkou a `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="e722a-129">There are no implicit conversions between floating-point types and the `decimal` type.</span></span>  
  
-   <span data-ttu-id="e722a-130">Konstantní výraz typu `int` lze převést na `sbyte`, `byte`, `short`, `ushort`, `uint`, nebo `ulong`, pokud má konstantní výraz hodnotu v rozsahu cílového umístění Zadejte.</span><span class="sxs-lookup"><span data-stu-id="e722a-130">A constant expression of type `int` can be converted to `sbyte`, `byte`, `short`, `ushort`, `uint`, or `ulong`, provided the value of the constant expression is within the range of the destination type.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="e722a-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e722a-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e722a-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="e722a-132">See Also</span></span>  

- [<span data-ttu-id="e722a-133">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e722a-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e722a-134">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e722a-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e722a-135">Tabulka celočíselných typů</span><span class="sxs-lookup"><span data-stu-id="e722a-135">Integral Types Table</span></span>](../../../csharp/language-reference/keywords/integral-types-table.md)  
- [<span data-ttu-id="e722a-136">Tabulka předdefinovaných typů</span><span class="sxs-lookup"><span data-stu-id="e722a-136">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
- [<span data-ttu-id="e722a-137">Tabulka explicitních číselných převodů</span><span class="sxs-lookup"><span data-stu-id="e722a-137">Explicit Numeric Conversions Table</span></span>](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)  
- [<span data-ttu-id="e722a-138">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="e722a-138">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)
