---
title: sizeof – C# operátor odkazu
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: c88f205a616587e5437bf4fc81bcbdcbbc19a9ac
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712634"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="324b4-102">sizeof – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="324b4-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="324b4-103">Operátor `sizeof` vrátí počet bajtů obsazených proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="324b4-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="324b4-104">Argument operátoru `sizeof` musí být název [nespravovaného typu](../builtin-types/unmanaged-types.md) nebo parametr typu, který je [omezený](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) na nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="324b4-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="324b4-105">Operátor `sizeof` vyžaduje [nezabezpečený](../keywords/unsafe.md) kontext.</span><span class="sxs-lookup"><span data-stu-id="324b4-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="324b4-106">Výrazy uvedené v následující tabulce jsou však vyhodnocovány v době kompilace do odpovídajících konstantních hodnot a nevyžadují nezabezpečený kontext:</span><span class="sxs-lookup"><span data-stu-id="324b4-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="324b4-107">Výraz</span><span class="sxs-lookup"><span data-stu-id="324b4-107">Expression</span></span>|<span data-ttu-id="324b4-108">Hodnota konstanty</span><span class="sxs-lookup"><span data-stu-id="324b4-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="324b4-109">1</span><span class="sxs-lookup"><span data-stu-id="324b4-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="324b4-110">1</span><span class="sxs-lookup"><span data-stu-id="324b4-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="324b4-111">2</span><span class="sxs-lookup"><span data-stu-id="324b4-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="324b4-112">2</span><span class="sxs-lookup"><span data-stu-id="324b4-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="324b4-113">4</span><span class="sxs-lookup"><span data-stu-id="324b4-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="324b4-114">4</span><span class="sxs-lookup"><span data-stu-id="324b4-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="324b4-115">8</span><span class="sxs-lookup"><span data-stu-id="324b4-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="324b4-116">8</span><span class="sxs-lookup"><span data-stu-id="324b4-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="324b4-117">2</span><span class="sxs-lookup"><span data-stu-id="324b4-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="324b4-118">4</span><span class="sxs-lookup"><span data-stu-id="324b4-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="324b4-119">8</span><span class="sxs-lookup"><span data-stu-id="324b4-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="324b4-120">16</span><span class="sxs-lookup"><span data-stu-id="324b4-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="324b4-121">1</span><span class="sxs-lookup"><span data-stu-id="324b4-121">1</span></span>|

<span data-ttu-id="324b4-122">Nemusíte také používat nezabezpečený kontext, pokud je Operand operátoru `sizeof` název typu [výčtu](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="324b4-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="324b4-123">Následující příklad ukazuje použití operátoru `sizeof`:</span><span class="sxs-lookup"><span data-stu-id="324b4-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="324b4-124">Operátor `sizeof` vrací počet bajtů, které by byly přiděleny modulem CLR (Common Language Runtime) ve spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="324b4-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="324b4-125">U typů [struktury](../keywords/struct.md) tato hodnota zahrnuje jakékoli odsazení, jak ukazuje předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="324b4-125">For [struct](../keywords/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="324b4-126">Výsledek operátoru `sizeof` se může lišit od výsledku metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, která vrací velikost typu v *nespravované* paměti.</span><span class="sxs-lookup"><span data-stu-id="324b4-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="324b4-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="324b4-127">C# language specification</span></span>

<span data-ttu-id="324b4-128">Další informace naleznete v části [operátor sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="324b4-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="324b4-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="324b4-129">See also</span></span>

- [<span data-ttu-id="324b4-130">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="324b4-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="324b4-131">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="324b4-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="324b4-132">Operátory související s ukazateli</span><span class="sxs-lookup"><span data-stu-id="324b4-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="324b4-133">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="324b4-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="324b4-134">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="324b4-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="324b4-135">Obecné typy v .NET</span><span class="sxs-lookup"><span data-stu-id="324b4-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
