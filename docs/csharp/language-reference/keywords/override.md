---
title: přepsání modifikátor - C# Reference
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: acad3aa3b196c184132ad1acdf52b18a799b0896
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713245"
---
# <a name="override-c-reference"></a><span data-ttu-id="ee0a2-102">override (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="ee0a2-102">override (C# Reference)</span></span>

<span data-ttu-id="ee0a2-103">Modifikátor `override` je nutné rozšířit nebo upravit abstraktní nebo virtuální implementaci zděděné metody, vlastnosti, indexeru nebo události.</span><span class="sxs-lookup"><span data-stu-id="ee0a2-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="ee0a2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee0a2-104">Example</span></span>

<span data-ttu-id="ee0a2-105">V `Square` tomto příkladu musí třída poskytnout `GetArea` potlačenou implementaci, protože `GetArea` je zděděna z abstraktní `Shape` třídy:</span><span class="sxs-lookup"><span data-stu-id="ee0a2-105">In this example, the `Square` class must provide an overridden implementation of `GetArea` because `GetArea` is inherited from the abstract `Shape` class:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="ee0a2-106">`override` Metoda poskytuje novou implementaci člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="ee0a2-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="ee0a2-107">Metoda, která je přepsána `override` deklarací, se označuje jako přepisovaná základní metoda.</span><span class="sxs-lookup"><span data-stu-id="ee0a2-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="ee0a2-108">Přepsána základní metoda musí mít `override` stejný podpis jako metoda.</span><span class="sxs-lookup"><span data-stu-id="ee0a2-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="ee0a2-109">Informace o dědičnosti naleznete v tématu [Dědičnost](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="ee0a2-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="ee0a2-110">Nelze přepsat nevirtuální nebo statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="ee0a2-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="ee0a2-111">Přepsání základní metody `virtual` `abstract`musí `override`být , , nebo .</span><span class="sxs-lookup"><span data-stu-id="ee0a2-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="ee0a2-112">Deklarace `override` nemůže změnit usnadnění `virtual` přístupu metody.</span><span class="sxs-lookup"><span data-stu-id="ee0a2-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="ee0a2-113">`override` Metoda i `virtual` metoda musí mít stejný [modifikátor úrovně přístupu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="ee0a2-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="ee0a2-114">Metodu `new` `static`nelze použít `virtual` pomocí modifikátorů , nebo modifikátorů. `override`</span><span class="sxs-lookup"><span data-stu-id="ee0a2-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="ee0a2-115">Deklarace vlastnosti overriding musí určit přesně stejný modifikátor přístupu, typ a název `virtual` `abstract`jako `override`zděděná vlastnost a přepsána vlastnost musí být , , nebo .</span><span class="sxs-lookup"><span data-stu-id="ee0a2-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="ee0a2-116">Další informace o použití `override` klíčového slova naleznete v [tématu Správa verzí s přepsáním a Nová klíčová slova](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a Informace o [tom, kdy použít přepsání a nová klíčová slova](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="ee0a2-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="ee0a2-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="ee0a2-117">Example</span></span>

<span data-ttu-id="ee0a2-118">Tento příklad definuje základní `Employee`třídu s názvem `SalesEmployee`a odvozenou třídu s názvem .</span><span class="sxs-lookup"><span data-stu-id="ee0a2-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="ee0a2-119">Třída `SalesEmployee` obsahuje další pole `salesbonus`, a přepíše metodu, `CalculatePay` aby se v úvahu.</span><span class="sxs-lookup"><span data-stu-id="ee0a2-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="ee0a2-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ee0a2-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="ee0a2-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="ee0a2-121">See also</span></span>

- [<span data-ttu-id="ee0a2-122">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ee0a2-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="ee0a2-123">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="ee0a2-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="ee0a2-124">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="ee0a2-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="ee0a2-125">C# Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="ee0a2-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="ee0a2-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="ee0a2-126">Modifiers</span></span>](index.md)
- [<span data-ttu-id="ee0a2-127">Abstraktní</span><span class="sxs-lookup"><span data-stu-id="ee0a2-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="ee0a2-128">virtual</span><span class="sxs-lookup"><span data-stu-id="ee0a2-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="ee0a2-129">nový (modifikátor)</span><span class="sxs-lookup"><span data-stu-id="ee0a2-129">new (modifier)</span></span>](new-modifier.md)
- [<span data-ttu-id="ee0a2-130">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="ee0a2-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
