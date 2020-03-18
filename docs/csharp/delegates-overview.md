---
title: Úvod do delegátů
description: Další informace o delegátech v tomto tématu přehledu, který představuje základní koncepty a popisuje cíle návrhu jazyka pro delegáty.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: fd594f77c034533a1d5aee1d8279e9b727284311
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79146226"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="d3ffa-103">Úvod do delegátů</span><span class="sxs-lookup"><span data-stu-id="d3ffa-103">Introduction to Delegates</span></span>

<span data-ttu-id="d3ffa-104">Delegáti poskytují *mechanismus pozdní vazby* v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-104">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="d3ffa-105">Pozdní vazba znamená, že vytvoříte algoritmus, kde volající také poskytuje alespoň jednu metodu, která implementuje část algoritmu.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-105">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="d3ffa-106">Zvažte například seřazení seznamu hvězd v aplikaci astronomie.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-106">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="d3ffa-107">Můžete se rozhodnout třídit tyto hvězdy podle jejich vzdálenosti od Země, nebo velikosti hvězdy, nebo jejich vnímaný jas.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-107">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="d3ffa-108">Ve všech těchto případech Sort() metoda v podstatě totéž: uspořádá položky v seznamu na základě některých porovnání.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-108">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="d3ffa-109">Kód, který porovnává dvě hvězdičky se liší pro každé řazení řazení.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-109">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="d3ffa-110">Tyto druhy řešení byly použity v softwaru po dobu půl století.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-110">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="d3ffa-111">Koncept delegáta jazyka C# poskytuje prvotřídní jazykovou podporu a bezpečnost typů kolem konceptu.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-111">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="d3ffa-112">Jak uvidíte dále v této řadě, kód Jazyka C#, který napíšete pro algoritmy, jako je tento, je typově bezpečný a využívá jazyk a kompilátor k zajištění, že typy odpovídají argumentům a návratovým typům.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-112">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="d3ffa-113">Cíle jazykového návrhu pro delegáty</span><span class="sxs-lookup"><span data-stu-id="d3ffa-113">Language Design Goals for Delegates</span></span>

<span data-ttu-id="d3ffa-114">Návrháři jazyka vyjmenovalněkolik cílů pro funkci, která se nakonec stala delegáty.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-114">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="d3ffa-115">Tým chtěl společnou jazykovou konstrukci, která by mohla být použita pro všechny algoritmy pozdní vazby.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-115">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="d3ffa-116">To umožňuje vývojářům naučit se jeden koncept a používat stejný koncept v mnoha různých softwarových problémech.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-116">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="d3ffa-117">Za druhé, tým chtěl podporovat volání metod jednoho i vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-117">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="d3ffa-118">(Vícesměrové vysílání delegáti jsou delegáti, které řetěz dohromady více volání metody.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-118">(Multicast delegates are delegates that chain together multiple method calls.</span></span>
<span data-ttu-id="d3ffa-119">Příklady uvidíte [dále v této sérii](delegate-class.md).)</span><span class="sxs-lookup"><span data-stu-id="d3ffa-119">You'll see examples [later in this series](delegate-class.md).)</span></span>

<span data-ttu-id="d3ffa-120">Tým chtěl delegáty podporovat stejný typ bezpečnosti, které vývojáři očekávají od všech c# konstrukce.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-120">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span>

<span data-ttu-id="d3ffa-121">Nakonec tým rozpoznal, že vzor události je jeden konkrétní vzor, kde delegáti nebo jakýkoli algoritmus pozdní vazby je velmi užitečné.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-121">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="d3ffa-122">Tým chtěl zajistit, že kód pro delegáty může poskytnout základ pro vzor události .NET.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-122">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="d3ffa-123">Výsledkem všech těchto prací byla podpora delegáta a události v c# a .NET.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-123">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="d3ffa-124">Zbývající články v této části se bude týkat funkce jazyka, podporu knihovny a společné idiomy, které se používají při práci s delegáty.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-124">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="d3ffa-125">Dozvíte se o `delegate` klíčovéslovo a jaký kód generuje.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-125">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="d3ffa-126">Dozvíte se o funkcích `System.Delegate` ve třídě a o tom, jak se tyto funkce používají.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-126">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="d3ffa-127">Dozvíte se, jak vytvořit typ bezpečné delegáty a jak vytvořit metody, které lze vyvolat prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-127">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="d3ffa-128">Dozvíte se také, jak pracovat s delegáty a události pomocí Lambda výrazy.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-128">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="d3ffa-129">Uvidíte, kde delegáti stanou jedním ze stavebních bloků pro LINQ.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-129">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="d3ffa-130">Dozvíte se, jak delegáti jsou základem pro vzor události .NET a jak se liší.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-130">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="d3ffa-131">Celkově uvidíte, jak delegáti jsou nedílnou součástí programování v rozhraní .NET a práce s rozhraní API rozhraní API architektury.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-131">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="d3ffa-132">Pusťme se do toho.</span><span class="sxs-lookup"><span data-stu-id="d3ffa-132">Let's get started.</span></span>

[<span data-ttu-id="d3ffa-133">Další</span><span class="sxs-lookup"><span data-stu-id="d3ffa-133">Next</span></span>](delegate-class.md)
