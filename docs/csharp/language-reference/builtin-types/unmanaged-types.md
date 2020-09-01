---
description: 'Další informace o nespravovaných typech v jazyce C #'
title: Nespravované typy – reference jazyka C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: b5a689ca3ade36ef77da958549894f76e074986e
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89143529"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="cf892-103">Nespravované typy (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cf892-103">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="cf892-104">Typ je **nespravovaný typ** , pokud se jedná o některý z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="cf892-104">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="cf892-105">`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `char` , `float` , `double` , `decimal` nebo `bool`</span><span class="sxs-lookup"><span data-stu-id="cf892-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="cf892-106">Libovolný typ [výčtu](enum.md)</span><span class="sxs-lookup"><span data-stu-id="cf892-106">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="cf892-107">Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="cf892-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="cf892-108">Libovolný uživatelsky definovaný typ [struktury](struct.md) , který obsahuje pouze pole nespravovaných typů a v jazyce C# 7,3 a starší není konstruovaný typ (typ, který obsahuje alespoň jeden argument typu).</span><span class="sxs-lookup"><span data-stu-id="cf892-108">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="cf892-109">Počínaje jazykem C# 7,3 můžete použít [ `unmanaged` omezení](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) , chcete-li určit, že parametr typu je nespravovaný typ bez hodnoty null.</span><span class="sxs-lookup"><span data-stu-id="cf892-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="cf892-110">Počínaje jazykem C# 8,0 je typ *konstruované* struktury obsahující pole pouze nespravovaných typů také nespravovaný, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="cf892-110">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="cf892-111">Obecná struktura může být zdrojem nespravovaných i nespravovaných konstruovaných typů.</span><span class="sxs-lookup"><span data-stu-id="cf892-111">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="cf892-112">Předchozí příklad definuje obecnou strukturu `Coords<T>` a prezentuje příklady nespravovaných konstruovaných typů.</span><span class="sxs-lookup"><span data-stu-id="cf892-112">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="cf892-113">Příkladem nespravovaného typu je `Coords<object>` .</span><span class="sxs-lookup"><span data-stu-id="cf892-113">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="cf892-114">Není nespravované, protože má pole `object` typu, která nejsou nespravována.</span><span class="sxs-lookup"><span data-stu-id="cf892-114">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="cf892-115">Pokud chcete, aby *všechny* vytvořené typy byly nespravované typy, použijte `unmanaged` omezení v definici obecné struktury:</span><span class="sxs-lookup"><span data-stu-id="cf892-115">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="cf892-116">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cf892-116">C# language specification</span></span>

<span data-ttu-id="cf892-117">Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="cf892-117">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="cf892-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf892-118">See also</span></span>

- [<span data-ttu-id="cf892-119">Referenční dokumentace k jazyku C#</span><span class="sxs-lookup"><span data-stu-id="cf892-119">C# reference</span></span>](../index.md)
- [<span data-ttu-id="cf892-120">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="cf892-120">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="cf892-121">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="cf892-121">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="cf892-122">sizeof – operátor</span><span class="sxs-lookup"><span data-stu-id="cf892-122">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="cf892-123">stackalloc</span><span class="sxs-lookup"><span data-stu-id="cf892-123">stackalloc</span></span>](../operators/stackalloc.md)
