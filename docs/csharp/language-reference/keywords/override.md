---
title: Přepsat modifikátor (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- override
- override_CSharpKeyword
helpviewer_keywords:
- override keyword [C#]
ms.assetid: dd1907a8-acf8-46d3-80b9-c2ca4febada8
ms.openlocfilehash: cbd5e21e7ca71a4986099a0386c684a6db37c3e8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187004"
---
# <a name="override-c-reference"></a><span data-ttu-id="be2ba-102">override (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="be2ba-102">override (C# Reference)</span></span>

<span data-ttu-id="be2ba-103">`override` Modifikátor je potřeba rozšířit nebo upravit abstraktní nebo virtuální provádění zděděné metody, vlastnosti, indexeru nebo události.</span><span class="sxs-lookup"><span data-stu-id="be2ba-103">The `override` modifier is required to extend or modify the abstract or virtual implementation of an inherited method, property, indexer, or event.</span></span>

## <a name="example"></a><span data-ttu-id="be2ba-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="be2ba-104">Example</span></span>

<span data-ttu-id="be2ba-105">V tomto příkladu `Square` třída musí poskytovat implementaci přepsané `Area` protože `Area` se dědí z abstraktní `ShapesClass`:</span><span class="sxs-lookup"><span data-stu-id="be2ba-105">In this example, the `Square` class must provide an overridden implementation of `Area` because `Area` is inherited from the abstract `ShapesClass`:</span></span>

[!code-csharp[csrefKeywordsModifiers#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#1)]

<span data-ttu-id="be2ba-106">`override` Metody poskytuje novou implementaci člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="be2ba-106">An `override` method provides a new implementation of a member that is inherited from a base class.</span></span> <span data-ttu-id="be2ba-107">Metoda, která je přepsána `override` prohlášení je označován jako přepsané základní metodě.</span><span class="sxs-lookup"><span data-stu-id="be2ba-107">The method that is overridden by an `override` declaration is known as the overridden base method.</span></span> <span data-ttu-id="be2ba-108">Přepsané základní metoda musí mít stejný podpis jako `override` metody.</span><span class="sxs-lookup"><span data-stu-id="be2ba-108">The overridden base method must have the same signature as the `override` method.</span></span> <span data-ttu-id="be2ba-109">Informace o dědičnosti, naleznete v tématu [dědičnosti](../../programming-guide/classes-and-structs/inheritance.md).</span><span class="sxs-lookup"><span data-stu-id="be2ba-109">For information about inheritance, see [Inheritance](../../programming-guide/classes-and-structs/inheritance.md).</span></span>

<span data-ttu-id="be2ba-110">Nevirtuální nebo statické metody nelze přepsat.</span><span class="sxs-lookup"><span data-stu-id="be2ba-110">You cannot override a non-virtual or static method.</span></span> <span data-ttu-id="be2ba-111">Přepsané základní metoda musí být `virtual`, `abstract`, nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="be2ba-111">The overridden base method must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="be2ba-112">`override` Deklarace nemůže změnit přístupnost `virtual` metody.</span><span class="sxs-lookup"><span data-stu-id="be2ba-112">An `override` declaration cannot change the accessibility of the `virtual` method.</span></span> <span data-ttu-id="be2ba-113">Obě `override` metoda a `virtual` metoda musí mít stejný [úrovně modifikátor přístupu](access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="be2ba-113">Both the `override` method and the `virtual` method must have the same [access level modifier](access-modifiers.md).</span></span>

<span data-ttu-id="be2ba-114">Nelze použít `new`, `static`, nebo `virtual` modifikátory upravit `override` metody.</span><span class="sxs-lookup"><span data-stu-id="be2ba-114">You cannot use the `new`, `static`, or `virtual` modifiers to modify an `override` method.</span></span>

<span data-ttu-id="be2ba-115">Přepsání deklarace vlastnost musíte zadat přesně stejné modifikátor přístupu, typ a název jako zděděné vlastnosti a musí být přepsané vlastnosti `virtual`, `abstract`, nebo `override`.</span><span class="sxs-lookup"><span data-stu-id="be2ba-115">An overriding property declaration must specify exactly the same access modifier, type, and name as the inherited property, and the overridden property must be `virtual`, `abstract`, or `override`.</span></span>

<span data-ttu-id="be2ba-116">Další informace o tom, jak používat `override` – klíčové slovo, naleznete v tématu [Správa verzí pomocí nových klíčových slov Override a](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) a [znalost, kdy použít nová klíčová slova Override a](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span><span class="sxs-lookup"><span data-stu-id="be2ba-116">For more information about how to use the `override` keyword, see [Versioning with the Override and New Keywords](../../programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md) and [Knowing when to use Override and New Keywords](../../programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md).</span></span>

## <a name="example"></a><span data-ttu-id="be2ba-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="be2ba-117">Example</span></span>

<span data-ttu-id="be2ba-118">Tento příklad definuje základní třídu s názvem `Employee`a odvozená třída s názvem `SalesEmployee`.</span><span class="sxs-lookup"><span data-stu-id="be2ba-118">This example defines a base class named `Employee`, and a derived class named `SalesEmployee`.</span></span> <span data-ttu-id="be2ba-119">`SalesEmployee` Třída zahrnuje další pole, `salesbonus`a přepíše metodu `CalculatePay` aby vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="be2ba-119">The `SalesEmployee` class includes an extra field, `salesbonus`, and overrides the method `CalculatePay` in order to take it into account.</span></span>

[!code-csharp[csrefKeywordsModifiers#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="be2ba-120">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be2ba-120">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="be2ba-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="be2ba-121">See also</span></span>

- [<span data-ttu-id="be2ba-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be2ba-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="be2ba-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="be2ba-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="be2ba-124">Dědičnost</span><span class="sxs-lookup"><span data-stu-id="be2ba-124">Inheritance</span></span>](../../programming-guide/classes-and-structs/inheritance.md)
- [<span data-ttu-id="be2ba-125">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be2ba-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="be2ba-126">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="be2ba-126">Modifiers</span></span>](modifiers.md)
- [<span data-ttu-id="be2ba-127">abstract</span><span class="sxs-lookup"><span data-stu-id="be2ba-127">abstract</span></span>](abstract.md)
- [<span data-ttu-id="be2ba-128">virtual</span><span class="sxs-lookup"><span data-stu-id="be2ba-128">virtual</span></span>](virtual.md)
- [<span data-ttu-id="be2ba-129">new</span><span class="sxs-lookup"><span data-stu-id="be2ba-129">new</span></span>](new.md)
- [<span data-ttu-id="be2ba-130">Polymorfismus</span><span class="sxs-lookup"><span data-stu-id="be2ba-130">Polymorphism</span></span>](../../programming-guide/classes-and-structs/polymorphism.md)
