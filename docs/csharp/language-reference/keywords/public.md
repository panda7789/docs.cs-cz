---
title: Public – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: a68cbf3af2568cd3c197eaece9e2d5a25cdb4a6a
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633703"
---
# <a name="public-c-reference"></a><span data-ttu-id="517eb-102">public (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="517eb-102">public (C# Reference)</span></span>

<span data-ttu-id="517eb-103">`public` – Klíčové slovo je modifikátor přístupu pro typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="517eb-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="517eb-104">Veřejný přístup je nejvíce omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="517eb-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="517eb-105">Neexistují žádná omezení na přístup k veřejným členům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="517eb-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="517eb-106">Zobrazit [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovní přístupu](accessibility-levels.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="517eb-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="517eb-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="517eb-107">Example</span></span>

<span data-ttu-id="517eb-108">V následujícím příkladu se deklarovat dvě třídy, `PointTest` a `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="517eb-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="517eb-109">Veřejné členy `x` a `y` z `PointTest` přistupují přímo z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="517eb-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="517eb-110">Pokud změníte `public` úroveň přístupu k [privátní](private.md) nebo [chráněné](protected.md), zobrazí se chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="517eb-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="517eb-111">"PointTest.y" je vzhledem k úrovni ochrany nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="517eb-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="517eb-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="517eb-112">C# language specification</span></span>  

<span data-ttu-id="517eb-113">Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="517eb-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="517eb-114">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="517eb-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="517eb-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="517eb-115">See also</span></span>

- [<span data-ttu-id="517eb-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="517eb-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="517eb-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="517eb-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="517eb-118">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="517eb-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="517eb-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="517eb-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="517eb-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="517eb-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="517eb-121">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="517eb-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="517eb-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="517eb-122">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="517eb-123">private</span><span class="sxs-lookup"><span data-stu-id="517eb-123">private</span></span>](private.md)
- [<span data-ttu-id="517eb-124">protected</span><span class="sxs-lookup"><span data-stu-id="517eb-124">protected</span></span>](protected.md)
- [<span data-ttu-id="517eb-125">internal</span><span class="sxs-lookup"><span data-stu-id="517eb-125">internal</span></span>](internal.md)
