---
title: Úvod do delegáti
description: Další informace o Delegáti v tomto tématu Přehled, který uvádí základní koncepty a popisuje cíle návrhu jazyk pro delegáti.
ms.date: 06/20/2016
ms.assetid: 59b61d77-84e5-457b-8da5-fb5f24ca6ed6
ms.openlocfilehash: d42d9d10aeaa153f12933fa3a59e58719f7741e7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33212184"
---
# <a name="introduction-to-delegates"></a><span data-ttu-id="101aa-103">Úvod do delegáti</span><span class="sxs-lookup"><span data-stu-id="101aa-103">Introduction to Delegates</span></span>

[<span data-ttu-id="101aa-104">Předchozí</span><span class="sxs-lookup"><span data-stu-id="101aa-104">Previous</span></span>](delegates-events.md)

<span data-ttu-id="101aa-105">Zadejte delegáti *pozdní vazby* mechanismus v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="101aa-105">Delegates provide a *late binding* mechanism in .NET.</span></span> <span data-ttu-id="101aa-106">Pozdní vazba znamená, že můžete vytvořit algoritmus kde volající také poskytuje alespoň jednu metodu, který implementuje část algoritmu.</span><span class="sxs-lookup"><span data-stu-id="101aa-106">Late Binding means that you create an algorithm where the caller also supplies at least one method that implements part of the algorithm.</span></span>

<span data-ttu-id="101aa-107">Představte si třeba řazení seznamu hvězdiček v aplikaci astronomii.</span><span class="sxs-lookup"><span data-stu-id="101aa-107">For example, consider sorting a list of stars in an astronomy application.</span></span>
<span data-ttu-id="101aa-108">Můžete řadit podle jejich vzdálenost od zemském povrchu, nebo odhad hvězdičkou nebo jejich dosahovaný také průraznost těchto hvězdiček.</span><span class="sxs-lookup"><span data-stu-id="101aa-108">You may choose to sort those stars by their distance from the earth, or the magnitude of the star, or their perceived brightness.</span></span>

<span data-ttu-id="101aa-109">V těchto případech metody Sort() provede v podstatě totéž: Uspořádá položky v seznamu na základě některé porovnání.</span><span class="sxs-lookup"><span data-stu-id="101aa-109">In all those cases, the Sort() method does essentially the same thing: arranges the items in the list based on some comparison.</span></span> <span data-ttu-id="101aa-110">Kód, který porovná dvě hvězdiček se liší pro jednotlivé pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="101aa-110">The code that compares two stars is different for each of the sort orderings.</span></span>

<span data-ttu-id="101aa-111">Tyto druhy řešení byly použity v softwaru pro poloviční století.</span><span class="sxs-lookup"><span data-stu-id="101aa-111">These kinds of solutions have been used in software for half a century.</span></span>
<span data-ttu-id="101aa-112">Koncept delegáta jazyka C# nabízí prvotřídní podporu a bezpečnost typů kolem koncept.</span><span class="sxs-lookup"><span data-stu-id="101aa-112">The C# language delegate concept provides first class language support, and type safety around the concept.</span></span>

<span data-ttu-id="101aa-113">Jak uvidíte dál v této série, napsaný pro algoritmy, jako je to kód C# je typově bezpečný a využívá jazyk a kompilátoru zajistit, že typy odpovídat argumenty a návratové typy.</span><span class="sxs-lookup"><span data-stu-id="101aa-113">As you'll see later in this series, the C# code you write for algorithms like this is type safe, and leverages the language and the compiler to ensure that the types match for arguments and return types.</span></span>

## <a name="language-design-goals-for-delegates"></a><span data-ttu-id="101aa-114">Cíle návrhu jazyk pro delegáti</span><span class="sxs-lookup"><span data-stu-id="101aa-114">Language Design Goals for Delegates</span></span>

<span data-ttu-id="101aa-115">Návrháři jazyk uvedené několik cíle pro funkci, nakonec se aktivovala delegáti.</span><span class="sxs-lookup"><span data-stu-id="101aa-115">The language designers enumerated several goals for the feature that eventually became delegates.</span></span>

<span data-ttu-id="101aa-116">Tým chtěli běžné konstrukce jazyk, které by mohly být použity žádné pozdní vazba algoritmy.</span><span class="sxs-lookup"><span data-stu-id="101aa-116">The team wanted a common language construct that could be used for any late binding algorithms.</span></span> <span data-ttu-id="101aa-117">Která umožňuje vývojářům další jeden koncept a použít tento stejný koncept napříč mnoha různých softwaru problémy.</span><span class="sxs-lookup"><span data-stu-id="101aa-117">That enables developers to learn one concept, and use that same concept across many different software problems.</span></span>

