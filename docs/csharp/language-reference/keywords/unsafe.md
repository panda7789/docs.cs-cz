---
description: nezabezpečené klíčové slovo – Referenční dokumentace jazyka C#
title: nezabezpečené klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 2e047a4cff77877862c5cbbb5e49eb1a75b42499
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141956"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="f642e-103">unsafe (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="f642e-103">unsafe (C# Reference)</span></span>

<span data-ttu-id="f642e-104">`unsafe`Klíčové slovo označuje nezabezpečený kontext, který je vyžadován pro všechny operace zahrnující ukazatele.</span><span class="sxs-lookup"><span data-stu-id="f642e-104">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="f642e-105">Další informace naleznete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f642e-105">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="f642e-106">Můžete použít `unsafe` Modifikátor v deklaraci typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="f642e-106">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="f642e-107">Celý textový rozsah typu nebo členu je proto považován za nezabezpečený kontext.</span><span class="sxs-lookup"><span data-stu-id="f642e-107">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="f642e-108">Například následující je metoda deklarovaná s `unsafe` modifikátorem:</span><span class="sxs-lookup"><span data-stu-id="f642e-108">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="f642e-109">Rozsah nebezpečného kontextu se rozšiřuje ze seznamu parametrů na konec metody, takže ukazatele lze použít také v seznamu parametrů:</span><span class="sxs-lookup"><span data-stu-id="f642e-109">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="f642e-110">Pomocí nebezpečného blokování můžete také povolit používání nebezpečného kódu uvnitř tohoto bloku.</span><span class="sxs-lookup"><span data-stu-id="f642e-110">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="f642e-111">Příklad:</span><span class="sxs-lookup"><span data-stu-id="f642e-111">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="f642e-112">Chcete-li zkompilovat nezabezpečený kód, je nutné zadat [`-unsafe`](../compiler-options/unsafe-compiler-option.md) možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="f642e-112">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="f642e-113">Modul CLR (Common Language Runtime) neumožňuje ověřit nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="f642e-113">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="f642e-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="f642e-114">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="f642e-115">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f642e-115">C# language specification</span></span>

<span data-ttu-id="f642e-116">Další informace naleznete v tématu [nezabezpečený kód](~/_csharplang/spec/unsafe-code.md) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="f642e-116">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="f642e-117">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="f642e-117">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="f642e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="f642e-118">See also</span></span>

- [<span data-ttu-id="f642e-119">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f642e-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f642e-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="f642e-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f642e-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="f642e-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f642e-122">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="f642e-122">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="f642e-123">Nezabezpečený kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="f642e-123">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="f642e-124">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="f642e-124">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
