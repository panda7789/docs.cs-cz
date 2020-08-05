---
title: sizeof – operátor – reference jazyka C#
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 84dc67be95fa65f6c46dab02af2ee7bc08d2ec31
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87555224"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="91c68-102">sizeof – operátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="91c68-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="91c68-103">`sizeof`Operátor vrátí počet bajtů obsazených proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="91c68-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="91c68-104">Argument `sizeof` operátoru musí být název [nespravovaného typu](../builtin-types/unmanaged-types.md) nebo parametr typu, který je [omezený](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) na nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="91c68-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="91c68-105">`sizeof`Operátor vyžaduje [nezabezpečený](../keywords/unsafe.md) kontext.</span><span class="sxs-lookup"><span data-stu-id="91c68-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="91c68-106">Výrazy uvedené v následující tabulce jsou však vyhodnocovány v době kompilace do odpovídajících konstantních hodnot a nevyžadují nezabezpečený kontext:</span><span class="sxs-lookup"><span data-stu-id="91c68-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="91c68-107">Výraz</span><span class="sxs-lookup"><span data-stu-id="91c68-107">Expression</span></span>|<span data-ttu-id="91c68-108">Hodnota konstanty</span><span class="sxs-lookup"><span data-stu-id="91c68-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="91c68-109">1</span><span class="sxs-lookup"><span data-stu-id="91c68-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="91c68-110">1</span><span class="sxs-lookup"><span data-stu-id="91c68-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="91c68-111">2</span><span class="sxs-lookup"><span data-stu-id="91c68-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="91c68-112">2</span><span class="sxs-lookup"><span data-stu-id="91c68-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="91c68-113">4</span><span class="sxs-lookup"><span data-stu-id="91c68-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="91c68-114">4</span><span class="sxs-lookup"><span data-stu-id="91c68-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="91c68-115">8</span><span class="sxs-lookup"><span data-stu-id="91c68-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="91c68-116">8</span><span class="sxs-lookup"><span data-stu-id="91c68-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="91c68-117">2</span><span class="sxs-lookup"><span data-stu-id="91c68-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="91c68-118">4</span><span class="sxs-lookup"><span data-stu-id="91c68-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="91c68-119">8</span><span class="sxs-lookup"><span data-stu-id="91c68-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="91c68-120">16</span><span class="sxs-lookup"><span data-stu-id="91c68-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="91c68-121">1</span><span class="sxs-lookup"><span data-stu-id="91c68-121">1</span></span>|

<span data-ttu-id="91c68-122">Nemusíte také používat nezabezpečený kontext, pokud je operandem `sizeof` operátoru název typu [výčtu](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="91c68-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="91c68-123">Následující příklad ukazuje použití `sizeof` operátoru:</span><span class="sxs-lookup"><span data-stu-id="91c68-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](snippets/SizeOfOperator.cs)]

<span data-ttu-id="91c68-124">`sizeof`Operátor vrátí počet bajtů, které by byly přiděleny modulem CLR (Common Language Runtime) ve spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="91c68-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="91c68-125">U typů [struktury](../builtin-types/struct.md) tato hodnota zahrnuje jakékoli odsazení, jak ukazuje předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="91c68-125">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="91c68-126">Výsledek `sizeof` operátoru se může lišit od výsledku <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, která vrací velikost typu v *nespravované* paměti.</span><span class="sxs-lookup"><span data-stu-id="91c68-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="91c68-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="91c68-127">C# language specification</span></span>

<span data-ttu-id="91c68-128">Další informace naleznete v části [operátor sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="91c68-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="91c68-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="91c68-129">See also</span></span>

- [<span data-ttu-id="91c68-130">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="91c68-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="91c68-131">Operátory a výrazy v C#</span><span class="sxs-lookup"><span data-stu-id="91c68-131">C# operators and expressions</span></span>](index.md)
- [<span data-ttu-id="91c68-132">Operátory související s ukazatelem</span><span class="sxs-lookup"><span data-stu-id="91c68-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="91c68-133">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="91c68-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="91c68-134">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="91c68-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="91c68-135">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="91c68-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
