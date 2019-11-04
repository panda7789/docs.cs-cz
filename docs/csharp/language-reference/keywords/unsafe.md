---
title: nezabezpečené – C# odkaz na klíčové slovo
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: aa22eac9d4ae06753bbed1fd5733eddeddd81a46
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422275"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="53725-102">unsafe (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="53725-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="53725-103">Klíčové slovo `unsafe` označuje nezabezpečený kontext, který je vyžadován pro všechny operace zahrnující ukazatele.</span><span class="sxs-lookup"><span data-stu-id="53725-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="53725-104">Další informace naleznete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="53725-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="53725-105">Můžete použít modifikátor `unsafe` v deklaraci typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="53725-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="53725-106">Celý textový rozsah typu nebo členu je proto považován za nezabezpečený kontext.</span><span class="sxs-lookup"><span data-stu-id="53725-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="53725-107">Například následující je metoda deklarovaná s modifikátorem `unsafe`:</span><span class="sxs-lookup"><span data-stu-id="53725-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="53725-108">Rozsah nebezpečného kontextu se rozšiřuje ze seznamu parametrů na konec metody, takže ukazatele lze použít také v seznamu parametrů:</span><span class="sxs-lookup"><span data-stu-id="53725-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="53725-109">Pomocí nebezpečného blokování můžete také povolit používání nebezpečného kódu uvnitř tohoto bloku.</span><span class="sxs-lookup"><span data-stu-id="53725-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="53725-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="53725-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="53725-111">Chcete-li zkompilovat nezabezpečený kód, je nutné zadat možnost kompilátoru [`-unsafe`](../compiler-options/unsafe-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="53725-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="53725-112">Modul CLR (Common Language Runtime) neumožňuje ověřit nezabezpečený kód.</span><span class="sxs-lookup"><span data-stu-id="53725-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="53725-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="53725-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="53725-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="53725-114">C# language specification</span></span>

<span data-ttu-id="53725-115">Další informace naleznete v tématu [nezabezpečený kód](~/_csharplang/spec/unsafe-code.md) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="53725-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="53725-116">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="53725-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="53725-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53725-117">See also</span></span>

- [<span data-ttu-id="53725-118">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="53725-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="53725-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="53725-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="53725-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="53725-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="53725-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="53725-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="53725-122">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="53725-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="53725-123">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="53725-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
