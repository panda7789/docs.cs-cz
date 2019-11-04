---
title: klíčové slovo Public C# – reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: dfb6e341ea0740225d7600f07af2813d39141b45
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422560"
---
# <a name="public-c-reference"></a><span data-ttu-id="3d3ad-102">public (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3d3ad-102">public (C# Reference)</span></span>

<span data-ttu-id="3d3ad-103">Klíčové slovo `public` je modifikátor přístupu pro typy a členy typů.</span><span class="sxs-lookup"><span data-stu-id="3d3ad-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="3d3ad-104">Veřejný přístup je nejpřísnější úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="3d3ad-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="3d3ad-105">Pro přístup k veřejným členům neexistují žádná omezení, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="3d3ad-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="3d3ad-106">Další informace najdete v tématu [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovně přístupnosti](accessibility-levels.md) .</span><span class="sxs-lookup"><span data-stu-id="3d3ad-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="3d3ad-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3d3ad-107">Example</span></span>

<span data-ttu-id="3d3ad-108">V následujícím příkladu jsou deklarovány dvě třídy, `PointTest` a `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="3d3ad-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="3d3ad-109">Veřejné členy `x` a `y` `PointTest` jsou přístupné přímo ze `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="3d3ad-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="3d3ad-110">Pokud změníte úroveň přístupu `public` na [soukromou](private.md) nebo [chráněnou](protected.md), zobrazí se chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="3d3ad-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="3d3ad-111">' PointTest. y ' je z důvodu úrovně ochrany nedostupné.</span><span class="sxs-lookup"><span data-stu-id="3d3ad-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3d3ad-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d3ad-112">C# language specification</span></span>  

<span data-ttu-id="3d3ad-113">Další informace najdete v tématu [deklarované přístupnosti](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="3d3ad-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="3d3ad-114">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3d3ad-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d3ad-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3d3ad-115">See also</span></span>

- [<span data-ttu-id="3d3ad-116">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="3d3ad-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3d3ad-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3d3ad-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3d3ad-118">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3d3ad-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3d3ad-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3d3ad-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3d3ad-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3d3ad-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="3d3ad-121">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="3d3ad-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="3d3ad-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="3d3ad-122">Modifiers</span></span>](index.md)
- [<span data-ttu-id="3d3ad-123">private</span><span class="sxs-lookup"><span data-stu-id="3d3ad-123">private</span></span>](private.md)
- [<span data-ttu-id="3d3ad-124">protected</span><span class="sxs-lookup"><span data-stu-id="3d3ad-124">protected</span></span>](protected.md)
- [<span data-ttu-id="3d3ad-125">internal</span><span class="sxs-lookup"><span data-stu-id="3d3ad-125">internal</span></span>](internal.md)
