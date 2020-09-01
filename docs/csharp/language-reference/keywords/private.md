---
description: Private – klíčové slovo – Reference jazyka C#
title: Private – klíčové slovo – Reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: e6f40712fd2cca6d7b1f64760f1c6c5dd5c71370
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89139395"
---
# <a name="private-c-reference"></a><span data-ttu-id="ccf79-103">private (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ccf79-103">private (C# Reference)</span></span>

<span data-ttu-id="ccf79-104">`private`Klíčové slovo je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="ccf79-104">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="ccf79-105">Tato stránka se zabývá `private` přístupem.</span><span class="sxs-lookup"><span data-stu-id="ccf79-105">This page covers `private` access.</span></span> <span data-ttu-id="ccf79-106">`private`Klíčové slovo je také součástí [`private protected`](./private-protected.md) modifikátoru přístupu.</span><span class="sxs-lookup"><span data-stu-id="ccf79-106">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="ccf79-107">Privátní přístup je nejnižší úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="ccf79-107">Private access is the least permissive access level.</span></span> <span data-ttu-id="ccf79-108">Soukromé členy jsou přístupné pouze v těle třídy nebo struktury, ve které jsou deklarovány, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="ccf79-108">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="ccf79-109">K těmto soukromým členům mohou přistupovat i vnořené typy ve stejném těle.</span><span class="sxs-lookup"><span data-stu-id="ccf79-109">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="ccf79-110">Jedná se o chybu při kompilaci, která odkazuje na soukromého člena mimo třídu nebo strukturu, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="ccf79-110">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="ccf79-111">Porovnání `private` s dalšími modifikátory přístupu najdete v tématu [úrovně přístupnosti](accessibility-levels.md) a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ccf79-111">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="ccf79-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="ccf79-112">Example</span></span>

<span data-ttu-id="ccf79-113">V tomto příkladu `Employee` Třída obsahuje dva soukromé datové členy `name` a `salary` .</span><span class="sxs-lookup"><span data-stu-id="ccf79-113">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="ccf79-114">Jako soukromé členy nejsou k dispozici, s výjimkou metod členů.</span><span class="sxs-lookup"><span data-stu-id="ccf79-114">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="ccf79-115">Veřejné metody s názvem `GetName` a `Salary` jsou přidány, aby umožnily řízený přístup soukromým členům.</span><span class="sxs-lookup"><span data-stu-id="ccf79-115">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="ccf79-116">K `name` členu se dá získat přístup prostřednictvím veřejné metody a k zobrazení `salary` člena se dostanete pomocí veřejné vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="ccf79-116">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="ccf79-117">(Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md) .)</span><span class="sxs-lookup"><span data-stu-id="ccf79-117">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="ccf79-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ccf79-118">C# language specification</span></span>  

<span data-ttu-id="ccf79-119">Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="ccf79-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="ccf79-120">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="ccf79-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="ccf79-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccf79-121">See also</span></span>

- [<span data-ttu-id="ccf79-122">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ccf79-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ccf79-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="ccf79-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ccf79-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ccf79-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ccf79-125">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="ccf79-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="ccf79-126">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="ccf79-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="ccf79-127">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="ccf79-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="ccf79-128">public</span><span class="sxs-lookup"><span data-stu-id="ccf79-128">public</span></span>](public.md)
- [<span data-ttu-id="ccf79-129">protected</span><span class="sxs-lookup"><span data-stu-id="ccf79-129">protected</span></span>](protected.md)
- [<span data-ttu-id="ccf79-130">internal</span><span class="sxs-lookup"><span data-stu-id="ccf79-130">internal</span></span>](internal.md)
