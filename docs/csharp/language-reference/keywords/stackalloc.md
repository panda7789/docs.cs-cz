---
title: "stackalloc (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- stackalloc_CSharpKeyword
- stackalloc
helpviewer_keywords:
- stackalloc keyword [C#]
ms.assetid: adc04c28-3ed2-4326-807a-7545df92b852
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad4453f889a344fcd44dfad44a30fef07380b6a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="stackalloc-c-reference"></a><span data-ttu-id="bf43f-102">stackalloc (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="bf43f-102">stackalloc (C# Reference)</span></span>
<span data-ttu-id="bf43f-103">`stackalloc` – Klíčové slovo se používá v kontextu nezabezpečený kód přidělit blok paměti v zásobníku.</span><span class="sxs-lookup"><span data-stu-id="bf43f-103">The `stackalloc` keyword is used in an unsafe code context to allocate a block of memory on the stack.</span></span>  
  
```  
int* block = stackalloc int[100];  
```  
  
## <a name="remarks"></a><span data-ttu-id="bf43f-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bf43f-104">Remarks</span></span>  
 <span data-ttu-id="bf43f-105">Klíčové slovo je platný jenom v místní proměnné inicializátory.</span><span class="sxs-lookup"><span data-stu-id="bf43f-105">The keyword is valid only in local variable initializers.</span></span> <span data-ttu-id="bf43f-106">Následující kód způsobí, že chyby kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="bf43f-106">The following code causes compiler errors.</span></span>  
  
```  
int* block;  
// The following assignment statement causes compiler errors. You  
// can use stackalloc only when declaring and initializing a local   
// variable.  
block = stackalloc int[100];  
```  
  
 <span data-ttu-id="bf43f-107">Protože se jedná o typy ukazatelů `stackalloc` vyžaduje [unsafe](../../../csharp/language-reference/keywords/unsafe.md) kontextu.</span><span class="sxs-lookup"><span data-stu-id="bf43f-107">Because pointer types are involved, `stackalloc` requires [unsafe](../../../csharp/language-reference/keywords/unsafe.md) context.</span></span> <span data-ttu-id="bf43f-108">Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="bf43f-108">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="bf43f-109">`stackalloc`je třeba [_alloca –](/cpp/c-runtime-library/reference/alloca) v běhové knihovny jazyka C.</span><span class="sxs-lookup"><span data-stu-id="bf43f-109">`stackalloc` is like [_alloca](/cpp/c-runtime-library/reference/alloca) in the C run-time library.</span></span>  
  
 <span data-ttu-id="bf43f-110">Následující příklad vypočítá a zobrazuje prvních 20 čísla v pořadí Fibonacciho.</span><span class="sxs-lookup"><span data-stu-id="bf43f-110">The following example calculates and displays the first 20 numbers in the Fibonacci sequence.</span></span> <span data-ttu-id="bf43f-111">Všechna čísla je součet hodnot předchozích dvou čísel.</span><span class="sxs-lookup"><span data-stu-id="bf43f-111">Each number is the sum of the previous two numbers.</span></span> <span data-ttu-id="bf43f-112">V kódu bloku paměti dostatečná velikost tak, aby obsahovala 20 elementy typu `int` je přidělená v zásobníku, není haldě.</span><span class="sxs-lookup"><span data-stu-id="bf43f-112">In the code, a block of memory of sufficient size to contain 20 elements of type `int` is allocated on the stack, not the heap.</span></span> <span data-ttu-id="bf43f-113">Adresu bloku je uložen v ukazatele `fib`.</span><span class="sxs-lookup"><span data-stu-id="bf43f-113">The address of the block is stored in the pointer `fib`.</span></span> <span data-ttu-id="bf43f-114">Tuto paměť nevztahují uvolňování paměti a proto nemusí být připnutý (pomocí [pevné](../../../csharp/language-reference/keywords/fixed-statement.md)).</span><span class="sxs-lookup"><span data-stu-id="bf43f-114">This memory is not subject to garbage collection and therefore does not have to be pinned (by using [fixed](../../../csharp/language-reference/keywords/fixed-statement.md)).</span></span> <span data-ttu-id="bf43f-115">Životnost bloku paměti je omezeno na dobu životnosti metody, která ho definuje.</span><span class="sxs-lookup"><span data-stu-id="bf43f-115">The lifetime of the memory block is limited to the lifetime of the method that defines it.</span></span> <span data-ttu-id="bf43f-116">Nelze uvolnit paměť, než metoda vrátí.</span><span class="sxs-lookup"><span data-stu-id="bf43f-116">You cannot free the memory before the method returns.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf43f-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf43f-117">Example</span></span>  
 [!code-csharp[csrefKeywordsOperator#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/stackalloc_1.cs)]  
  
## <a name="security"></a><span data-ttu-id="bf43f-118">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="bf43f-118">Security</span></span>  
 <span data-ttu-id="bf43f-119">Nezabezpečený kód je méně bezpečné než bezpečné alternativy.</span><span class="sxs-lookup"><span data-stu-id="bf43f-119">Unsafe code is less secure than safe alternatives.</span></span> <span data-ttu-id="bf43f-120">Ale použití `stackalloc` automaticky povolí funkce zjišťování přetečení vyrovnávací paměti v common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="bf43f-120">However, the use of `stackalloc` automatically enables buffer overrun detection features in the common language runtime (CLR).</span></span> <span data-ttu-id="bf43f-121">Pokud je zjištěn přetečení vyrovnávací paměti, co nejrychleji, chcete-li minimalizovat riziko, že se spustí škodlivý kód ukončení procesu.</span><span class="sxs-lookup"><span data-stu-id="bf43f-121">If a buffer overrun is detected, the process is terminated as quickly as possible to minimize the chance that malicious code is executed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="bf43f-122">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bf43f-122">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="bf43f-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf43f-123">See Also</span></span>  
 [<span data-ttu-id="bf43f-124">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bf43f-124">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bf43f-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="bf43f-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bf43f-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="bf43f-126">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="bf43f-127">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="bf43f-127">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="bf43f-128">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="bf43f-128">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)
