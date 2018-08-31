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
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2018
ms.locfileid: "43256125"
---
# <a name="public-c-reference"></a><span data-ttu-id="01904-102">public (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="01904-102">public (C# Reference)</span></span>

<span data-ttu-id="01904-103">`public` – Klíčové slovo je modifikátor přístupu pro typy a členy typu.</span><span class="sxs-lookup"><span data-stu-id="01904-103">The `public` keyword is an access modifier for types and type members.</span></span> <span data-ttu-id="01904-104">Veřejný přístup je nejvíce omezující úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="01904-104">Public access is the most permissive access level.</span></span> <span data-ttu-id="01904-105">Neexistují žádná omezení na přístup k veřejným členům, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="01904-105">There are no restrictions on accessing public members, as in this example:</span></span>

```csharp
class SampleClass
{
    public int x; // No access restrictions.
}
```

<span data-ttu-id="01904-106">Zobrazit [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md) a [úrovní přístupu](accessibility-levels.md) Další informace.</span><span class="sxs-lookup"><span data-stu-id="01904-106">See [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md) and [Accessibility Levels](accessibility-levels.md) for more information.</span></span>

## <a name="example"></a><span data-ttu-id="01904-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="01904-107">Example</span></span>

<span data-ttu-id="01904-108">V následujícím příkladu se deklarovat dvě třídy, `PointTest` a `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="01904-108">In the following example, two classes are declared, `PointTest` and `MainClass`.</span></span> <span data-ttu-id="01904-109">Veřejné členy `x` a `y` z `PointTest` přistupují přímo z `MainClass`.</span><span class="sxs-lookup"><span data-stu-id="01904-109">The public members `x` and `y` of `PointTest` are accessed directly from `MainClass`.</span></span>

[!code-csharp[csrefKeywordsModifiers#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#13)]

<span data-ttu-id="01904-110">Pokud změníte `public` úroveň přístupu k [privátní](private.md) nebo [chráněné](protected.md), zobrazí se chybová zpráva:</span><span class="sxs-lookup"><span data-stu-id="01904-110">If you change the `public` access level to [private](private.md) or [protected](protected.md), you will get the error message:</span></span>

<span data-ttu-id="01904-111">"PointTest.y" je vzhledem k úrovni ochrany nepřístupný.</span><span class="sxs-lookup"><span data-stu-id="01904-111">'PointTest.y' is inaccessible due to its protection level.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="01904-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01904-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="01904-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="01904-113">See also</span></span>

- [<span data-ttu-id="01904-114">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01904-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="01904-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="01904-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="01904-116">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="01904-116">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="01904-117">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="01904-117">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="01904-118">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="01904-118">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="01904-119">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="01904-119">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="01904-120">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="01904-120">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="01904-121">private</span><span class="sxs-lookup"><span data-stu-id="01904-121">private</span></span>](private.md)
- [<span data-ttu-id="01904-122">protected</span><span class="sxs-lookup"><span data-stu-id="01904-122">protected</span></span>](protected.md)
- [<span data-ttu-id="01904-123">internal</span><span class="sxs-lookup"><span data-stu-id="01904-123">internal</span></span>](internal.md)