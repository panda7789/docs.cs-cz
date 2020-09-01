---
description: Protected klíčové slovo – Referenční dokumentace jazyka C#
title: Protected klíčové slovo – Referenční dokumentace jazyka C#
ms.date: 07/20/2015
f1_keywords:
- protected
- protected_CSharpKeyword
helpviewer_keywords:
- protected keyword [C#]
ms.assetid: 05ce3794-6675-4025-bddb-eaaa0ec22892
ms.openlocfilehash: 4c18d1f2f45a0a154dccd42736a01874dd1af853
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89122378"
---
# <a name="protected-c-reference"></a><span data-ttu-id="2cdc3-103">protected (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2cdc3-103">protected (C# Reference)</span></span>

<span data-ttu-id="2cdc3-104">`protected`Klíčové slovo je modifikátor přístupu ke členu.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-104">The `protected` keyword is a member access modifier.</span></span>

 > <span data-ttu-id="2cdc3-105">Tato stránka se zabývá `protected` přístupem.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-105">This page covers `protected` access.</span></span> <span data-ttu-id="2cdc3-106">`protected`Klíčové slovo je také součástí [`protected internal`](protected-internal.md) [`private protected`](private-protected.md) modifikátorů a přístupu.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-106">The `protected` keyword is also part of the [`protected internal`](protected-internal.md) and [`private protected`](private-protected.md) access modifiers.</span></span>

<span data-ttu-id="2cdc3-107">Chráněný člen je přístupný v rámci své třídy a odvozené instance třídy.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-107">A protected member is accessible within its class and by derived class instances.</span></span>

<span data-ttu-id="2cdc3-108">Porovnání `protected` s dalšími modifikátory přístupu najdete v tématu [úrovně usnadnění](accessibility-levels.md).</span><span class="sxs-lookup"><span data-stu-id="2cdc3-108">For a comparison of `protected` with the other access modifiers, see [Accessibility Levels](accessibility-levels.md).</span></span>

## <a name="example"></a><span data-ttu-id="2cdc3-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="2cdc3-109">Example</span></span>

<span data-ttu-id="2cdc3-110">Chráněný člen základní třídy je přístupný v odvozené třídě pouze v případě, že k přístupu dojde prostřednictvím odvozené třídy typu.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-110">A protected member of a base class is accessible in a derived class only if the access occurs through the derived class type.</span></span> <span data-ttu-id="2cdc3-111">Zvažte například následující segment kódu:</span><span class="sxs-lookup"><span data-stu-id="2cdc3-111">For example, consider the following code segment:</span></span>

[!code-csharp[csrefKeywordsModifiers#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#11)]

<span data-ttu-id="2cdc3-112">Příkaz `a.x = 10` vygeneruje chybu, protože je vytvořena v rámci statické metody Main a nikoli instance třídy B.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-112">The statement `a.x = 10` generates an error because it is made within the static method Main, and not an instance of class B.</span></span>

<span data-ttu-id="2cdc3-113">Členy struktury nelze chránit, protože strukturu nelze zdědit.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-113">Struct members cannot be protected because the struct cannot be inherited.</span></span>

## <a name="example"></a><span data-ttu-id="2cdc3-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="2cdc3-114">Example</span></span>

<span data-ttu-id="2cdc3-115">V tomto příkladu `DerivedPoint` je třída odvozena z `Point` .</span><span class="sxs-lookup"><span data-stu-id="2cdc3-115">In this example, the class `DerivedPoint` is derived from `Point`.</span></span> <span data-ttu-id="2cdc3-116">Proto máte přístup k chráněným členům základní třídy přímo z odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-116">Therefore, you can access the protected members of the base class directly from the derived class.</span></span>

[!code-csharp[csrefKeywordsModifiers#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#12)]  

<span data-ttu-id="2cdc3-117">Pokud změníte úrovně přístupu u `x` a `y` na [Private](private.md), kompilátor vydá chybové zprávy:</span><span class="sxs-lookup"><span data-stu-id="2cdc3-117">If you change the access levels of `x` and `y` to [private](private.md), the compiler will issue the error messages:</span></span>

`'Point.y' is inaccessible due to its protection level.`

`'Point.x' is inaccessible due to its protection level.`

## <a name="c-language-specification"></a><span data-ttu-id="2cdc3-118">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2cdc3-118">C# language specification</span></span>  

<span data-ttu-id="2cdc3-119">Další informace najdete v tématu [deklarovaná přístupnost](~/_csharplang/spec/basic-concepts.md#declared-accessibility) ve [specifikaci jazyka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="2cdc3-119">For more information, see [Declared accessibility](~/_csharplang/spec/basic-concepts.md#declared-accessibility) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="2cdc3-120">Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2cdc3-120">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="2cdc3-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="2cdc3-121">See also</span></span>

- [<span data-ttu-id="2cdc3-122">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2cdc3-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="2cdc3-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="2cdc3-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="2cdc3-124">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2cdc3-124">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="2cdc3-125">Modifikátory přístupu</span><span class="sxs-lookup"><span data-stu-id="2cdc3-125">Access Modifiers</span></span>](access-modifiers.md)
- [<span data-ttu-id="2cdc3-126">Úrovně přístupnosti</span><span class="sxs-lookup"><span data-stu-id="2cdc3-126">Accessibility Levels</span></span>](accessibility-levels.md)
- [<span data-ttu-id="2cdc3-127">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="2cdc3-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="2cdc3-128">public</span><span class="sxs-lookup"><span data-stu-id="2cdc3-128">public</span></span>](public.md)
- [<span data-ttu-id="2cdc3-129">private</span><span class="sxs-lookup"><span data-stu-id="2cdc3-129">private</span></span>](private.md)
- [<span data-ttu-id="2cdc3-130">internal</span><span class="sxs-lookup"><span data-stu-id="2cdc3-130">internal</span></span>](internal.md)
- <span data-ttu-id="2cdc3-131">[Problémy se zabezpečením pro interní virtuální klíčová slova](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="2cdc3-131">[Security concerns for internal virtual keywords](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/heyd8kky(v=vs.100))</span></span>
