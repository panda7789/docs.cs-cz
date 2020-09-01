---
description: sizeof – operátor – reference jazyka C#
title: sizeof – operátor – reference jazyka C#
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: f1358cbfb6cbc2942cef12e650f7bd362ba37a78
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89136873"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="b0dfb-103">sizeof – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b0dfb-103">sizeof operator (C# reference)</span></span>

<span data-ttu-id="b0dfb-104">`sizeof`Operátor vrátí počet bajtů obsazených proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-104">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="b0dfb-105">Argument `sizeof` operátoru musí být název [nespravovaného typu](../builtin-types/unmanaged-types.md) nebo parametr typu, který je [omezený](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) na nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-105">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="b0dfb-106">`sizeof`Operátor vyžaduje [nezabezpečený](../keywords/unsafe.md) kontext.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-106">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="b0dfb-107">Výrazy uvedené v následující tabulce jsou však vyhodnocovány v době kompilace do odpovídajících konstantních hodnot a nevyžadují nezabezpečený kontext:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-107">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="b0dfb-108">Výraz</span><span class="sxs-lookup"><span data-stu-id="b0dfb-108">Expression</span></span>|<span data-ttu-id="b0dfb-109">Hodnota konstanty</span><span class="sxs-lookup"><span data-stu-id="b0dfb-109">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="b0dfb-110">1</span><span class="sxs-lookup"><span data-stu-id="b0dfb-110">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="b0dfb-111">1</span><span class="sxs-lookup"><span data-stu-id="b0dfb-111">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="b0dfb-112">2</span><span class="sxs-lookup"><span data-stu-id="b0dfb-112">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="b0dfb-113">2</span><span class="sxs-lookup"><span data-stu-id="b0dfb-113">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="b0dfb-114">4</span><span class="sxs-lookup"><span data-stu-id="b0dfb-114">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="b0dfb-115">4</span><span class="sxs-lookup"><span data-stu-id="b0dfb-115">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="b0dfb-116">8</span><span class="sxs-lookup"><span data-stu-id="b0dfb-116">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="b0dfb-117">8</span><span class="sxs-lookup"><span data-stu-id="b0dfb-117">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="b0dfb-118">2</span><span class="sxs-lookup"><span data-stu-id="b0dfb-118">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="b0dfb-119">4</span><span class="sxs-lookup"><span data-stu-id="b0dfb-119">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="b0dfb-120">8</span><span class="sxs-lookup"><span data-stu-id="b0dfb-120">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="b0dfb-121">16</span><span class="sxs-lookup"><span data-stu-id="b0dfb-121">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="b0dfb-122">1</span><span class="sxs-lookup"><span data-stu-id="b0dfb-122">1</span></span>|

<span data-ttu-id="b0dfb-123">Nemusíte také používat nezabezpečený kontext, pokud je operandem `sizeof` operátoru název typu [výčtu](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="b0dfb-123">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="b0dfb-124">Následující příklad ukazuje použití `sizeof` operátoru:</span><span class="sxs-lookup"><span data-stu-id="b0dfb-124">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](snippets/shared/SizeOfOperator.cs)]

<span data-ttu-id="b0dfb-125">`sizeof`Operátor vrátí počet bajtů, které by byly přiděleny modulem CLR (Common Language Runtime) ve spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-125">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="b0dfb-126">U typů [struktury](../builtin-types/struct.md) tato hodnota zahrnuje jakékoli odsazení, jak ukazuje předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-126">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="b0dfb-127">Výsledek `sizeof` operátoru se může lišit od výsledku <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, která vrací velikost typu v *nespravované* paměti.</span><span class="sxs-lookup"><span data-stu-id="b0dfb-127">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="b0dfb-128">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0dfb-128">C# language specification</span></span>

<span data-ttu-id="b0dfb-129">Další informace naleznete v části [operátor sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="b0dfb-129">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b0dfb-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0dfb-130">See also</span></span>

- [<span data-ttu-id="b0dfb-131">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="b0dfb-131">C# reference</span></span>](../index.md)
- [<span data-ttu-id="b0dfb-132">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="b0dfb-132">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="b0dfb-133">Operátory související s ukazatelem</span><span class="sxs-lookup"><span data-stu-id="b0dfb-133">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="b0dfb-134">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="b0dfb-134">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="b0dfb-135">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="b0dfb-135">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="b0dfb-136">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="b0dfb-136">Generics in .NET</span></span>](../../../standard/generics/index.md)
