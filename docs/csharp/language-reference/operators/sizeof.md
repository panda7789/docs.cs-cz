---
title: sizeof operátor - c# odkaz
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: a9e80ecb3288479a2ca81b43c9d088809ed5f2f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847284"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="7da1c-102">sizeof operátor (odkaz C# )</span><span class="sxs-lookup"><span data-stu-id="7da1c-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="7da1c-103">Operátor `sizeof` vrátí počet bajtů obsazených proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="7da1c-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="7da1c-104">Argument emitovaný `sizeof` operátorem musí být název [nespravovaného typu](../builtin-types/unmanaged-types.md) nebo parametr typu, který je [omezen](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) na nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="7da1c-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="7da1c-105">Operátor `sizeof` vyžaduje [nebezpečný](../keywords/unsafe.md) kontext.</span><span class="sxs-lookup"><span data-stu-id="7da1c-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="7da1c-106">Výrazy uvedené v následující tabulce jsou však vyhodnocovány v době kompilace na odpovídající konstantní hodnoty a nevyžadují nebezpečný kontext:</span><span class="sxs-lookup"><span data-stu-id="7da1c-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="7da1c-107">Expression</span><span class="sxs-lookup"><span data-stu-id="7da1c-107">Expression</span></span>|<span data-ttu-id="7da1c-108">Konstantní hodnota</span><span class="sxs-lookup"><span data-stu-id="7da1c-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="7da1c-109">1</span><span class="sxs-lookup"><span data-stu-id="7da1c-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="7da1c-110">1</span><span class="sxs-lookup"><span data-stu-id="7da1c-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="7da1c-111">2</span><span class="sxs-lookup"><span data-stu-id="7da1c-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="7da1c-112">2</span><span class="sxs-lookup"><span data-stu-id="7da1c-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="7da1c-113">4</span><span class="sxs-lookup"><span data-stu-id="7da1c-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="7da1c-114">4</span><span class="sxs-lookup"><span data-stu-id="7da1c-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="7da1c-115">8</span><span class="sxs-lookup"><span data-stu-id="7da1c-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="7da1c-116">8</span><span class="sxs-lookup"><span data-stu-id="7da1c-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="7da1c-117">2</span><span class="sxs-lookup"><span data-stu-id="7da1c-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="7da1c-118">4</span><span class="sxs-lookup"><span data-stu-id="7da1c-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="7da1c-119">8</span><span class="sxs-lookup"><span data-stu-id="7da1c-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="7da1c-120">16</span><span class="sxs-lookup"><span data-stu-id="7da1c-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="7da1c-121">1</span><span class="sxs-lookup"><span data-stu-id="7da1c-121">1</span></span>|

<span data-ttu-id="7da1c-122">Také není nutné použít nebezpečný kontext, pokud operand `sizeof` operátoru je název typu [výčtu.](../builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="7da1c-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="7da1c-123">Následující příklad ukazuje použití operátoru: `sizeof`</span><span class="sxs-lookup"><span data-stu-id="7da1c-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](snippets/SizeOfOperator.cs)]

<span data-ttu-id="7da1c-124">Operátor `sizeof` vrátí počet bajtů, které by byly přiděleny za běhu společného jazyka ve spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="7da1c-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="7da1c-125">Pro [typy struktury](../builtin-types/struct.md) tato hodnota zahrnuje všechny odsazení, jak ukazuje předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="7da1c-125">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="7da1c-126">Výsledek operátoru `sizeof` se může lišit od <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> výsledku metody, která vrací velikost typu v *nespravované* paměti.</span><span class="sxs-lookup"><span data-stu-id="7da1c-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="7da1c-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7da1c-127">C# language specification</span></span>

<span data-ttu-id="7da1c-128">Další informace naleznete v části [sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="7da1c-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7da1c-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="7da1c-129">See also</span></span>

- [<span data-ttu-id="7da1c-130">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="7da1c-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="7da1c-131">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="7da1c-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="7da1c-132">Operátory související s ukazatelem</span><span class="sxs-lookup"><span data-stu-id="7da1c-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="7da1c-133">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="7da1c-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="7da1c-134">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="7da1c-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="7da1c-135">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="7da1c-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
