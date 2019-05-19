---
title: unsafe – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: bca12c1dd8c79a5ae17e4a9b7b75d3c7b302fb89
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875865"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="6d0ec-102">unsafe (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6d0ec-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="6d0ec-103">`unsafe` – Klíčové slovo označuje nezabezpečený kontext, který se vyžaduje pro libovolnou operaci s ukazateli.</span><span class="sxs-lookup"><span data-stu-id="6d0ec-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="6d0ec-104">Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d0ec-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="6d0ec-105">Můžete použít `unsafe` modifikátor v deklaraci typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="6d0ec-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="6d0ec-106">Textové celý rozsah tento typ nebo člen je proto považován za nezabezpečený kontext.</span><span class="sxs-lookup"><span data-stu-id="6d0ec-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="6d0ec-107">Například tady je metody deklarované s `unsafe` modifikátor:</span><span class="sxs-lookup"><span data-stu-id="6d0ec-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="6d0ec-108">Obor nezabezpečeném kontextu rozšiřuje ze seznamu parametrů na konec metody, takže ukazatele lze také v seznamu parametrů:</span><span class="sxs-lookup"><span data-stu-id="6d0ec-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="6d0ec-109">Můžete také použít blok unsafe umožní použít nezabezpečený kód v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="6d0ec-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="6d0ec-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6d0ec-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="6d0ec-111">Chcete-li zkompilovat nebezpečný kód, je nutné zadat [ `-unsafe` ](../compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6d0ec-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="6d0ec-112">Nezabezpečený kód není možné ověřit modulem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="6d0ec-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="6d0ec-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d0ec-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="6d0ec-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6d0ec-114">C# language specification</span></span>

<span data-ttu-id="6d0ec-115">Další informace najdete v tématu [nezabezpečený kód](~/_csharplang/spec/unsafe-code.md) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="6d0ec-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="6d0ec-116">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="6d0ec-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="6d0ec-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6d0ec-117">See also</span></span>

- [<span data-ttu-id="6d0ec-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6d0ec-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6d0ec-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6d0ec-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6d0ec-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6d0ec-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6d0ec-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="6d0ec-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="6d0ec-122">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="6d0ec-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="6d0ec-123">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="6d0ec-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
