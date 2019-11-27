---
title: Nespravované typy C# – referenční informace
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 81eef59ceb20bcae6c749dd59578ce35da253826
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204475"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="90375-102">Nespravované typyC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="90375-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="90375-103">Typ je **nespravovaný typ** , pokud se jedná o některý z následujících typů:</span><span class="sxs-lookup"><span data-stu-id="90375-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="90375-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`nebo `bool`</span><span class="sxs-lookup"><span data-stu-id="90375-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="90375-105">Libovolný typ [výčtu](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="90375-105">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="90375-106">Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="90375-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="90375-107">Libovolný uživatelsky definovaný typ [struktury](../keywords/struct.md) , který obsahuje pole nespravovaných typů a v C# 7,3 a starších verzích není konstruovaný typ (typ, který obsahuje alespoň jeden argument typu).</span><span class="sxs-lookup"><span data-stu-id="90375-107">Any user-defined [struct](../keywords/struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="90375-108">Počínaje C# 7,3 můžete použít [omezení`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) k určení toho, že parametr typu není ukazatel nespravovaného typu, který neumožňuje hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="90375-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="90375-109">Počínaje C# 8,0, *konstruovaný* typ struktury obsahující pole pouze nespravovaných typů je také nespravovaný, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="90375-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="90375-110">Obecná struktura může být zdrojem nespravovaných i nespravovaných konstruovaných typů.</span><span class="sxs-lookup"><span data-stu-id="90375-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="90375-111">Předchozí příklad definuje obecnou strukturu `Coords<T>` a prezentuje příklady nespravovaných konstruovaných typů.</span><span class="sxs-lookup"><span data-stu-id="90375-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="90375-112">Příkladem nespravovaného typu je `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="90375-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="90375-113">Není nespravovaný, protože obsahuje pole `object` typu, který není nespravovaný.</span><span class="sxs-lookup"><span data-stu-id="90375-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="90375-114">Pokud chcete, aby *všechny* vytvořené typy byly nespravované typy, použijte omezení `unmanaged` v definici obecné struktury:</span><span class="sxs-lookup"><span data-stu-id="90375-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="90375-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="90375-115">C# language specification</span></span>

<span data-ttu-id="90375-116">Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="90375-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="90375-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="90375-117">See also</span></span>

- [<span data-ttu-id="90375-118">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="90375-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="90375-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="90375-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="90375-120">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="90375-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="90375-121">sizeof – operátor</span><span class="sxs-lookup"><span data-stu-id="90375-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="90375-122">stackalloc – operátor</span><span class="sxs-lookup"><span data-stu-id="90375-122">stackalloc operator</span></span>](../operators/stackalloc.md)
