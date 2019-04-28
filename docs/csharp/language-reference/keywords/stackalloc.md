---
title: stackalloc – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 04/12/2018
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.openlocfilehash: 61a27e777a1919a2a6fc5140a311835a8f3daba9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660707"
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="c3414-102">stackalloc (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c3414-102">stackalloc (C# Reference)</span></span>

<span data-ttu-id="c3414-103">`stackalloc` – Klíčové slovo se používá k přidělení bloku paměti na zásobníku.</span><span class="sxs-lookup"><span data-stu-id="c3414-103">The `stackalloc` keyword is used to allocate a block of memory on the stack.</span></span>

```csharp
Span<int> block = stackalloc int[100];
```

<span data-ttu-id="c3414-104">Přiřazení přiděleného bloku k <xref:System.Span%601?displayName=nameWithType> místo `int*` umožňuje přidělení zásobníku v nouzovém bloku.</span><span class="sxs-lookup"><span data-stu-id="c3414-104">Assigning the allocated block to a <xref:System.Span%601?displayName=nameWithType> instead of an `int*` allows stack allocations in a safe block.</span></span> <span data-ttu-id="c3414-105">`unsafe` Kontextu se nevyžaduje.</span><span class="sxs-lookup"><span data-stu-id="c3414-105">The `unsafe` context is not required.</span></span>

## <a name="remarks"></a><span data-ttu-id="c3414-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c3414-106">Remarks</span></span>

<span data-ttu-id="c3414-107">Klíčové slovo je platný jenom v místní proměnné inicializátory.</span><span class="sxs-lookup"><span data-stu-id="c3414-107">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="c3414-108">Následující kód způsobí chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c3414-108">The following code causes compiler errors.</span></span>

```csharp
int* block;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
block = stackalloc int[100];
Span<int> span;
// The following assignment statement causes compiler errors. You
// can use stackalloc only when declaring and initializing a local
// variable.
span = stackalloc int[100];
```

<span data-ttu-id="c3414-109">Od verze C# 7.3, můžete použít syntaxi inicializátoru pole pro `stackalloc` pole.</span><span class="sxs-lookup"><span data-stu-id="c3414-109">Beginning with C# 7.3, you can use array initializer syntax for `stackalloc` arrays.</span></span> <span data-ttu-id="c3414-110">Následující deklarace deklarovat pole s tři elementy, jejichž hodnoty jsou celá čísla `1`, `2`, a `3`.</span><span class="sxs-lookup"><span data-stu-id="c3414-110">All the following declarations declare an array with three elements whose values are the integers `1`, `2`, and `3`.</span></span> <span data-ttu-id="c3414-111">Druhý inicializace přiřadí paměti pro <xref:System.ReadOnlySpan%601>, označující, že je paměť nelze upravit.</span><span class="sxs-lookup"><span data-stu-id="c3414-111">The second initialization assigns the memory to a <xref:System.ReadOnlySpan%601>, indicating that the memory cannot be modified.</span></span>

```csharp
// Valid starting with C# 7.3
Span<int> first = stackalloc int[3] { 1, 2, 3 };
ReadOnlySpan<int> second = stackalloc int[] { 1, 2, 3 };
Span<int> third = stackalloc[] { 1, 2, 3 };
```

<span data-ttu-id="c3414-112">Pokud se jedná o typy ukazatelů, `stackalloc` vyžaduje [nebezpečné](unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="c3414-112">When pointer types are involved, `stackalloc` requires an [unsafe](unsafe.md) context.</span></span> <span data-ttu-id="c3414-113">Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="c3414-113">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="c3414-114">`stackalloc` je třeba [_alloca](/cpp/c-runtime-library/reference/alloca) v knihovně C Runtime.</span><span class="sxs-lookup"><span data-stu-id="c3414-114">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>

## <a name="examples"></a><span data-ttu-id="c3414-115">Příklady</span><span class="sxs-lookup"><span data-stu-id="c3414-115">Examples</span></span>

<span data-ttu-id="c3414-116">Následující příklad vypočítá a zobrazí prvních 20 čísla v pořadí Fibonacciho.</span><span class="sxs-lookup"><span data-stu-id="c3414-116">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="c3414-117">Každé číslo je součtu předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="c3414-117">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="c3414-118">V kódu, blok paměti dostatečnou velikost tak, aby obsahovala 20 prvky typu `int` přidělené v zásobníku, není haldy.</span><span class="sxs-lookup"><span data-stu-id="c3414-118">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="c3414-119">Adresu bloku je uložen v `Span` `fib`.</span><span class="sxs-lookup"><span data-stu-id="c3414-119">The address of the block is stored in the `Span` `fib`.</span></span> <span data-ttu-id="c3414-120">Tuto paměť není předmětem pravidla kolekce paměti a proto nemusí být připnutá (s použitím [oprava](fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="c3414-120">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](fixed-statement.md)).</span></span> <span data-ttu-id="c3414-121">Životnost blok paměti je omezená na životnost metody, která ho definuje.</span><span class="sxs-lookup"><span data-stu-id="c3414-121">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="c3414-122">Nelze uvolnit paměť, než metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="c3414-122">You cannot free the memory before the method returns.</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#1)]

<span data-ttu-id="c3414-123">Následující příklad inicializuje `stackalloc` pole celých čísel bitová maska s jeden bit nastaven v jednotlivých prvcích.</span><span class="sxs-lookup"><span data-stu-id="c3414-123">The following example initializes a `stackalloc` array of integers to a bit mask with one bit set in each element.</span></span> <span data-ttu-id="c3414-124">Tento příklad ukazuje novou syntaxi inicializátoru k dispozici od C# 7.3:</span><span class="sxs-lookup"><span data-stu-id="c3414-124">This demonstrates the new initializer syntax available starting in C# 7.3:</span></span>

[!code-csharp[csrefKeywordsOperator#15](~/samples/snippets/csharp/keywords/StackAllocExamples.cs#2)]

## <a name="security"></a><span data-ttu-id="c3414-125">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="c3414-125">Security</span></span>

<span data-ttu-id="c3414-126">Měli byste použít <xref:System.Span%601> nebo <xref:System.ReadOnlySpan%601> Pokud je to možné, protože je méně bezpečné než bezpečné alternativy nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="c3414-126">You should use <xref:System.Span%601> or <xref:System.ReadOnlySpan%601> when possible because unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="c3414-127">I v případě, že se používá s ukazateli, použití `stackalloc` automaticky povoluje funkce detekce přetečení vyrovnávací paměti v modulu common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="c3414-127">Even when used with pointers, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="c3414-128">Pokud se zjistí přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat pravděpodobnost, že je proveden škodlivý kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="c3414-128">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="c3414-129">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c3414-129">C# language specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="c3414-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c3414-130">See also</span></span>

- [<span data-ttu-id="c3414-131">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c3414-131">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c3414-132">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c3414-132">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c3414-133">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c3414-133">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="c3414-134">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="c3414-134">Operator Keywords</span></span>](operator-keywords.md)
- [<span data-ttu-id="c3414-135">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="c3414-135">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
