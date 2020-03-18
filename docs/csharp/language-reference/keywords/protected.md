---
title: chráněné klíčové slovo - C# Reference
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: bec619d4f49bd26daa742c18c830909c14948adf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713180"
---
# <a name="protected-c-reference"></a><span data-ttu-id="70211-102">protected (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="70211-102">protected (C# Reference)</span></span>

<span data-ttu-id="70211-103">Klíčové `protected` slovo je modifikátor přístupu člena.</span><span class="sxs-lookup"><span data-stu-id="70211-103">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="70211-104">Tato stránka `protected` se týká přístupu.</span><span class="sxs-lookup"><span data-stu-id="70211-104">This page covers `protected` access.</span></span> <span data-ttu-id="70211-105">Klíčové `protected` slovo je také [`protected internal`](protected-internal.md) [`private protected`](private-protected.md) součástí modifikátorů a přístup.</span><span class="sxs-lookup"><span data-stu-id="70211-105">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="70211-106">Chráněný člen je přístupný v rámci své třídy a podle odvozených instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="70211-106">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="70211-107">Porovnání `protected` s ostatními modifikátory přístupu naleznete v [tématu Úrovně usnadnění přístupu](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="70211-107">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="70211-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="70211-108">Example</span></span>

<span data-ttu-id="70211-109">Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že přístup probíhá prostřednictvím odvozeného typu třídy.</span><span class="sxs-lookup"><span data-stu-id="70211-109">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="70211-110">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="70211-110">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="70211-111">Příkaz `a.x = 10` generuje chybu, protože je provedena v rámci statické metody Main a není instancí třídy B.</span><span class="sxs-lookup"><span data-stu-id="70211-111">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="70211-112">Členy struktury nelze chránit, protože strukturu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="70211-112">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="70211-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="70211-113">Example</span></span>

<span data-ttu-id="70211-114">V tomto příkladu `DerivedPoint` je třída `Point`odvozena od .</span><span class="sxs-lookup"><span data-stu-id="70211-114">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="70211-115">Proto můžete přistupovat k chráněným členům základní třídy přímo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="70211-115">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="70211-116">Pokud změníte úrovně `x` přístupu a `y` [soukromé](private.md), kompilátor vydá chybové zprávy:</span><span class="sxs-lookup"><span data-stu-id="70211-116">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="70211-117">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70211-117">C# language specification</span></span>  

<span data-ttu-id="70211-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="70211-118">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="70211-119">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="70211-119">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="70211-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="70211-120">See also</span></span>

- [<span data-ttu-id="70211-121">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70211-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="70211-122">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="70211-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="70211-123">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="70211-123">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="70211-124">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="70211-124">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="70211-125">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="70211-125">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="70211-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="70211-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="70211-127">Veřejné</span><span class="sxs-lookup"><span data-stu-id="70211-127">public</span></span>](public.md)
- [<span data-ttu-id="70211-128">Soukromé</span><span class="sxs-lookup"><span data-stu-id="70211-128">private</span></span>](private.md)
- [<span data-ttu-id="70211-129">Vnitřní</span><span class="sxs-lookup"><span data-stu-id="70211-129">internal</span></span>](internal.md)
- <span data-ttu-id="70211-130">[Obavy o zabezpečení interních virtuálních klíčových slov](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="70211-130">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
