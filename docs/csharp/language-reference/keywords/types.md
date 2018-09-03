---
title: Typy (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- types [C#]
- data types [C#], type system
ms.assetid: 16b984df-f417-4e02-b1e6-4589d4a614ea
ms.openlocfilehash: c5c29f5d9a1a4e25e2d5f8816a0df31fa9a91fb1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43463309"
---
# <a name="types-c-reference"></a><span data-ttu-id="e65c6-102">Typy (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="e65c6-102">Types (C# Reference)</span></span>
<span data-ttu-id="e65c6-103">Zadáním systému C# obsahuje následující kategorie:</span><span class="sxs-lookup"><span data-stu-id="e65c6-103">The C# typing system contains the following categories:</span></span>  
  
-   [<span data-ttu-id="e65c6-104">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="e65c6-104">Value types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
  
-   [<span data-ttu-id="e65c6-105">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="e65c6-105">Reference types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
  
-   [<span data-ttu-id="e65c6-106">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="e65c6-106">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
 <span data-ttu-id="e65c6-107">Proměnné, které jsou typy hodnot ukládání dat, a ty, které jsou odkazové typy ukládání odkazů na skutečná data.</span><span class="sxs-lookup"><span data-stu-id="e65c6-107">Variables that are value types store data, and those that are reference types store references to the actual data.</span></span> <span data-ttu-id="e65c6-108">Typy odkazů jsou také označovány jako objekty.</span><span class="sxs-lookup"><span data-stu-id="e65c6-108">Reference types are also referred to as objects.</span></span> <span data-ttu-id="e65c6-109">Typy ukazatelů lze použít pouze ve [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) režimu.</span><span class="sxs-lookup"><span data-stu-id="e65c6-109">Pointer types can be used only in [unsafe](../../../csharp/language-reference/keywords/unsafe.md) mode.</span></span>  
  
 <span data-ttu-id="e65c6-110">Je možné převést typ hodnoty na odkazový typ a zpět na typ hodnoty, s použitím [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="e65c6-110">It is possible to convert a value type to a reference type, and back again to a value type, by using [boxing and unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span> <span data-ttu-id="e65c6-111">S výjimkou zabalený typ hodnoty nelze převést typ odkazu na typ hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e65c6-111">With the exception of a boxed value type, you cannot convert a reference type to a value type.</span></span>  
  
 <span data-ttu-id="e65c6-112">Tato část také zavádí [void](../../../csharp/language-reference/keywords/void.md).</span><span class="sxs-lookup"><span data-stu-id="e65c6-112">This section also introduces [void](../../../csharp/language-reference/keywords/void.md).</span></span>  
  
 <span data-ttu-id="e65c6-113">Typy hodnot jsou také s možnou hodnotou Null, což znamená, že jsou v nich uložené další stav bez hodnoty.</span><span class="sxs-lookup"><span data-stu-id="e65c6-113">Value types are also nullable, which means they can store an additional non-value state.</span></span> <span data-ttu-id="e65c6-114">Další informace najdete v tématu [typy připouštějící hodnotu Null](../../../csharp/programming-guide/nullable-types/index.md).</span><span class="sxs-lookup"><span data-stu-id="e65c6-114">For more information, see [Nullable Types](../../../csharp/programming-guide/nullable-types/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e65c6-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e65c6-115">See Also</span></span>

- [<span data-ttu-id="e65c6-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e65c6-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="e65c6-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="e65c6-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="e65c6-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="e65c6-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="e65c6-119">Referenční tabulky pro typy</span><span class="sxs-lookup"><span data-stu-id="e65c6-119">Reference Tables for Types</span></span>](../../../csharp/language-reference/keywords/reference-tables-for-types.md)  
- [<span data-ttu-id="e65c6-120">Přetypování a převody typů</span><span class="sxs-lookup"><span data-stu-id="e65c6-120">Casting and Type Conversions</span></span>](../../../csharp/programming-guide/types/casting-and-type-conversions.md)  
- [<span data-ttu-id="e65c6-121">Typy</span><span class="sxs-lookup"><span data-stu-id="e65c6-121">Types</span></span>](../../../csharp/programming-guide/types/index.md)
