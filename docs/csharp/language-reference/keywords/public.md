---
description: Public – klíčové slovo – Referenční dokumentace jazyka C#
title: Public – klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 26edaf7538d11d082a4b8863228213c3ebc46937
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122339"
---
# <a name="public-c-reference"></a><span data-ttu-id="62644-103">public (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="62644-103">public (C# Reference)</span></span>

<span data-ttu-id="62644-104">`public`Klíčové slovo je modifikátor přístupu pro typy a členy typů.</span><span class="sxs-lookup"><span data-stu-id="62644-104">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="62644-105">Veřejný přístup je nejpřísnější úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="62644-105">Public access is the most permissive access level.</span></span> <span data-ttu-id="62644-106">Pro přístup k veřejným členům neexistují žádná omezení, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="62644-106">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="62644-107">Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovně přístupnosti](accessibility-levels.md) .</span><span class="sxs-lookup"><span data-stu-id="62644-107">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="62644-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="62644-108">Example</span></span>

<span data-ttu-id="62644-109">V následujícím příkladu jsou deklarovány dvě třídy, `PointTest` a `MainClass` .</span><span class="sxs-lookup"><span data-stu-id="62644-109">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="62644-110">Veřejné členy `x` a `y` `PointTest` jsou přístupné přímo z `MainClass` .</span><span class="sxs-lookup"><span data-stu-id="62644-110">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="62644-111">Pokud změníte `public` úroveň přístupu na [soukromou](private.md) nebo [chráněnou](protected.md), zobrazí se chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="62644-111">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="62644-112">' PointTest. y ' je z důvodu úrovně ochrany nedostupné.</span><span class="sxs-lookup"><span data-stu-id="62644-112">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="62644-113">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62644-113">C# language specification</span></span>  

<span data-ttu-id="62644-114">Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="62644-114">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="62644-115">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="62644-115">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="62644-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="62644-116">See also</span></span>

- [<span data-ttu-id="62644-117">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62644-117">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="62644-118">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="62644-118">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="62644-119">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="62644-119">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="62644-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="62644-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="62644-121">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="62644-121">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="62644-122">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="62644-122">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="62644-123">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="62644-123">Modifiers</span></span>](index.md)
- [<span data-ttu-id="62644-124">private</span><span class="sxs-lookup"><span data-stu-id="62644-124">private</span></span>](private.md)
- [<span data-ttu-id="62644-125">protected</span><span class="sxs-lookup"><span data-stu-id="62644-125">protected</span></span>](protected.md)
- [<span data-ttu-id="62644-126">internal</span><span class="sxs-lookup"><span data-stu-id="62644-126">internal</span></span>](internal.md)
