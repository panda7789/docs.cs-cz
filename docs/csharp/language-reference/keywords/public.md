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
ms.openlocfilehash: 15b86920736f1220553b462d103841ac98d88b7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660863"
---
# <a name="public-c-reference"></a><span data-ttu-id="3bf9a-102">public (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="3bf9a-102">public (C# Reference)</span></span>

<span data-ttu-id="3bf9a-103">`public` – Klíčové slovo je modifikátor přístupu pro typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="3bf9a-104">Veřejný přístup je nejvíce omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="3bf9a-105">Neexistují žádná omezení na přístup k veřejným členům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3bf9a-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="3bf9a-106">Zobrazit [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovní přístupu](accessibility-levels.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="3bf9a-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="3bf9a-107">Example</span></span>

<span data-ttu-id="3bf9a-108">V následujícím příkladu se deklarovat dvě třídy, `PointTest` a `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="3bf9a-109">Veřejné členy `x` a `y` z `PointTest` přistupují přímo z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="3bf9a-110">Pokud změníte `public` úroveň přístupu k [privátní](private.md) nebo [chráněné](protected.md), zobrazí se chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="3bf9a-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="3bf9a-111">"PointTest.y" je vzhledem k úrovni ochrany nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="3bf9a-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3bf9a-112">C# language specification</span></span>  

<span data-ttu-id="3bf9a-113">Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="3bf9a-113">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="3bf9a-114">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="3bf9a-114">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="3bf9a-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3bf9a-115">See also</span></span>

- [<span data-ttu-id="3bf9a-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3bf9a-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="3bf9a-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3bf9a-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="3bf9a-118">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3bf9a-118">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="3bf9a-119">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3bf9a-119">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="3bf9a-120">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="3bf9a-120">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="3bf9a-121">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="3bf9a-121">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="3bf9a-122">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="3bf9a-122">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="3bf9a-123">private</span><span class="sxs-lookup"><span data-stu-id="3bf9a-123">private</span></span>](private.md)
- [<span data-ttu-id="3bf9a-124">protected</span><span class="sxs-lookup"><span data-stu-id="3bf9a-124">protected</span></span>](protected.md)
- [<span data-ttu-id="3bf9a-125">internal</span><span class="sxs-lookup"><span data-stu-id="3bf9a-125">internal</span></span>](internal.md)