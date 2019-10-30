---
title: Úvod do delegátů
description: Přečtěte si o delegátech v tomto přehledovém tématu, které přináší základní koncepty a popisuje jazykové cíle návrhu pro delegáty.
ms.date: 06/20/2016
ms.technology: csharp-fundamentals
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: deff297ccce6cd14a7cd21c49638a9c6030a9996
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2019
ms.locfileid: "73037405"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="fde6c-103">Úvod do delegátů</span><span class="sxs-lookup"><span data-stu-id="fde6c-103">Introduction to Delegates</span></span>

<span data-ttu-id="fde6c-104">Delegáti poskytují v .NET mechanismus *pozdní vazby* .</span><span class="sxs-lookup"><span data-stu-id="fde6c-104">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="fde6c-105">Pozdní vazba znamená, že vytvoříte algoritmus, kde volající také dodá alespoň jednu metodu, která implementuje část algoritmu.</span><span class="sxs-lookup"><span data-stu-id="fde6c-105">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="fde6c-106">Zvažte například řazení seznamu hvězdiček v aplikaci astronomická aplikace.</span><span class="sxs-lookup"><span data-stu-id="fde6c-106">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="fde6c-107">Tyto hvězdy můžete seřadit podle jejich vzdálenosti od země nebo podle velikosti hvězdičky nebo jejich vypozorovaného jasu.</span><span class="sxs-lookup"><span data-stu-id="fde6c-107">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="fde6c-108">Ve všech těchto případech metoda sort () má v podstatě stejnou věc: Uspořádá položky v seznamu na základě nějakého porovnání.</span><span class="sxs-lookup"><span data-stu-id="fde6c-108">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="fde6c-109">Kód, který porovnává dvě hvězdičky, se liší pro každé pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="fde6c-109">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="fde6c-110">Tyto druhy řešení se používají v softwaru pro polovinu století.</span><span class="sxs-lookup"><span data-stu-id="fde6c-110">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="fde6c-111">Koncept C# delegáta jazyka poskytuje prvotřídní podporu pro jazyky a bezpečnost typů kolem konceptu.</span><span class="sxs-lookup"><span data-stu-id="fde6c-111">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="fde6c-112">Jak uvidíte později v této sérii, C# kód, který napíšete pro algoritmy jako je typově bezpečný, a využívá jazyk a kompilátor k zajištění shody typů pro argumenty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="fde6c-112">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="fde6c-113">Cíle návrhu jazyka pro delegáty</span><span class="sxs-lookup"><span data-stu-id="fde6c-113">Language Design Goals for Delegates</span></span>

<span data-ttu-id="fde6c-114">Návrháři jazyka vyčíslují několik cílů pro funkci, která se nakonec stala delegáty.</span><span class="sxs-lookup"><span data-stu-id="fde6c-114">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="fde6c-115">Tým chtěl, aby se vytvořila společná jazyková konstrukce, která by se dala použít pro všechny algoritmy s pozdní vazbou.</span><span class="sxs-lookup"><span data-stu-id="fde6c-115">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="fde6c-116">To umožňuje vývojářům naučit se jeden koncept a stejný koncept používat v mnoha různých problémech se softwarem.</span><span class="sxs-lookup"><span data-stu-id="fde6c-116">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="fde6c-117">Za druhé tým chtěl podporovat volání metody Single i Multicast.</span><span class="sxs-lookup"><span data-stu-id="fde6c-117">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="fde6c-118">(Delegáti vícesměrového vysílání jsou delegáti, kteří zřetězit dohromady více volání metody.</span><span class="sxs-lookup"><span data-stu-id="fde6c-118">(Multicast delegates are delegates that chain together multiple method calls.</span></span> <span data-ttu-id="fde6c-119">[V této sérii](delegate-class.md)uvidíte příklady později.)</span><span class="sxs-lookup"><span data-stu-id="fde6c-119">You'll see examples [later in this series](delegate-class.md).)</span></span> 

<span data-ttu-id="fde6c-120">Tým chtěl, aby podporoval stejnou bezpečnost typů, kterou vývojáři očekávají ze všech C# konstrukcí.</span><span class="sxs-lookup"><span data-stu-id="fde6c-120">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="fde6c-121">Nakonec tým rozpoznal, že vzor události je jeden konkrétní vzor, ve kterém jsou delegáti nebo jakékoli pozdní vazby algoritmu velmi užitečné.</span><span class="sxs-lookup"><span data-stu-id="fde6c-121">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="fde6c-122">Tým chtěl zajistit, aby kód pro delegáty mohl poskytnout základ pro vzor události .NET.</span><span class="sxs-lookup"><span data-stu-id="fde6c-122">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="fde6c-123">Výsledek všechny této práce byl delegát a podpora událostí v C# a .NET.</span><span class="sxs-lookup"><span data-stu-id="fde6c-123">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="fde6c-124">Zbývající články v této části se týkají funkcí jazyka, podpory knihoven a běžných idiomy, které se používají při práci s delegáty.</span><span class="sxs-lookup"><span data-stu-id="fde6c-124">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="fde6c-125">Dozvíte se o klíčovém slově `delegate` a o tom, jaký kód generuje.</span><span class="sxs-lookup"><span data-stu-id="fde6c-125">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="fde6c-126">Dozvíte se o funkcích ve třídě `System.Delegate` a o tom, jak se tyto funkce používají.</span><span class="sxs-lookup"><span data-stu-id="fde6c-126">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="fde6c-127">Naučíte se, jak vytvořit typy bezpečných delegátů a jak vytvořit metody, které mohou být vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="fde6c-127">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="fde6c-128">Naučíte se také, jak pracovat s delegáty a událostmi pomocí výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="fde6c-128">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="fde6c-129">Uvidíte, kde se delegáti stanou jedním ze stavebních bloků pro LINQ.</span><span class="sxs-lookup"><span data-stu-id="fde6c-129">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="fde6c-130">Dozvíte se, jak jsou delegáti základem pro vzorec události .NET a jak se liší.</span><span class="sxs-lookup"><span data-stu-id="fde6c-130">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="fde6c-131">Celkově vidíte, jak jsou delegáti nedílnou součástí programování v rozhraní .NET a pracují s rozhraními API rozhraní Framework.</span><span class="sxs-lookup"><span data-stu-id="fde6c-131">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="fde6c-132">Pojďme začít.</span><span class="sxs-lookup"><span data-stu-id="fde6c-132">Let's get started.</span></span>

[<span data-ttu-id="fde6c-133">Next</span><span class="sxs-lookup"><span data-stu-id="fde6c-133">Next</span></span>](delegate-class.md)
