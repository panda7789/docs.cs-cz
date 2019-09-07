---
title: přepis – modifikátor C# – referenční informace
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: bbdbcaf466e0b4dca4b78902ca9e7a49b02ac718
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394239"
---
# <a name="override-c-reference"></a><span data-ttu-id="55585-102">override (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="55585-102">override (C# Reference)</span></span>

<span data-ttu-id="55585-103">`override` Modifikátor je vyžadován pro rozšiřování nebo úpravu abstraktní nebo virtuální implementace zděděné metody, vlastnosti, indexeru nebo události.</span><span class="sxs-lookup"><span data-stu-id="55585-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="55585-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="55585-104">Example</span></span>

<span data-ttu-id="55585-105">V tomto příkladu `Square` třída musí poskytovat přepsanou implementaci, `GetArea` protože `GetArea` je zděděna z abstraktní `Shape` třídy:</span><span class="sxs-lookup"><span data-stu-id="55585-105">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="55585-106">`override` Metoda poskytuje novou implementaci člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="55585-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="55585-107">Metoda, která je přepsána `override` deklarací, je označována jako přepsaná základní metoda.</span><span class="sxs-lookup"><span data-stu-id="55585-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="55585-108">Přepsaná základní metoda musí mít stejnou signaturu jako `override` metoda.</span><span class="sxs-lookup"><span data-stu-id="55585-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="55585-109">Informace o dědičnosti naleznete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="55585-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="55585-110">Nemůžete přepsat nevirtuální nebo statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="55585-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="55585-111">Přepsaná základní metoda musí být `virtual`, `abstract`nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="55585-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="55585-112">Deklarace nemůže změnit přístupnost `virtual` metody. `override`</span><span class="sxs-lookup"><span data-stu-id="55585-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="55585-113">Metoda i metoda musí mít stejný [Modifikátor úrovně přístupu.](access-modifiers.md) `override` `virtual`</span><span class="sxs-lookup"><span data-stu-id="55585-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="55585-114">Nemůžete použít `new`modifikátory, `virtual` `static`nebo pro úpravu `override` metody.</span><span class="sxs-lookup"><span data-stu-id="55585-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="55585-115">Přepisující deklaraci vlastnosti musí jako zděděné vlastnosti zadat přesně stejný modifikátor přístupu, typ a název a přepsanou vlastnost musí být `virtual`, `abstract`nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="55585-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="55585-116">Další informace o použití `override` klíčového slova naleznete v tématu [Správa verzí pomocí klíčových slov override a New](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a znalost, [kdy použít klíčová slova override a New](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="55585-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="55585-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="55585-117">Example</span></span>

<span data-ttu-id="55585-118">Tento příklad definuje základní třídu s názvem `Employee`a odvozenou třídu s názvem `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="55585-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="55585-119">Třída obsahuje pole navíc, a přepisuje metodu `CalculatePay` , aby ji bylo možné vzít v úvahu. `salesbonus` `SalesEmployee`</span><span class="sxs-lookup"><span data-stu-id="55585-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="55585-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55585-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="55585-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55585-121">See also</span></span>

- [<span data-ttu-id="55585-122">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="55585-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="55585-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="55585-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="55585-124">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="55585-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="55585-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="55585-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="55585-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="55585-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="55585-127">abstract</span><span class="sxs-lookup"><span data-stu-id="55585-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="55585-128">virtual</span><span class="sxs-lookup"><span data-stu-id="55585-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="55585-129">New (modifikátor)</span><span class="sxs-lookup"><span data-stu-id="55585-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="55585-130">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="55585-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
