---
title: Public – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- public
- public_CSharpKeyword
helpviewer_keywords:
- public keyword [C#]
ms.assetid: 0ae45d16-a551-4b74-9845-57208de1328e
ms.openlocfilehash: 84a3bc49b6eea047d518edc01dab7f2301854b6a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484154"
---
# <a name="public-c-reference"></a><span data-ttu-id="cbad9-102">public (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="cbad9-102">public (C# Reference)</span></span>

<span data-ttu-id="cbad9-103">`public` – Klíčové slovo je modifikátor přístupu pro typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="cbad9-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="cbad9-104">Veřejný přístup je nejvíce omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="cbad9-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="cbad9-105">Neexistují žádná omezení na přístup k veřejným členům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="cbad9-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="cbad9-106">Zobrazit [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovní přístupu](accessibility-levels.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="cbad9-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="cbad9-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="cbad9-107">Example</span></span>

<span data-ttu-id="cbad9-108">V následujícím příkladu se deklarovat dvě třídy, `PointTest` a `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="cbad9-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="cbad9-109">Veřejné členy `x` a `y` z `PointTest` přistupují přímo z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="cbad9-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="cbad9-110">Pokud změníte `public` úroveň přístupu k [privátní](private.md) nebo [chráněné](protected.md), zobrazí se chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="cbad9-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="cbad9-111">"PointTest.y" je vzhledem k úrovni ochrany nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="cbad9-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="cbad9-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cbad9-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="cbad9-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbad9-113">See also</span></span>

- [<span data-ttu-id="cbad9-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cbad9-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="cbad9-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="cbad9-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="cbad9-116">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="cbad9-116">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="cbad9-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="cbad9-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="cbad9-118">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="cbad9-118">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="cbad9-119">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="cbad9-119">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="cbad9-120">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="cbad9-120">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="cbad9-121">private</span><span class="sxs-lookup"><span data-stu-id="cbad9-121">private</span></span>](private.md)
- [<span data-ttu-id="cbad9-122">protected</span><span class="sxs-lookup"><span data-stu-id="cbad9-122">protected</span></span>](protected.md)
- [<span data-ttu-id="cbad9-123">internal</span><span class="sxs-lookup"><span data-stu-id="cbad9-123">internal</span></span>](internal.md)