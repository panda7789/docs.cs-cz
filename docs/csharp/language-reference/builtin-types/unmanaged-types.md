---
title: Nespravované typy – odkaz jazyka C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 9dd2ab4e044b8a86bfe72a6fcf2481b8e1e80bf4
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507227"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="9e7c4-102">Nespravované typy (odkaz Jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9e7c4-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="9e7c4-103">Typ je **nespravovaný typ,** pokud se jedná o některý z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="9e7c4-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="9e7c4-104">`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `char`, `float` `double`, `decimal`, , , , , , nebo`bool`</span><span class="sxs-lookup"><span data-stu-id="9e7c4-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="9e7c4-105">Libovolný typ [výčtu](enum.md)</span><span class="sxs-lookup"><span data-stu-id="9e7c4-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="9e7c4-106">Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="9e7c4-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="9e7c4-107">Jakýkoli uživatelem definovaný typ [struktury,](struct.md) který obsahuje pouze pole nespravovaných typů a v c# 7.3 a starších není konstruovaným typem (typ, který obsahuje alespoň jeden argument typu)</span><span class="sxs-lookup"><span data-stu-id="9e7c4-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="9e7c4-108">Počínaje C# 7.3, můžete použít [ `unmanaged` omezení](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) k určení, že parametr typu je neukazatel, nenulelný nespravovaný typ.</span><span class="sxs-lookup"><span data-stu-id="9e7c4-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="9e7c4-109">Počínaje C# 8.0, *konstruované* struct typ, který obsahuje pouze pole nespravovaných typů je také nespravované, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="9e7c4-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="9e7c4-110">Obecná struktura může být zdrojem nespravovaných i nespravovaných konstrukčních typů.</span><span class="sxs-lookup"><span data-stu-id="9e7c4-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="9e7c4-111">Předchozí příklad definuje obecnou strukturu `Coords<T>` a představuje příklady nespravovaných konstruovaných typů.</span><span class="sxs-lookup"><span data-stu-id="9e7c4-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="9e7c4-112">Příkladem nespravovaného typu je `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="9e7c4-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="9e7c4-113">Není nespravované, protože má pole `object` typu, který není nespravované.</span><span class="sxs-lookup"><span data-stu-id="9e7c4-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="9e7c4-114">Pokud *chcete,* aby všechny konstruované typy byly `unmanaged` nespravované typy, použijte omezení v definici obecné struktury:</span><span class="sxs-lookup"><span data-stu-id="9e7c4-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="9e7c4-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9e7c4-115">C# language specification</span></span>

<span data-ttu-id="9e7c4-116">Další informace naleznete v části [Typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="9e7c4-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="9e7c4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e7c4-117">See also</span></span>

- [<span data-ttu-id="9e7c4-118">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="9e7c4-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="9e7c4-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="9e7c4-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="9e7c4-120">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="9e7c4-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="9e7c4-121">sizeof – operátor</span><span class="sxs-lookup"><span data-stu-id="9e7c4-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="9e7c4-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="9e7c4-122">stackalloc</span></span>](../operators/stackalloc.md)
