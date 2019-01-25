---
title: Aritmetické operace na ukazatelích - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], arithmetic operations
ms.assetid: d4f0b623-827e-45ce-8649-cfcebc8692aa
ms.openlocfilehash: b0b75a6aa47cfc169157b229c4386ed7dc1e627b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54710193"
---
# <a name="arithmetic-operations-on-pointers-c-programming-guide"></a><span data-ttu-id="1a53a-102">Aritmetické operace na ukazatelích (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="1a53a-102">Arithmetic operations on pointers (C# Programming Guide)</span></span>
<span data-ttu-id="1a53a-103">Toto téma popisuje použití aritmetické operátory `+` a `-` manipulace s ukazateli.</span><span class="sxs-lookup"><span data-stu-id="1a53a-103">This topic discusses using the arithmetic operators `+` and `-` to manipulate pointers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a53a-104">Nelze provést všechny aritmetické operace u ukazatelů typu void.</span><span class="sxs-lookup"><span data-stu-id="1a53a-104">You cannot perform any arithmetic operations on void pointers.</span></span>  
  
## <a name="adding-and-subtracting-numeric-values-to-or-from-pointers"></a><span data-ttu-id="1a53a-105">Přičítání a odečítání číselné hodnoty do nebo z ukazatele</span><span class="sxs-lookup"><span data-stu-id="1a53a-105">Adding and subtracting numeric values to or from pointers</span></span>  
 <span data-ttu-id="1a53a-106">Můžete přidat hodnotu `n` typu [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [dlouhé](../../../csharp/language-reference/keywords/long.md), nebo [ulong](../../../csharp/language-reference/keywords/ulong.md) na ukazatel.</span><span class="sxs-lookup"><span data-stu-id="1a53a-106">You can add a value `n` of type [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [long](../../../csharp/language-reference/keywords/long.md), or [ulong](../../../csharp/language-reference/keywords/ulong.md) to a pointer.</span></span> <span data-ttu-id="1a53a-107">Pokud `p` je ukazatel typu `pointer-type*`, výsledek `p+n` je ukazatel výsledkem přidání `n * sizeof(pointer-type)` na adresu `p`.</span><span class="sxs-lookup"><span data-stu-id="1a53a-107">If `p` is a pointer of the type `pointer-type*`, the result `p+n` is the pointer resulting from adding `n * sizeof(pointer-type)` to the address of `p`.</span></span> <span data-ttu-id="1a53a-108">Obdobně `p-n` je ukazatel výsledkem odečtením `n * sizeof(pointer-type)` z adresy `p`.</span><span class="sxs-lookup"><span data-stu-id="1a53a-108">Similarly, `p-n` is the pointer resulting from subtracting `n * sizeof(pointer-type)` from the address of `p`.</span></span>  
  
## <a name="subtracting-pointers"></a><span data-ttu-id="1a53a-109">Odečtení ukazatele</span><span class="sxs-lookup"><span data-stu-id="1a53a-109">Subtracting pointers</span></span>  
 <span data-ttu-id="1a53a-110">Můžete rovněž odečíst ukazateli stejného typu.</span><span class="sxs-lookup"><span data-stu-id="1a53a-110">You can also subtract pointers of the same type.</span></span> <span data-ttu-id="1a53a-111">Výsledek je vždy typu `long`.</span><span class="sxs-lookup"><span data-stu-id="1a53a-111">The result is always of the type `long`.</span></span> <span data-ttu-id="1a53a-112">Například pokud `p1` a `p2` jsou ukazatele typ `pointer-type*`, pak výraz `p1-p2` výsledkem:</span><span class="sxs-lookup"><span data-stu-id="1a53a-112">For example, if `p1` and `p2` are pointers of the type `pointer-type*`, then the expression `p1-p2` results in:</span></span>  
  
 `((long)p1 - (long)p2)/sizeof(pointer-type)`  
  
 <span data-ttu-id="1a53a-113">Při přetečení aritmetické operace domény ukazatele a výsledek závisí na implementaci, nejsou generovány žádné výjimky.</span><span class="sxs-lookup"><span data-stu-id="1a53a-113">No exceptions are generated when the arithmetic operation overflows the domain of the pointer, and the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1a53a-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="1a53a-114">Example</span></span>  
 [!code-csharp[csProgGuidePointers#14](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#15](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/arithmetic-operations-on-pointers_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1a53a-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a53a-115">C# language specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1a53a-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a53a-116">See also</span></span>

- [<span data-ttu-id="1a53a-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1a53a-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="1a53a-118">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="1a53a-118">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="1a53a-119">Výrazy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="1a53a-119">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="1a53a-120">Operátory jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1a53a-120">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
- [<span data-ttu-id="1a53a-121">Manipulace s ukazateli</span><span class="sxs-lookup"><span data-stu-id="1a53a-121">Manipulating Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/manipulating-pointers.md)
- [<span data-ttu-id="1a53a-122">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="1a53a-122">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="1a53a-123">Typy</span><span class="sxs-lookup"><span data-stu-id="1a53a-123">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="1a53a-124">unsafe</span><span class="sxs-lookup"><span data-stu-id="1a53a-124">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="1a53a-125">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="1a53a-125">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="1a53a-126">stackalloc</span><span class="sxs-lookup"><span data-stu-id="1a53a-126">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
