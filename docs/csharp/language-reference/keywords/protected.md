---
title: Protected – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: f25e692430f876ec384971079d6d0aa2c97e967b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484232"
---
# <a name="protected-c-reference"></a><span data-ttu-id="ed5d5-102">protected (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ed5d5-102">protected (C# Reference)</span></span>

<span data-ttu-id="ed5d5-103">`protected` – Klíčové slovo je modifikátor přístupu členu.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="ed5d5-104">Tato stránka popisuje `protected` přístup.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-104">This page covers `protected` access.</span></span> <span data-ttu-id="ed5d5-105">`protected` – Klíčové slovo je také součástí [ `protected internal` ](protected-internal.md) a [ `private protected` ](private-protected.md) modifikátorů přístupu.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="ed5d5-106">Chráněný člen je přístupný v rámci své třídy a instance odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="ed5d5-107">Porovnání `protected` jiných přístupu modifikátory přístupu, najdete v článku [úrovní přístupu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="ed5d5-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="ed5d5-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed5d5-108">Example</span></span>

<span data-ttu-id="ed5d5-109">Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že dojde k přístup až po typ odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="ed5d5-110">Představte si třeba následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="ed5d5-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="ed5d5-111">Příkaz `a.x = 10` dojde k chybě, protože se provádí v rámci statickou metodu Main, a ne instance třídy B.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="ed5d5-112">Členy struktury nejde chránit, protože struktura nemůže dědit.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="ed5d5-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="ed5d5-113">Example</span></span>

<span data-ttu-id="ed5d5-114">V tomto příkladu třída `DerivedPoint` je odvozen z `Point`.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="ed5d5-115">Proto můžete přistupovat k chráněným členům základní třídy přímo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="ed5d5-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="ed5d5-116">Pokud změníte úrovně přístupu `x` a `y` k [privátní](private.md), kompilátor vydá chybové zprávy:</span><span class="sxs-lookup"><span data-stu-id="ed5d5-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="ed5d5-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ed5d5-117">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ed5d5-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ed5d5-118">See also</span></span>

- [<span data-ttu-id="ed5d5-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ed5d5-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="ed5d5-120">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="ed5d5-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="ed5d5-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ed5d5-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ed5d5-122">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="ed5d5-122">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="ed5d5-123">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="ed5d5-123">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="ed5d5-124">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="ed5d5-124">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="ed5d5-125">public</span><span class="sxs-lookup"><span data-stu-id="ed5d5-125">public</span></span>](public.md)
- [<span data-ttu-id="ed5d5-126">private</span><span class="sxs-lookup"><span data-stu-id="ed5d5-126">private</span></span>](private.md)
- [<span data-ttu-id="ed5d5-127">internal</span><span class="sxs-lookup"><span data-stu-id="ed5d5-127">internal</span></span>](internal.md)
- <span data-ttu-id="ed5d5-128">[Zajištění zabezpečení pro klíčových slov internal virtual](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="ed5d5-128">[Security concerns for internal virtual keywords](https://docs.microsoft.com/en-us/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>