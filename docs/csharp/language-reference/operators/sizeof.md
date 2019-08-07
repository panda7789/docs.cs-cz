---
title: sizeof – C# operátor odkazu
ms.custom: seodec18
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: c455804923f4d0e7cc8f556bb9b9df34b6332d82
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796526"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="46016-102">sizeof – operátorC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="46016-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="46016-103">`sizeof` Operátor vrátí počet bajtů obsazených proměnnou daného typu.</span><span class="sxs-lookup"><span data-stu-id="46016-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="46016-104">Argument `sizeof` operátoru musí být název nespravovaného [typu](../builtin-types/unmanaged-types.md) nebo parametr typu, který je [omezený](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) na nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="46016-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="46016-105">Operátor vyžaduje nezabezpečený kontext. [](../keywords/unsafe.md) `sizeof`</span><span class="sxs-lookup"><span data-stu-id="46016-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="46016-106">Výrazy uvedené v následující tabulce jsou však vyhodnocovány v době kompilace do odpovídajících konstantních hodnot a nevyžadují nezabezpečený kontext:</span><span class="sxs-lookup"><span data-stu-id="46016-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="46016-107">Výraz</span><span class="sxs-lookup"><span data-stu-id="46016-107">Expression</span></span>|<span data-ttu-id="46016-108">Hodnota konstanty</span><span class="sxs-lookup"><span data-stu-id="46016-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="46016-109">1</span><span class="sxs-lookup"><span data-stu-id="46016-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="46016-110">1</span><span class="sxs-lookup"><span data-stu-id="46016-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="46016-111">2</span><span class="sxs-lookup"><span data-stu-id="46016-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="46016-112">2</span><span class="sxs-lookup"><span data-stu-id="46016-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="46016-113">4</span><span class="sxs-lookup"><span data-stu-id="46016-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="46016-114">4</span><span class="sxs-lookup"><span data-stu-id="46016-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="46016-115">8</span><span class="sxs-lookup"><span data-stu-id="46016-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="46016-116">8</span><span class="sxs-lookup"><span data-stu-id="46016-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="46016-117">2</span><span class="sxs-lookup"><span data-stu-id="46016-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="46016-118">4</span><span class="sxs-lookup"><span data-stu-id="46016-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="46016-119">8</span><span class="sxs-lookup"><span data-stu-id="46016-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="46016-120">16</span><span class="sxs-lookup"><span data-stu-id="46016-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="46016-121">1</span><span class="sxs-lookup"><span data-stu-id="46016-121">1</span></span>|

<span data-ttu-id="46016-122">Nemusíte také používat nezabezpečený kontext, pokud je operandem `sizeof` operátoru název typu [výčtu](../keywords/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="46016-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="46016-123">Následující příklad ukazuje použití `sizeof` operátoru:</span><span class="sxs-lookup"><span data-stu-id="46016-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="46016-124">`sizeof` Operátor vrátí počet bajtů, které by byly přiděleny modulem CLR (Common Language Runtime) ve spravované paměti.</span><span class="sxs-lookup"><span data-stu-id="46016-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="46016-125">U typů [struktury](../keywords/struct.md) tato hodnota zahrnuje jakékoli odsazení, jak ukazuje předchozí příklad.</span><span class="sxs-lookup"><span data-stu-id="46016-125">For [struct](../keywords/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="46016-126">Výsledek `sizeof` operátoru se může lišit od výsledku <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, která vrací velikost typu v nespravované paměti.</span><span class="sxs-lookup"><span data-stu-id="46016-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="46016-127">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="46016-127">C# language specification</span></span>

<span data-ttu-id="46016-128">Další informace naleznete v části [operátor sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="46016-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46016-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46016-129">See also</span></span>

- [<span data-ttu-id="46016-130">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="46016-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="46016-131">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="46016-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="46016-132">Operátory související s ukazateli</span><span class="sxs-lookup"><span data-stu-id="46016-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="46016-133">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="46016-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="46016-134">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="46016-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
