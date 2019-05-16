---
title: Private – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 67b2621d382651abc27cee2eadad91a6253895c1
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633331"
---
# <a name="private-c-reference"></a><span data-ttu-id="2a3bb-102">private (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2a3bb-102">private (C# Reference)</span></span>

<span data-ttu-id="2a3bb-103">`private` – Klíčové slovo je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="2a3bb-104">Tato stránka popisuje `private` přístup.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-104">This page covers `private` access.</span></span> <span data-ttu-id="2a3bb-105">`private` – Klíčové slovo je také součástí [ `private protected` ](./private-protected.md) modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="2a3bb-106">Soukromý přístup je omezenou úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="2a3bb-107">Privátní členy jsou přístupné jenom v rámci třídy nebo struktury, ve kterém jsou deklarovány, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="2a3bb-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="2a3bb-108">Vnořené typy ve stejné tělo se dostanete také tyto soukromé členy.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="2a3bb-109">Je chyba kompilace tak, aby odkazovaly soukromý člen mimo třídy nebo struktury, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="2a3bb-110">Porovnání `private` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md) a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="2a3bb-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="2a3bb-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="2a3bb-111">Example</span></span>

<span data-ttu-id="2a3bb-112">V tomto příkladu `Employee` třída obsahuje dva soukromé datové členy `name` a `salary`.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="2a3bb-113">Jako soukromé členy k nim nelze přistupovat s výjimkou metody člena.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="2a3bb-114">Veřejné metody s názvem `GetName` a `Salary` přidávají povolit řízený přístup k soukromým členům.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="2a3bb-115">`name` Člen přistupuje prostřednictvím veřejnou metodu a `salary` člen přistupuje prostřednictvím veřejné vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="2a3bb-116">(Viz [vlastnosti](../../programming-guide/classes-and-structs/properties.md) Další informace.)</span><span class="sxs-lookup"><span data-stu-id="2a3bb-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="2a3bb-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a3bb-117">C# language specification</span></span>  

<span data-ttu-id="2a3bb-118">Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="2a3bb-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="2a3bb-119">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2a3bb-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="2a3bb-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a3bb-120">See also</span></span>

- [<span data-ttu-id="2a3bb-121">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a3bb-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="2a3bb-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2a3bb-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="2a3bb-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2a3bb-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2a3bb-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="2a3bb-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="2a3bb-125">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="2a3bb-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="2a3bb-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="2a3bb-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="2a3bb-127">public</span><span class="sxs-lookup"><span data-stu-id="2a3bb-127">public</span></span>](public.md)
- [<span data-ttu-id="2a3bb-128">protected</span><span class="sxs-lookup"><span data-stu-id="2a3bb-128">protected</span></span>](protected.md)
- [<span data-ttu-id="2a3bb-129">internal</span><span class="sxs-lookup"><span data-stu-id="2a3bb-129">internal</span></span>](internal.md)
