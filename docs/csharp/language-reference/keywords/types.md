---
title: Typy – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
ms.openlocfilehash: 41406e74a207f289968017f1f9869b23b165c34b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660460"
---
# <a name="types-c-reference"></a><span data-ttu-id="66d16-102">Typy (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="66d16-102">Types (C# Reference)</span></span>

<span data-ttu-id="66d16-103">Zadáním systému C# obsahuje následující kategorie:</span><span class="sxs-lookup"><span data-stu-id="66d16-103">The C# typing system contains the following categories:</span></span>

- [<span data-ttu-id="66d16-104">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="66d16-104">Value types</span></span>](value-types.md)

- [<span data-ttu-id="66d16-105">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="66d16-105">Reference types</span></span>](reference-types.md)

- [<span data-ttu-id="66d16-106">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="66d16-106">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)

 <span data-ttu-id="66d16-107">Proměnné, které jsou typy hodnot ukládání dat, a ty, které jsou odkazové typy ukládání odkazů na skutečná data.</span><span class="sxs-lookup"><span data-stu-id="66d16-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="66d16-108">Instance typy odkazů jsou také označovány jako objekty.</span><span class="sxs-lookup"><span data-stu-id="66d16-108">Instances of reference types are also referred to as objects.</span></span> <span data-ttu-id="66d16-109">Typy ukazatelů lze použít pouze ve [nebezpečné](unsafe.md) režimu.</span><span class="sxs-lookup"><span data-stu-id="66d16-109">Pointer types can be used only in [unsafe](unsafe.md) mode.</span></span>

 <span data-ttu-id="66d16-110">Je možné převést typ hodnoty na odkazový typ a zpět na typ hodnoty, s použitím [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="66d16-110">It's possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="66d16-111">S výjimkou zabalený typ hodnoty nelze převést typ odkazu na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="66d16-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>

 <span data-ttu-id="66d16-112">Tato část také zavádí [void](void.md).</span><span class="sxs-lookup"><span data-stu-id="66d16-112">This section also introduces [void](void.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="66d16-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="66d16-113">See also</span></span>

- [<span data-ttu-id="66d16-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="66d16-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="66d16-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="66d16-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="66d16-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="66d16-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="66d16-117">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="66d16-117">Reference Tables for Types</span></span>](reference-tables-for-types.md)
- [<span data-ttu-id="66d16-118">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="66d16-118">Casting and Type Conversions</span></span>](../../programming-guide/types/casting-and-type-conversions.md)
- [<span data-ttu-id="66d16-119">Typy</span><span class="sxs-lookup"><span data-stu-id="66d16-119">Types</span></span>](../../programming-guide/types/index.md)
