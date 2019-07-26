---
title: Nespravované typy C# – referenční informace
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512079"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="f4b93-102">Nespravované typyC# (Referenční dokumentace)</span><span class="sxs-lookup"><span data-stu-id="f4b93-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="f4b93-103">**Nespravovaný typ** je jakýkoli typ, který není odkazovým typem nebo vytvořeným typem (typ, který obsahuje alespoň jeden argument typu) a neobsahuje typ odkazu ani vytvořená pole typu na jakékoli úrovni vnoření.</span><span class="sxs-lookup"><span data-stu-id="f4b93-103">An **unmanaged type** is any type that isn't a reference type or constructed type (a type that includes at least one type argument), and doesn't contain reference type or constructed type fields at any level of nesting.</span></span> <span data-ttu-id="f4b93-104">Jinými slovy, nespravovaný typ je jedna z následujících:</span><span class="sxs-lookup"><span data-stu-id="f4b93-104">In other words, an unmanaged type is one of the following:</span></span>

- <span data-ttu-id="f4b93-105">`sbyte`, `byte` ,`short`, ,`int`, ,`long`,,,, ,`double`nebo `uint` `ulong` `char` `float` `ushort` `decimal``bool`</span><span class="sxs-lookup"><span data-stu-id="f4b93-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="f4b93-106">Libovolný typ [výčtu](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="f4b93-106">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="f4b93-107">Libovolný typ [ukazatele](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="f4b93-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="f4b93-108">Libovolný uživatelsky definovaný typ [struktury](../keywords/struct.md) , který není konstruovaným typem a obsahuje pole pouze nespravovaných typů.</span><span class="sxs-lookup"><span data-stu-id="f4b93-108">Any user-defined [struct](../keywords/struct.md) type that is not a constructed type and contains fields of unmanaged types only</span></span>

<span data-ttu-id="f4b93-109">Počínaje C# 7,3 můžete [ `unmanaged` omezení](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) použít k určení toho, že parametr typu je nespravovaný typ bez ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f4b93-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f4b93-110">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f4b93-110">C# language specification</span></span>

<span data-ttu-id="f4b93-111">Další informace naleznete v části [typy ukazatelů](~/_csharplang/spec/unsafe-code.md#pointer-types) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="f4b93-111">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f4b93-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f4b93-112">See also</span></span>

- [<span data-ttu-id="f4b93-113">C#odkaz</span><span class="sxs-lookup"><span data-stu-id="f4b93-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="f4b93-114">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="f4b93-114">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="f4b93-115">Typy související s Memory a Span</span><span class="sxs-lookup"><span data-stu-id="f4b93-115">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="f4b93-116">sizeof – operátor</span><span class="sxs-lookup"><span data-stu-id="f4b93-116">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="f4b93-117">stackalloc – operátor</span><span class="sxs-lookup"><span data-stu-id="f4b93-117">stackalloc operator</span></span>](../operators/stackalloc.md)
