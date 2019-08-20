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
ms.openlocfilehash: a20c0a6fd729c2fc34449167eb92cb774bc3b84e
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602010"
---
# <a name="private-c-reference"></a><span data-ttu-id="fab6f-102">private (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="fab6f-102">private (C# Reference)</span></span>

<span data-ttu-id="fab6f-103">`private` Klíčové slovo je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="fab6f-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="fab6f-104">Tato stránka se `private` zabývá přístupem.</span><span class="sxs-lookup"><span data-stu-id="fab6f-104">This page covers `private` access.</span></span> <span data-ttu-id="fab6f-105">Klíčové slovo je také součástí [`private protected`](./private-protected.md) modifikátoru přístupu. `private`</span><span class="sxs-lookup"><span data-stu-id="fab6f-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="fab6f-106">Privátní přístup je nejnižší úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="fab6f-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="fab6f-107">Soukromé členy jsou přístupné pouze v těle třídy nebo struktury, ve které jsou deklarovány, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="fab6f-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="fab6f-108">K těmto soukromým členům mohou přistupovat i vnořené typy ve stejném těle.</span><span class="sxs-lookup"><span data-stu-id="fab6f-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="fab6f-109">Jedná se o chybu při kompilaci, která odkazuje na soukromého člena mimo třídu nebo strukturu, ve které je deklarována.</span><span class="sxs-lookup"><span data-stu-id="fab6f-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="fab6f-110">Porovnání `private` s dalšími modifikátory přístupu najdete v tématu [úrovně](accessibility-levels.md) přístupnosti a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="fab6f-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="fab6f-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="fab6f-111">Example</span></span>

<span data-ttu-id="fab6f-112">V tomto příkladu `Employee` třída obsahuje dva soukromé datové `name` členy a `salary`.</span><span class="sxs-lookup"><span data-stu-id="fab6f-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="fab6f-113">Jako soukromé členy nejsou k dispozici, s výjimkou metod členů.</span><span class="sxs-lookup"><span data-stu-id="fab6f-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="fab6f-114">Veřejné metody s `GetName` názvem `Salary` a jsou přidány, aby umožnily řízený přístup soukromým členům.</span><span class="sxs-lookup"><span data-stu-id="fab6f-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="fab6f-115">K členu se dá získat přístup prostřednictvím veřejné metody `salary` a k zobrazení člena se dostanete pomocí veřejné vlastnosti jen pro čtení. `name`</span><span class="sxs-lookup"><span data-stu-id="fab6f-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="fab6f-116">(Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md) .)</span><span class="sxs-lookup"><span data-stu-id="fab6f-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="fab6f-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fab6f-117">C# language specification</span></span>  

<span data-ttu-id="fab6f-118">Další informace najdete v tématu [deklarované](~/_csharplang/spec/basic-concepts.md#declared-accessibility) přístupnosti ve [ C# specifikaci jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="fab6f-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="fab6f-119">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="fab6f-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="fab6f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fab6f-120">See also</span></span>

- [<span data-ttu-id="fab6f-121">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="fab6f-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fab6f-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="fab6f-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fab6f-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="fab6f-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="fab6f-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="fab6f-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="fab6f-125">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="fab6f-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="fab6f-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="fab6f-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="fab6f-127">public</span><span class="sxs-lookup"><span data-stu-id="fab6f-127">public</span></span>](public.md)
- [<span data-ttu-id="fab6f-128">protected</span><span class="sxs-lookup"><span data-stu-id="fab6f-128">protected</span></span>](protected.md)
- [<span data-ttu-id="fab6f-129">internal</span><span class="sxs-lookup"><span data-stu-id="fab6f-129">internal</span></span>](internal.md)
