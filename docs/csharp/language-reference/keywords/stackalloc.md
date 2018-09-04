---
title: stackalloc (Referenční dokumentace jazyka C#)
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 5926550eea1f5a2f8fb74645f22ca54c2bed3136
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43508577"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="53a8b-102">stackalloc (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="53a8b-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="53a8b-103">`stackalloc` – Klíčové slovo se používá v kontextu unsafe kódu k přidělení bloku paměti na zásobníku.</span><span class="sxs-lookup"><span data-stu-id="53a8b-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>

```csharp
int* block = stackalloc int[100];
```

## <a name="remarks"></a><span data-ttu-id="53a8b-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53a8b-104">Remarks</span></span>

<span data-ttu-id="53a8b-105">Klíčové slovo je platný jenom v místní proměnné inicializátory.</span><span class="sxs-lookup"><span data-stu-id="53a8b-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="53a8b-106">Následující kód způsobí chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="53a8b-106">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
```

<span data-ttu-id="53a8b-107">Od verze C# 7.3, můžete použít syntaxi inicializátoru pole pro `stackalloc` pole.</span><span class="sxs-lookup"><span data-stu-id="53a8b-107">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="53a8b-108">Následující deklarace deklarovat pole s tři elementy, jejichž hodnoty jsou celá čísla `1`, `2`, a `3`:</span><span class="sxs-lookup"><span data-stu-id="53a8b-108">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`:</span></span>

```csharp
// Valid starting with C# 7.3
int* first = stackalloc int[3] { 1, 2, 3 };
int* second = stackalloc int[] { 1, 2, 3 };
int* third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="53a8b-109">Protože se jedná o typy ukazatelů, `stackalloc` vyžaduje [nebezpečné](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="53a8b-109">Because pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="53a8b-110">Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md)</span><span class="sxs-lookup"><span data-stu-id="53a8b-110">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md)</span></span> 

<span data-ttu-id="53a8b-111">`stackalloc` je třeba [_alloca](/cpp/c-runtime-library/reference/alloca) v knihovně C Runtime.</span><span class="sxs-lookup"><span data-stu-id="53a8b-111">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="53a8b-112">Příklady</span><span class="sxs-lookup"><span data-stu-id="53a8b-112">Examples</span></span>

<span data-ttu-id="53a8b-113">Následující příklad vypočítá a zobrazí prvních 20 čísla v pořadí Fibonacciho.</span><span class="sxs-lookup"><span data-stu-id="53a8b-113">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="53a8b-114">Každé číslo je součtu předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="53a8b-114">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="53a8b-115">V kódu, blok paměti dostatečnou velikost tak, aby obsahovala 20 prvky typu `int` přidělené v zásobníku, není haldy.</span><span class="sxs-lookup"><span data-stu-id="53a8b-115">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="53a8b-116">Adresu bloku je uloženou v ukazateli `fib`.</span><span class="sxs-lookup"><span data-stu-id="53a8b-116">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="53a8b-117">Tuto paměť není předmětem pravidla kolekce paměti a proto nemusí být připnutá (s použitím [oprava](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="53a8b-117">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="53a8b-118">Životnost blok paměti je omezená na životnost metody, která ho definuje.</span><span class="sxs-lookup"><span data-stu-id="53a8b-118">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="53a8b-119">Nelze uvolnit paměť, než metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="53a8b-119">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="53a8b-120">Následující příklad inicializuje `stackalloc` pole celých čísel bitová maska s jeden bit nastaven v jednotlivých prvcích.</span><span class="sxs-lookup"><span data-stu-id="53a8b-120">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="53a8b-121">Tento příklad ukazuje novou syntaxi inicializátoru k dispozici od C# 7.3:</span><span class="sxs-lookup"><span data-stu-id="53a8b-121">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](../../../../samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="53a8b-122">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="53a8b-122">Security</span></span>

<span data-ttu-id="53a8b-123">Nezabezpečený kód je méně bezpečné než bezpečné alternativy.</span><span class="sxs-lookup"><span data-stu-id="53a8b-123">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="53a8b-124">Nicméně použití `stackalloc` automaticky povoluje funkce detekce přetečení vyrovnávací paměti v modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="53a8b-124">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="53a8b-125">Pokud se zjistí přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat pravděpodobnost, že je proveden škodlivý kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="53a8b-125">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="53a8b-126">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="53a8b-126">C# Language Specification</span></span>
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="53a8b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="53a8b-127">See Also</span></span>

- [<span data-ttu-id="53a8b-128">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="53a8b-128">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="53a8b-129">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="53a8b-129">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="53a8b-130">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="53a8b-130">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="53a8b-131">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="53a8b-131">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
- [<span data-ttu-id="53a8b-132">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="53a8b-132">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
