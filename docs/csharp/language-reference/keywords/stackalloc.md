---
title: stackalloc (Referenční dokumentace jazyka C#)
ms.date: 04/12/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c4cde254bb6a5601d10619c4a3bd2f00f1f146d3
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2018
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="fd338-102">stackalloc (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fd338-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="fd338-103">`stackalloc` – Klíčové slovo se používá v kontextu nezabezpečený kód přidělit blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="fd338-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="fd338-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fd338-104">Remarks</span></span>

<span data-ttu-id="fd338-105">Klíčové slovo je platný jenom v místní proměnné inicializátory.</span><span class="sxs-lookup"><span data-stu-id="fd338-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="fd338-106">Následující kód způsobí, že chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="fd338-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="fd338-107">Počínaje 7.3 C#, můžete pomocí syntaxe inicializátoru pole pro `stackalloc` pole.</span><span class="sxs-lookup"><span data-stu-id="fd338-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="fd338-108">Všechny následující deklarace deklarovat pole s tři elementy, jejichž hodnoty jsou celá čísla `1`, `2`, a `3`:</span><span class="sxs-lookup"><span data-stu-id="fd338-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="fd338-109">Protože se jedná o typy ukazatelů `stackalloc` vyžaduje [unsafe](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="fd338-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="fd338-110">Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)</span><span class="sxs-lookup"><span data-stu-id="fd338-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md)</span></span> 

<span data-ttu-id="fd338-111">`stackalloc` je třeba [_alloca –](/cpp/c-runtime-library/reference/alloca) v běhové knihovny jazyka C.</span><span class="sxs-lookup"><span data-stu-id="fd338-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="fd338-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="fd338-112">Examples</span></span>

<span data-ttu-id="fd338-113">Následující příklad vypočítá a zobrazuje prvních 20 čísla v pořadí Fibonacciho.</span><span class="sxs-lookup"><span data-stu-id="fd338-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="fd338-114">Všechna čísla je součet hodnot předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="fd338-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="fd338-115">V kódu bloku paměti dostatečná velikost tak, aby obsahovala 20 elementy typu `int` je přidělená v zásobníku, není haldě.</span><span class="sxs-lookup"><span data-stu-id="fd338-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="fd338-116">Adresu bloku je uložen v ukazatele `fib`.</span><span class="sxs-lookup"><span data-stu-id="fd338-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="fd338-117">Tuto paměť nevztahují uvolňování paměti a proto nemusí být připnutý (pomocí [pevné](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="fd338-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="fd338-118">Životnost bloku paměti je omezeno na dobu životnosti metody, která ho definuje.</span><span class="sxs-lookup"><span data-stu-id="fd338-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="fd338-119">Nelze uvolnit paměť, než metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="fd338-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="fd338-120">Tento příklad inicializuje `stackalloc` pole celých čísel na bitová maska s jeden bit nastavit v jednotlivých prvků.</span><span class="sxs-lookup"><span data-stu-id="fd338-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="fd338-121">Tento příklad ukazuje nové syntaxe inicializátoru, která je k dispozici od 7.3 C#:</span><span class="sxs-lookup"><span data-stu-id="fd338-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="fd338-122">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="fd338-122">Security</span></span>

<span data-ttu-id="fd338-123">Nezabezpečený kód je méně bezpečné než bezpečné alternativy.</span><span class="sxs-lookup"><span data-stu-id="fd338-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="fd338-124">Ale použití `stackalloc` automaticky povolí funkce zjišťování přetečení vyrovnávací paměti v common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="fd338-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="fd338-125">Pokud je zjištěn přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat riziko, že se spustí škodlivý kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="fd338-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="fd338-126">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fd338-126">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="fd338-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="fd338-127">See Also</span></span>
 [<span data-ttu-id="fd338-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fd338-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="fd338-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fd338-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="fd338-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fd338-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="fd338-131">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="fd338-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="fd338-132">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="fd338-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