<span data-ttu-id="101aa-118">Druhý chtěli týmem pro podporu obou volání metody jednoho a vícesměrového vysílání.</span><span class="sxs-lookup"><span data-stu-id="101aa-118">Second, the team wanted to support both single and multi-cast method calls.</span></span> <span data-ttu-id="101aa-119">(Vícesměroví Delegáti jsou delegáti kde několik metod zřetězenými společně.</span><span class="sxs-lookup"><span data-stu-id="101aa-119">(Multicast delegates are delegates where multiple methods have been chained together.</span></span> <span data-ttu-id="101aa-120">Uvidíte příklady [dál v této série](delegate-class.md).</span><span class="sxs-lookup"><span data-stu-id="101aa-120">You'll see examples [later in this series](delegate-class.md).</span></span> 

<span data-ttu-id="101aa-121">Tým chtěli delegáty pro podporu stejné bezpečnost typů, které vývojáři očekávat od všech konstrukce jazyka C#.</span><span class="sxs-lookup"><span data-stu-id="101aa-121">The team wanted delegates to support the same type safety that developers expect from all C# constructs.</span></span> 

<span data-ttu-id="101aa-122">Nakonec týmem rozpoznat, že vzor událostí je jeden specifického vzoru kde delegáti nebo libovolný algoritmus pozdní vazba) je velmi užitečné.</span><span class="sxs-lookup"><span data-stu-id="101aa-122">Finally, the team recognized that an event pattern is one specific pattern where delegates, or any late binding algorithm) is very useful.</span></span> <span data-ttu-id="101aa-123">Tým chtěli Ujistěte se, že kód pro delegáti může být základem pro vzor událostí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="101aa-123">The team wanted to ensure that the code for delegates could provide the basis for the .NET event pattern.</span></span>

<span data-ttu-id="101aa-124">Výsledek všechno, co pracovní byla podpora delegáta a události v C# a rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="101aa-124">The result of all that work was the delegate and event support in C# and .NET.</span></span> <span data-ttu-id="101aa-125">Zbývající články v této části se věnují funkce jazyka, podpora knihovny a běžné idioms, které se používají při práci s delegáti.</span><span class="sxs-lookup"><span data-stu-id="101aa-125">The remaining articles in this section will cover the language features, the library support, and the common idioms that are used when you work with delegates.</span></span>

<span data-ttu-id="101aa-126">Získáte informace o `delegate` – klíčové slovo a co ho kódu generuje.</span><span class="sxs-lookup"><span data-stu-id="101aa-126">You'll learn about the `delegate` keyword and what code it generates.</span></span> <span data-ttu-id="101aa-127">Získáte informace o funkcích v `System.Delegate` třídy a jak se používají tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="101aa-127">You'll learn about the features in the `System.Delegate` class, and how those features are used.</span></span> <span data-ttu-id="101aa-128">Dozvíte se, jak vytvořit typ bezpečné Delegáti a postup vytvoření metody, které můžete vyvolat prostřednictvím delegáti.</span><span class="sxs-lookup"><span data-stu-id="101aa-128">You'll learn how to create type safe delegates, and how to create methods that can be invoked through delegates.</span></span> <span data-ttu-id="101aa-129">Budete také zjistěte, jak pracovat s Delegáti a události pomocí výrazů Lambda.</span><span class="sxs-lookup"><span data-stu-id="101aa-129">You'll also learn how to work with delegates and events by using Lambda expressions.</span></span> <span data-ttu-id="101aa-130">Uvidíte, kde delegáti stane jeden ze stavebních bloků pro výrazy LINQ.</span><span class="sxs-lookup"><span data-stu-id="101aa-130">You'll see where delegates become one of the building blocks for LINQ.</span></span> <span data-ttu-id="101aa-131">Dozvíte se, jak delegáti slouží jako základ pro vzor událostí rozhraní .NET a jak se liší.</span><span class="sxs-lookup"><span data-stu-id="101aa-131">You'll learn how delegates are the basis for the .NET event pattern, and how they are different.</span></span>

<span data-ttu-id="101aa-132">Celkově platí uvidíte, jak Delegáti jsou nedílnou součástí programování v rozhraní .NET a práci s rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="101aa-132">Overall, you'll see how delegates are an integral part of programming in .NET and working with the framework APIs.</span></span>

<span data-ttu-id="101aa-133">Můžeme začít.</span><span class="sxs-lookup"><span data-stu-id="101aa-133">Let's get started.</span></span>

[<span data-ttu-id="101aa-134">Next</span><span class="sxs-lookup"><span data-stu-id="101aa-134">Next</span></span>](delegate-class.md)
