---
title: Protected – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 6d625b2fd0a1f42a0bde7f68ebc332510a4e56ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660889"
---
# <a name="protected-c-reference"></a><span data-ttu-id="8c83f-102">protected (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8c83f-102">protected (C# Reference)</span></span>

<span data-ttu-id="8c83f-103">`protected` – Klíčové slovo je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="8c83f-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="8c83f-104">Tato stránka popisuje `protected` přístup.</span><span class="sxs-lookup"><span data-stu-id="8c83f-104">This page covers `protected` access.</span></span> <span data-ttu-id="8c83f-105">`protected` – Klíčové slovo je také součástí [ `protected internal` ](protected-internal.md) a [ `private protected` ](private-protected.md) modifikátorů přístupu.</span><span class="sxs-lookup"><span data-stu-id="8c83f-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="8c83f-106">Chráněný člen je přístupný v rámci své třídy a instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="8c83f-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="8c83f-107">Porovnání `protected` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="8c83f-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="8c83f-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c83f-108">Example</span></span>

<span data-ttu-id="8c83f-109">Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že dojde k přístup až po typ odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="8c83f-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="8c83f-110">Představte si třeba následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="8c83f-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="8c83f-111">Příkaz `a.x = 10` dojde k chybě, protože se provádí v rámci statickou metodu Main, a ne instance třídy B.</span><span class="sxs-lookup"><span data-stu-id="8c83f-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="8c83f-112">Členy struktury nejde chránit, protože struktura nemůže dědit.</span><span class="sxs-lookup"><span data-stu-id="8c83f-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="8c83f-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c83f-113">Example</span></span>

<span data-ttu-id="8c83f-114">V tomto příkladu třída `DerivedPoint` je odvozen z `Point`.</span><span class="sxs-lookup"><span data-stu-id="8c83f-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="8c83f-115">Proto můžete přistupovat k chráněným členům základní třídy přímo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="8c83f-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="8c83f-116">Pokud změníte úrovně přístupu `x` a `y` k [privátní](private.md), kompilátor vydá chybové zprávy:</span><span class="sxs-lookup"><span data-stu-id="8c83f-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="8c83f-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8c83f-117">C# language specification</span></span>  

<span data-ttu-id="8c83f-118">Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) v [ C# specifikace jazyka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8c83f-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="8c83f-119">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="8c83f-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c83f-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c83f-120">See also</span></span>

- [<span data-ttu-id="8c83f-121">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8c83f-121">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="8c83f-122">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8c83f-122">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="8c83f-123">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8c83f-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8c83f-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="8c83f-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="8c83f-125">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="8c83f-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="8c83f-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="8c83f-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="8c83f-127">public</span><span class="sxs-lookup"><span data-stu-id="8c83f-127">public</span></span>](public.md)
- [<span data-ttu-id="8c83f-128">private</span><span class="sxs-lookup"><span data-stu-id="8c83f-128">private</span></span>](private.md)
- [<span data-ttu-id="8c83f-129">internal</span><span class="sxs-lookup"><span data-stu-id="8c83f-129">internal</span></span>](internal.md)
- <span data-ttu-id="8c83f-130">[Zajištění zabezpečení pro klíčových slov internal virtual](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="8c83f-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>