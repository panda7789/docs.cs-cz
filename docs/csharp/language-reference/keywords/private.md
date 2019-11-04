---
title: soukromé klíčové slovo C# – reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 19e2925cd65cc9c68ff50d370398a4f401275940
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422595"
---
# <a name="private-c-reference"></a><span data-ttu-id="184e7-102">private (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="184e7-102">private (C# Reference)</span></span>

<span data-ttu-id="184e7-103">Klíčové slovo `private` je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="184e7-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="184e7-104">Tato stránka pokrývá přístup `private`.</span><span class="sxs-lookup"><span data-stu-id="184e7-104">This page covers `private` access.</span></span> <span data-ttu-id="184e7-105">Klíčové slovo `private` je také součástí modifikátoru přístupu [`private protected`](./private-protected.md) .</span><span class="sxs-lookup"><span data-stu-id="184e7-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="184e7-106">Privátní přístup je nejnižší úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="184e7-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="184e7-107">Soukromé členy jsou přístupné pouze v těle třídy nebo struktury, ve které jsou deklarovány, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="184e7-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="184e7-108">K těmto soukromým členům mohou přistupovat i vnořené typy ve stejném těle.</span><span class="sxs-lookup"><span data-stu-id="184e7-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="184e7-109">Jedná se o chybu při kompilaci, která odkazuje na soukromého člena mimo třídu nebo strukturu, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="184e7-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="184e7-110">Porovnání `private` s dalšími modifikátory přístupu najdete v tématu [úrovně přístupnosti](accessibility-levels.md) a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="184e7-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="184e7-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="184e7-111">Example</span></span>

<span data-ttu-id="184e7-112">V tomto příkladu třída `Employee` obsahuje dva soukromé datové členy `name` a `salary`.</span><span class="sxs-lookup"><span data-stu-id="184e7-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="184e7-113">Jako soukromé členy nejsou k dispozici, s výjimkou metod členů.</span><span class="sxs-lookup"><span data-stu-id="184e7-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="184e7-114">Jsou přidány veřejné metody s názvem `GetName` a `Salary`, které umožňují řízený přístup k soukromým členům.</span><span class="sxs-lookup"><span data-stu-id="184e7-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="184e7-115">K `name`mu členu se dá získat přístup prostřednictvím veřejné metody a k `salary`mu členu se dá získat přístup prostřednictvím veřejné vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="184e7-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="184e7-116">(Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md) .)</span><span class="sxs-lookup"><span data-stu-id="184e7-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="184e7-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="184e7-117">C# language specification</span></span>  

<span data-ttu-id="184e7-118">Další informace najdete v tématu [deklarované přístupnosti](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [ C# specifikaci jazyka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="184e7-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="184e7-119">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="184e7-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="184e7-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="184e7-120">See also</span></span>

- [<span data-ttu-id="184e7-121">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="184e7-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="184e7-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="184e7-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="184e7-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="184e7-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="184e7-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="184e7-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="184e7-125">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="184e7-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="184e7-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="184e7-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="184e7-127">public</span><span class="sxs-lookup"><span data-stu-id="184e7-127">public</span></span>](public.md)
- [<span data-ttu-id="184e7-128">protected</span><span class="sxs-lookup"><span data-stu-id="184e7-128">protected</span></span>](protected.md)
- [<span data-ttu-id="184e7-129">internal</span><span class="sxs-lookup"><span data-stu-id="184e7-129">internal</span></span>](internal.md)
