---
title: Úvod do delegátů
description: Další informace o delegátech v tomto úvodním tématu, který představuje základní koncepty a popisuje cíle návrhu jazyk pro delegáty.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: 43cdf9345f0bae9d5c4d0e6a31d80bc269c37fec
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65879033"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="10b1e-103">Úvod do delegátů</span><span class="sxs-lookup"><span data-stu-id="10b1e-103">Introduction to Delegates</span></span>

<span data-ttu-id="10b1e-104">Delegáti poskytují *pozdní vazby* mechanismus v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="10b1e-104">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="10b1e-105">Pozdní vazby znamená, že vytvoříte algoritmus kde volající také poskytuje alespoň jednu metodu, která implementuje část algoritmus.</span><span class="sxs-lookup"><span data-stu-id="10b1e-105">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="10b1e-106">Představte si třeba seznam hvězdiček v aplikaci astronomii řazení.</span><span class="sxs-lookup"><span data-stu-id="10b1e-106">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="10b1e-107">Můžete seřadit tyto hvězdiček podle jejich vzdálenost od země nebo velikost na hvězdičku nebo jejich vnímaná jasu.</span><span class="sxs-lookup"><span data-stu-id="10b1e-107">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="10b1e-108">V těchto případech se metoda Sort() provede v podstatě totéž: Uspořádá položky v seznamu na základě některých porovnání.</span><span class="sxs-lookup"><span data-stu-id="10b1e-108">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="10b1e-109">Kód, který porovná dvě hvězdičky se liší pro každý z pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="10b1e-109">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="10b1e-110">Tyto druhy řešení se používají v softwaru pro polovinu století.</span><span class="sxs-lookup"><span data-stu-id="10b1e-110">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="10b1e-111">C# Konceptu jazyka delegáta poskytuje prvotřídní podporu a bezpečnost typů kolem koncepce.</span><span class="sxs-lookup"><span data-stu-id="10b1e-111">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="10b1e-112">Jak uvidíte později v tomto seriálu C# kód, který píšete pro algoritmy, jako to je typově bezpečný a využívá jazyk, a kompilátor zajistíte, že typy odpovídají pro argumenty a vrátí typy.</span><span class="sxs-lookup"><span data-stu-id="10b1e-112">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="10b1e-113">Cíle návrhu jazyk pro delegáty</span><span class="sxs-lookup"><span data-stu-id="10b1e-113">Language Design Goals for Delegates</span></span>

<span data-ttu-id="10b1e-114">Návrháři jazyka Výčtový několik cílů pro funkci, která se nakonec začal být delegáti.</span><span class="sxs-lookup"><span data-stu-id="10b1e-114">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="10b1e-115">Tým chtěla při podpoře běžné konstrukce jazyka, která se dá použít pro jakékoli pozdní vazby algoritmů.</span><span class="sxs-lookup"><span data-stu-id="10b1e-115">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="10b1e-116">Který umožňuje vývojářům další jeden koncept a použijte tento stejný koncept napříč řadou různých softwarových problémů.</span><span class="sxs-lookup"><span data-stu-id="10b1e-116">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="10b1e-117">Za druhé tým chtěli podporu obou volání metody single a vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="10b1e-117">Second, the team wanted to support both single and multicast method calls.</span></span> <span data-ttu-id="10b1e-118">(Vícesměroví Delegáti jsou delegáty, kteří zřetězit více volání metody.</span><span class="sxs-lookup"><span data-stu-id="10b1e-118">(Multicast delegates are delegates that chain together multiple method calls.</span></span> <span data-ttu-id="10b1e-119">Zobrazí se vám příklady [dále v této sérii](delegate-class.md).)</span><span class="sxs-lookup"><span data-stu-id="10b1e-119">You'll see examples [later in this series](delegate-class.md).)</span></span> 

<span data-ttu-id="10b1e-120">Tým chtěla delegáty pro podporu stejné bezpečnost typů, který vývojářům ze všech C# vytvoří.</span><span class="sxs-lookup"><span data-stu-id="10b1e-120">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="10b1e-121">Nakonec tým rozpoznat, že vzor události je jeden konkrétní vzor, kde je velmi užitečné delegáty nebo libovolný algoritmus pozdní vazbu.</span><span class="sxs-lookup"><span data-stu-id="10b1e-121">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm, is very useful.</span></span> <span data-ttu-id="10b1e-122">Tým chtěli Ujistěte se, že kód pro delegáty, může být základem pro vzor události .NET.</span><span class="sxs-lookup"><span data-stu-id="10b1e-122">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="10b1e-123">Výsledek všechnu tu práci byla podpora delegátů a událostí v C# a .NET.</span><span class="sxs-lookup"><span data-stu-id="10b1e-123">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="10b1e-124">Zbývající články v této části probereme funkce jazyka, podpora knihovny a společné idiomy, které se používají při práci s delegátů.</span><span class="sxs-lookup"><span data-stu-id="10b1e-124">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="10b1e-125">Seznámí vás `delegate` – klíčové slovo a co kódu generuje.</span><span class="sxs-lookup"><span data-stu-id="10b1e-125">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="10b1e-126">Se dozvíte o funkcích `System.Delegate` třídy a jak se používají tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="10b1e-126">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="10b1e-127">Dozvíte se, jak vytvořit typ bezpečné delegáty a vytvoření metody, které mohou být vyvolány prostřednictvím delegátů.</span><span class="sxs-lookup"><span data-stu-id="10b1e-127">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="10b1e-128">Budete se také dozvíte, jak pracovat s Delegáti a události pomocí výrazů Lambda.</span><span class="sxs-lookup"><span data-stu-id="10b1e-128">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="10b1e-129">Uvidíte, kde delegáti stal jednou z stavební bloky pro funkci LINQ.</span><span class="sxs-lookup"><span data-stu-id="10b1e-129">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="10b1e-130">Dozvíte se, jak Delegáti jsou základem pro vzor události .NET a jak se liší.</span><span class="sxs-lookup"><span data-stu-id="10b1e-130">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="10b1e-131">Celkově uvidíte, jak Delegáti jsou nedílnou součástí programování v rozhraní .NET a používání rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="10b1e-131">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="10b1e-132">Pusťme se do práce.</span><span class="sxs-lookup"><span data-stu-id="10b1e-132">Let's get started.</span></span>

[<span data-ttu-id="10b1e-133">Next</span><span class="sxs-lookup"><span data-stu-id="10b1e-133">Next</span></span>](delegate-class.md)
