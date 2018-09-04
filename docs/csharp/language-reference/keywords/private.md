---
title: Private – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- private_CSharpKeyword
- private
helpviewer_keywords:
- private keyword [C#]
ms.assetid: 654c0bb8-e6ac-4086-bf96-7474fa6aa1c8
ms.openlocfilehash: 0c564f38940e993bdfb93af0ec995c684be0eeb7
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43537784"
---
# <a name="private-c-reference"></a><span data-ttu-id="23104-102">private (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="23104-102">private (C# Reference)</span></span>

<span data-ttu-id="23104-103">`private` – Klíčové slovo je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="23104-103">The `private` keyword is a member access modifier.</span></span>

> <span data-ttu-id="23104-104">Tato stránka popisuje `private` přístup.</span><span class="sxs-lookup"><span data-stu-id="23104-104">This page covers `private` access.</span></span> <span data-ttu-id="23104-105">`private` – Klíčové slovo je také součástí [ `private protected` ](./private-protected.md) modifikátor přístupu.</span><span class="sxs-lookup"><span data-stu-id="23104-105">The `private` keyword is also part of the [`private protected`](./private-protected.md) access modifier.</span></span>

<span data-ttu-id="23104-106">Soukromý přístup je omezenou úroveň přístupu.</span><span class="sxs-lookup"><span data-stu-id="23104-106">Private access is the least permissive access level.</span></span> <span data-ttu-id="23104-107">Privátní členy jsou přístupné jenom v rámci třídy nebo struktury, ve kterém jsou deklarovány, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="23104-107">Private members are accessible only within the body of the class or the struct in which they are declared, as in this example:</span></span>

```csharp
class Employee
{
    private int i;
    double d;   // private access by default
}
```

<span data-ttu-id="23104-108">Vnořené typy ve stejné tělo se dostanete také tyto soukromé členy.</span><span class="sxs-lookup"><span data-stu-id="23104-108">Nested types in the same body can also access those private members.</span></span>

<span data-ttu-id="23104-109">Je chyba kompilace tak, aby odkazovaly soukromý člen mimo třídy nebo struktury, ve kterém je deklarována.</span><span class="sxs-lookup"><span data-stu-id="23104-109">It is a compile-time error to reference a private member outside the class or the struct in which it is declared.</span></span>

<span data-ttu-id="23104-110">Porovnání `private` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md) a [modifikátory přístupu](../../programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="23104-110">For a comparison of `private` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md) and [Access Modifiers](../../programming-guide/classes-and-structs/access-modifiers.md).</span></span>

## <a name="example"></a><span data-ttu-id="23104-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="23104-111">Example</span></span>

<span data-ttu-id="23104-112">V tomto příkladu `Employee` třída obsahuje dva soukromé datové členy `name` a `salary`.</span><span class="sxs-lookup"><span data-stu-id="23104-112">In this example, the `Employee` class contains two private data members, `name` and `salary`.</span></span> <span data-ttu-id="23104-113">Jako soukromé členy k nim nelze přistupovat s výjimkou metody člena.</span><span class="sxs-lookup"><span data-stu-id="23104-113">As private members, they cannot be accessed except by member methods.</span></span> <span data-ttu-id="23104-114">Veřejné metody s názvem `GetName` a `Salary` přidávají povolit řízený přístup k soukromým členům.</span><span class="sxs-lookup"><span data-stu-id="23104-114">Public methods named `GetName` and `Salary` are added to allow controlled access to the private members.</span></span> <span data-ttu-id="23104-115">`name` Člen přistupuje prostřednictvím veřejnou metodu a `salary` člen přistupuje prostřednictvím veřejné vlastnosti jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="23104-115">The `name` member is accessed by way of a public method, and the `salary` member is accessed by way of a public read-only property.</span></span> <span data-ttu-id="23104-116">(Viz [vlastnosti](../../programming-guide/classes-and-structs/properties.md) Další informace.)</span><span class="sxs-lookup"><span data-stu-id="23104-116">(See [Properties](../../programming-guide/classes-and-structs/properties.md) for more information.)</span></span>

[!code-csharp[csrefKeywordsModifiers#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#10)]

## <a name="c-language-specification"></a><span data-ttu-id="23104-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="23104-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="23104-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="23104-118">See also</span></span>

- [<span data-ttu-id="23104-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="23104-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="23104-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="23104-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="23104-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="23104-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="23104-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="23104-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="23104-123">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="23104-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="23104-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="23104-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="23104-125">public</span><span class="sxs-lookup"><span data-stu-id="23104-125">public</span></span>](public.md)
- [<span data-ttu-id="23104-126">protected</span><span class="sxs-lookup"><span data-stu-id="23104-126">protected</span></span>](protected.md)
- [<span data-ttu-id="23104-127">internal</span><span class="sxs-lookup"><span data-stu-id="23104-127">internal</span></span>](internal.md)