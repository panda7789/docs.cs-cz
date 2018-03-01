---
title: "Aritmetické operace na ukazatelích (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 54c439aab8b6cd34a796db8d31f9eabeefddf9f8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="75f4b-102">Aritmetické operace na ukazatelích (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="75f4b-102">Arithmetic Operations on Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="75f4b-103">Toto téma popisuje použití aritmetické operátory `+` a  **-**  k manipulaci s ukazatele.</span><span class="sxs-lookup"><span data-stu-id="75f4b-103">This topic discusses using the arithmetic operators `+` and **-** to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="75f4b-104">Nelze provést žádné aritmetické operace na ukazatelích void.</span><span class="sxs-lookup"><span data-stu-id="75f4b-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="75f4b-105">Sčítání a odečítání číselných hodnot do nebo z ukazatele</span><span class="sxs-lookup"><span data-stu-id="75f4b-105">Adding and Subtracting Numeric Values to or From Pointers</span></span>  
 <span data-ttu-id="75f4b-106">Můžete přidat hodnotu `n` typu [int](../../../csharp/language-reference/keywords/int.md), [Celé_číslo](../../../csharp/language-reference/keywords/uint.md), [dlouho](../../../csharp/language-reference/keywords/long.md), nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) na ukazatel, `p`, libovolného typu, s výjimkou `void*`.</span><span class="sxs-lookup"><span data-stu-id="75f4b-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer, `p`,of any type except `void*`.</span></span> <span data-ttu-id="75f4b-107">Výsledek `p+n` je výsledkem přidání ukazatele `n * sizeof(p) to the address of p`.</span><span class="sxs-lookup"><span data-stu-id="75f4b-107">The result `p+n` is the pointer resulting from adding `n * sizeof(p) to the address of p`.</span></span> <span data-ttu-id="75f4b-108">Podobně `p-n` je ukazatel vyplývající z odečtením `n * sizeof(p)` z adresy `p`.</span><span class="sxs-lookup"><span data-stu-id="75f4b-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(p)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="75f4b-109">Odečtení ukazatele</span><span class="sxs-lookup"><span data-stu-id="75f4b-109">Subtracting Pointers</span></span>  
 <span data-ttu-id="75f4b-110">Můžete také odečtena ukazatele stejného typu.</span><span class="sxs-lookup"><span data-stu-id="75f4b-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="75f4b-111">Výsledek je vždy typu `long`.</span><span class="sxs-lookup"><span data-stu-id="75f4b-111">The result is always of the type `long`.</span></span> <span data-ttu-id="75f4b-112">Například pokud `p1` a `p2` jsou ukazatelé typu `pointer-type*`, pak výraz `p1-p2` výsledkem:</span><span class="sxs-lookup"><span data-stu-id="75f4b-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer_type)`  
  
 <span data-ttu-id="75f4b-113">Žádné výjimky jsou generovány, pokud doména ukazatele Přetečení aritmetické operace a výsledek závisí na implementaci.</span><span class="sxs-lookup"><span data-stu-id="75f4b-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75f4b-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="75f4b-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="75f4b-115">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="75f4b-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="75f4b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="75f4b-116">See Also</span></span>  
 [<span data-ttu-id="75f4b-117">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="75f4b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="75f4b-118">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="75f4b-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="75f4b-119">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="75f4b-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="75f4b-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="75f4b-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="75f4b-121">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="75f4b-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)  
 [<span data-ttu-id="75f4b-122">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="75f4b-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="75f4b-123">Typy</span><span class="sxs-lookup"><span data-stu-id="75f4b-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="75f4b-124">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="75f4b-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="75f4b-125">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="75f4b-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="75f4b-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="75f4b-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
