---
title: "Úvod do delegáti"
description: "Další informace o Delegáti v tomto tématu Přehled, který uvádí základní koncepty a popisuje cíle návrhu jazyk pro delegáti."
keywords: "Rozhraní .NET, .NET core"
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: dd4c68fb4f960d0c2d5cbdc9e699650070cacaf1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="2bd93-104">Úvod do delegáti</span><span class="sxs-lookup"><span data-stu-id="2bd93-104">Introduction to Delegates</span></span>

[<span data-ttu-id="2bd93-105">Předchozí</span><span class="sxs-lookup"><span data-stu-id="2bd93-105">Previous</span></span>](delegates-events.md)

<span data-ttu-id="2bd93-106">Zadejte delegáti *pozdní vazby* mechanismus v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2bd93-106">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="2bd93-107">Pozdní vazba znamená, že můžete vytvořit algoritmus kde volající také poskytuje alespoň jednu metodu, který implementuje část algoritmu.</span><span class="sxs-lookup"><span data-stu-id="2bd93-107">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="2bd93-108">Představte si třeba řazení seznamu hvězdiček v aplikaci astronomii.</span><span class="sxs-lookup"><span data-stu-id="2bd93-108">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="2bd93-109">Můžete řadit podle jejich vzdálenost od zemském povrchu, nebo odhad hvězdičkou nebo jejich dosahovaný také průraznost těchto hvězdiček.</span><span class="sxs-lookup"><span data-stu-id="2bd93-109">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="2bd93-110">V těchto případech metody Sort() provede v podstatě totéž: Uspořádá položky v seznamu na základě některé porovnání.</span><span class="sxs-lookup"><span data-stu-id="2bd93-110">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="2bd93-111">Kód, který porovná dvě hvězdiček se liší pro jednotlivé pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="2bd93-111">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="2bd93-112">Tyto druhy řešení byly použity v softwaru pro poloviční století.</span><span class="sxs-lookup"><span data-stu-id="2bd93-112">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="2bd93-113">Koncept delegáta jazyka C# nabízí prvotřídní podporu a bezpečnost typů kolem koncept.</span><span class="sxs-lookup"><span data-stu-id="2bd93-113">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="2bd93-114">Jak uvidíte dál v této série, napsaný pro algoritmy, jako je to kód C# je typově bezpečný a využívá jazyk a kompilátoru zajistit, že typy odpovídat argumenty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="2bd93-114">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="2bd93-115">Cíle návrhu jazyk pro delegáti</span><span class="sxs-lookup"><span data-stu-id="2bd93-115">Language Design Goals for Delegates</span></span>

<span data-ttu-id="2bd93-116">Návrháři jazyk uvedené několik cíle pro funkci, nakonec se aktivovala delegáti.</span><span class="sxs-lookup"><span data-stu-id="2bd93-116">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="2bd93-117">Tým chtěli běžné konstrukce jazyk, které by mohly být použity žádné pozdní vazba algoritmy.</span><span class="sxs-lookup"><span data-stu-id="2bd93-117">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="2bd93-118">Která umožňuje vývojářům další jeden koncept a použít tento stejný koncept napříč mnoha různých softwaru problémy.</span><span class="sxs-lookup"><span data-stu-id="2bd93-118">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="2bd93-119">Druhý chtěli týmem pro podporu obou volání metody jednoho a vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="2bd93-119">Second, the team wanted to support both single and multi-cast method calls.</span></span> <span data-ttu-id="2bd93-120">(Vícesměroví Delegáti jsou delegáti kde několik metod zřetězenými společně.</span><span class="sxs-lookup"><span data-stu-id="2bd93-120">(Multicast delegates are delegates where multiple methods have been chained together.</span></span> <span data-ttu-id="2bd93-121">Uvidíte příklady [dál v této série](delegate-class.md).</span><span class="sxs-lookup"><span data-stu-id="2bd93-121">You'll see examples [later in this series](delegate-class.md).</span></span> 

<span data-ttu-id="2bd93-122">Tým chtěli delegáty pro podporu stejné bezpečnost typů, které vývojáři očekávat od všech konstrukce jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="2bd93-122">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="2bd93-123">Nakonec týmem rozpoznat, že vzor událostí je jeden specifického vzoru kde delegáti nebo libovolný algoritmus pozdní vazba) je velmi užitečné.</span><span class="sxs-lookup"><span data-stu-id="2bd93-123">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm) is very useful.</span></span> <span data-ttu-id="2bd93-124">Tým chtěli Ujistěte se, že kód pro delegáti může být základem pro vzor událostí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2bd93-124">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="2bd93-125">Výsledek všechno, co pracovní byla podpora delegáta a události v C# a rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="2bd93-125">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="2bd93-126">Zbývající články v této části se věnují funkce jazyka, podpora knihovny a běžné idioms, které se používají při práci s delegáti.</span><span class="sxs-lookup"><span data-stu-id="2bd93-126">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="2bd93-127">Získáte informace o `delegate` – klíčové slovo a co ho kódu generuje.</span><span class="sxs-lookup"><span data-stu-id="2bd93-127">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="2bd93-128">Získáte informace o funkcích v `System.Delegate` třídy a jak se používají tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="2bd93-128">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="2bd93-129">Dozvíte se, jak vytvořit typ bezpečné Delegáti a postup vytvoření metody, které můžete vyvolat prostřednictvím delegáti.</span><span class="sxs-lookup"><span data-stu-id="2bd93-129">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="2bd93-130">Budete také zjistěte, jak pracovat s Delegáti a události pomocí výrazů Lambda.</span><span class="sxs-lookup"><span data-stu-id="2bd93-130">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="2bd93-131">Uvidíte, kde delegáti stane jeden ze stavebních bloků pro výrazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="2bd93-131">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="2bd93-132">Dozvíte se, jak delegáti slouží jako základ pro vzor událostí rozhraní .NET a jak se liší.</span><span class="sxs-lookup"><span data-stu-id="2bd93-132">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="2bd93-133">Celkově platí uvidíte, jak Delegáti jsou nedílnou součástí programování v rozhraní .NET a práci s rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="2bd93-133">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="2bd93-134">Můžeme začít.</span><span class="sxs-lookup"><span data-stu-id="2bd93-134">Let's get started.</span></span>

[<span data-ttu-id="2bd93-135">Další</span><span class="sxs-lookup"><span data-stu-id="2bd93-135">Next</span></span>](delegate-class.md)
