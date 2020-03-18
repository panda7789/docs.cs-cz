---
title: nebezpečné klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712985"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="79ed4-102">unsafe (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="79ed4-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="79ed4-103">Klíčové `unsafe` slovo označuje nebezpečný kontext, který je vyžadován pro všechny operace zahrnující ukazatele.</span><span class="sxs-lookup"><span data-stu-id="79ed4-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="79ed4-104">Další informace naleznete [v tématu Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="79ed4-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="79ed4-105">`unsafe` Modifikátor můžete použít v deklaraci typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="79ed4-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="79ed4-106">Celý textový rozsah typu nebo člena je proto považován za nebezpečný kontext.</span><span class="sxs-lookup"><span data-stu-id="79ed4-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="79ed4-107">Například následující je metoda deklarovaná modifikátorem: `unsafe`</span><span class="sxs-lookup"><span data-stu-id="79ed4-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="79ed4-108">Rozsah nebezpečného kontextu sahá od seznamu parametrů až po konec metody, takže ukazatele lze také použít v seznamu parametrů:</span><span class="sxs-lookup"><span data-stu-id="79ed4-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="79ed4-109">Můžete také použít nebezpečný blok k povolení použití nebezpečného kódu uvnitř tohoto bloku.</span><span class="sxs-lookup"><span data-stu-id="79ed4-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="79ed4-110">Například:</span><span class="sxs-lookup"><span data-stu-id="79ed4-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="79ed4-111">Chcete-li zkompilovat [`-unsafe`](../compiler-options/unsafe-compiler-option.md) nebezpečný kód, musíte zadat možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="79ed4-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="79ed4-112">Nebezpečný kód není ověřitelný běžným jazykem runtime.</span><span class="sxs-lookup"><span data-stu-id="79ed4-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="79ed4-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="79ed4-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="79ed4-114">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="79ed4-114">C# language specification</span></span>

<span data-ttu-id="79ed4-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="79ed4-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="79ed4-116">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="79ed4-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="79ed4-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="79ed4-117">See also</span></span>

- [<span data-ttu-id="79ed4-118">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="79ed4-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="79ed4-119">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="79ed4-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="79ed4-120">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="79ed4-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="79ed4-121">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="79ed4-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="79ed4-122">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="79ed4-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="79ed4-123">Vyrovnávací paměti s pevnou velikostí</span><span class="sxs-lookup"><span data-stu-id="79ed4-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
