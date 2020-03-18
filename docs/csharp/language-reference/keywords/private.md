---
title: soukromé klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: a13e9ef18b0f6452c3ff1497dc97110bc21c433d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715199"
---
# <a name="private-c-reference"></a><span data-ttu-id="59593-102">private (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="59593-102">private (C# Reference)</span></span>

<span data-ttu-id="59593-103">Klíčové `private` slovo je modifikátor přístupu člena.</span><span class="sxs-lookup"><span data-stu-id="59593-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="59593-104">Tato stránka `private` se týká přístupu.</span><span class="sxs-lookup"><span data-stu-id="59593-104">This page covers `private` access.</span></span> <span data-ttu-id="59593-105">Klíčové `private` slovo je také [`private protected`](./private-protected.md) součástí modifikátoru přístupu.</span><span class="sxs-lookup"><span data-stu-id="59593-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="59593-106">Soukromý přístup je nejméně tolerantní úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="59593-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="59593-107">Soukromé členy jsou přístupné pouze v rámci těla třídy nebo struktury, ve kterém jsou deklarovány, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="59593-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="59593-108">Vnořené typy ve stejném těle mohou také přistupovat k těmto soukromým členům.</span><span class="sxs-lookup"><span data-stu-id="59593-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="59593-109">Jedná se o chybu v době kompilace odkazovat na soukromý člen mimo třídu nebo strukturu, ve které je deklarován.</span><span class="sxs-lookup"><span data-stu-id="59593-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="59593-110">Porovnání s `private` ostatními modifikátory přístupu naleznete v [tématu Úrovně přístupnosti](accessibility-levels.md) a [Modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="59593-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="59593-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="59593-111">Example</span></span>

<span data-ttu-id="59593-112">V tomto příkladu `Employee` třída obsahuje dva `name` `salary`soukromé datové členy a .</span><span class="sxs-lookup"><span data-stu-id="59593-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="59593-113">Jako soukromé členy, nemohou být přístupné s výjimkou členské metody.</span><span class="sxs-lookup"><span data-stu-id="59593-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="59593-114">Veřejné metody `GetName` `Salary` s názvem a jsou přidány povolit řízený přístup k soukromým členům.</span><span class="sxs-lookup"><span data-stu-id="59593-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="59593-115">Člen `name` je přístupný prostřednictvím veřejné metody a `salary` člen je přístupný prostřednictvím veřejné vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="59593-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="59593-116">(Další informace naleznete v tématu [Vlastnosti.)](../../programming-guide/classes-and-structs/properties.md)</span><span class="sxs-lookup"><span data-stu-id="59593-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="59593-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="59593-117">C# language specification</span></span>  

<span data-ttu-id="59593-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="59593-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="59593-119">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="59593-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="59593-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="59593-120">See also</span></span>

- [<span data-ttu-id="59593-121">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="59593-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="59593-122">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="59593-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="59593-123">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="59593-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="59593-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="59593-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="59593-125">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="59593-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="59593-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="59593-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="59593-127">Veřejné</span><span class="sxs-lookup"><span data-stu-id="59593-127">public</span></span>](public.md)
- [<span data-ttu-id="59593-128">protected</span><span class="sxs-lookup"><span data-stu-id="59593-128">protected</span></span>](protected.md)
- [<span data-ttu-id="59593-129">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="59593-129">internal</span></span>](internal.md)
