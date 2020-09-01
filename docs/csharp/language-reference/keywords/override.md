---
description: override – modifikátor – reference jazyka C#
title: override – modifikátor – reference jazyka C#
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: 51ca806310214981b7ff24a796fe078d902dca4d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89134455"
---
# <a name="override-c-reference"></a><span data-ttu-id="1d50c-103">override (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1d50c-103">override (C# Reference)</span></span>

<span data-ttu-id="1d50c-104">`override`Modifikátor je vyžadován pro rozšiřování nebo úpravu abstraktní nebo virtuální implementace zděděné metody, vlastnosti, indexeru nebo události.</span><span class="sxs-lookup"><span data-stu-id="1d50c-104">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="1d50c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d50c-105">Example</span></span>

<span data-ttu-id="1d50c-106">V tomto příkladu `Square` Třída musí poskytovat přepsanou implementaci, `GetArea` protože `GetArea` je zděděna z abstraktní `Shape` třídy:</span><span class="sxs-lookup"><span data-stu-id="1d50c-106">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="1d50c-107">`override`Metoda poskytuje novou implementaci člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="1d50c-107">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="1d50c-108">Metoda, která je přepsána `override` deklarací, je označována jako přepsaná základní metoda.</span><span class="sxs-lookup"><span data-stu-id="1d50c-108">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="1d50c-109">Přepsaná základní metoda musí mít stejnou signaturu jako `override` metoda.</span><span class="sxs-lookup"><span data-stu-id="1d50c-109">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="1d50c-110">Informace o dědičnosti naleznete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="1d50c-110">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="1d50c-111">Nemůžete přepsat nevirtuální nebo statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="1d50c-111">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="1d50c-112">Přepsaná základní metoda musí být `virtual` , `abstract` nebo `override` .</span><span class="sxs-lookup"><span data-stu-id="1d50c-112">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="1d50c-113">`override`Deklarace nemůže změnit přístupnost `virtual` metody.</span><span class="sxs-lookup"><span data-stu-id="1d50c-113">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="1d50c-114">`override`Metoda i `virtual` Metoda musí mít stejný [Modifikátor úrovně přístupu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="1d50c-114">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="1d50c-115">Nemůžete použít `new` `static` `virtual` modifikátory, nebo pro úpravu `override` metody.</span><span class="sxs-lookup"><span data-stu-id="1d50c-115">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="1d50c-116">Přepisující deklaraci vlastnosti musí jako zděděné vlastnosti zadat přesně stejný modifikátor přístupu, typ a název a přepsanou vlastnost musí být `virtual` , `abstract` nebo `override` .</span><span class="sxs-lookup"><span data-stu-id="1d50c-116">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="1d50c-117">Další informace o použití `override` klíčového slova naleznete v tématu [Správa verzí pomocí klíčových slov override a New](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít klíčová slova override a New](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="1d50c-117">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="1d50c-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d50c-118">Example</span></span>

<span data-ttu-id="1d50c-119">Tento příklad definuje základní třídu s názvem `Employee` a odvozenou třídu s názvem `SalesEmployee` .</span><span class="sxs-lookup"><span data-stu-id="1d50c-119">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="1d50c-120">`SalesEmployee`Třída obsahuje pole navíc, `salesbonus` a přepisuje metodu, `CalculatePay` aby ji bylo možné vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="1d50c-120">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="1d50c-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1d50c-121">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="1d50c-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d50c-122">See also</span></span>

- [<span data-ttu-id="1d50c-123">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1d50c-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1d50c-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="1d50c-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1d50c-125">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="1d50c-125">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="1d50c-126">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1d50c-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1d50c-127">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="1d50c-127">Modifiers</span></span>](index.md)
- [<span data-ttu-id="1d50c-128">Výtah</span><span class="sxs-lookup"><span data-stu-id="1d50c-128">abstract</span></span>](abstract.md)
- [<span data-ttu-id="1d50c-129">virtual</span><span class="sxs-lookup"><span data-stu-id="1d50c-129">virtual</span></span>](virtual.md)
- [<span data-ttu-id="1d50c-130">New (modifikátor)</span><span class="sxs-lookup"><span data-stu-id="1d50c-130">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="1d50c-131">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="1d50c-131">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
