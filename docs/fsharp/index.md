---
title: Průvodce jazykem F#
description: 'Tato příručka poskytuje přehled o různých studijních materiálů F # je funkční programovací jazyk, který běží na rozhraní .NET.'
author: jackfoxy
ms.author: phcart
ms.date: 03/19/2018
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: ea27fb37-dad1-4bd4-a3cc-4f5c70767ae9
ms.openlocfilehash: a101233f396368c0bc25937c49f77699cb9f8cf2
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2018
---
# <a name="f-guide"></a><span data-ttu-id="ac9ae-103">Průvodce jazykem F#</span><span class="sxs-lookup"><span data-stu-id="ac9ae-103">F# Guide</span></span>

<span data-ttu-id="ac9ae-104">F # je funkční programovací jazyk, který běží na rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-104">F# is a functional programming language that runs on .NET.</span></span> <span data-ttu-id="ac9ae-105">Je také plnou podporu pro objekty, že vám dovolí blend funkční a objekt programování pro protokol řešení jakýkoli problém.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-105">It also has full support for objects, letting you blend functional and object programming for pragmatic solutions to any problem.</span></span>

```fsharp
open System // Get access to functionality in System namespace.

// Function: takes a name and produces a greeting.
let getGreeting name =
    sprintf "Hello, %s! Isn't F# great?" name

// Use the EntryPoint attribute to run the program.
[<EntryPoint>]
let main args =
    // Define a list of names
    let names = [| "Don"; "Julia"; "Xi" |]
    
    // Print a fun greeting for each name!
    names
    |> Array.map getGreeting
    |> Array.iter (fun greeting -> printfn "%s" greeting)

    0
```

<span data-ttu-id="ac9ae-106">F # je o produktivitu svou podstatou.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-106">F# is about productivity at its heart.</span></span> <span data-ttu-id="ac9ae-107">Podpora nástrojů pro F # je všudypřítomná a úplné pokročilých funkcí.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-107">The tooling support for F# is ubiquitous and full of advanced features.</span></span>

## <a name="learning-f"></a><span data-ttu-id="ac9ae-108">Learning F #</span><span class="sxs-lookup"><span data-stu-id="ac9ae-108">Learning F#</span></span> #

<span data-ttu-id="ac9ae-109">[Prohlídka F #](tour.md) shrnovat hlavní jazykové funkce s mnoha ukázek kódu.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-109">[Tour of F#](tour.md) gives an overview of major language features with lots of code samples.</span></span> <span data-ttu-id="ac9ae-110">To se doporučuje, když jste nový F # a chcete se podívat, jak jazyk funguje.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-110">This is recommended if you are new to F# and want to get a feel for how the language works.</span></span>

<span data-ttu-id="ac9ae-111">[Začínáme s F # v sadě Visual Studio](get-started/get-started-visual-studio.md) Pokud jste v systému Windows a chcete úplné prostředí Visual Studio IDE (Integraded Development Environment).</span><span class="sxs-lookup"><span data-stu-id="ac9ae-111">[Get started with F# in Visual Studio](get-started/get-started-visual-studio.md) if you're on Windows and want the full Visual Studio IDE (Integraded Development Environment) experience.</span></span>

<span data-ttu-id="ac9ae-112">[Začínáme s F # v sadě Visual Studio pro Mac](get-started/get-started-with-visual-studio-for-mac.md) Pokud jste v systému macOS a chcete použít Visual Studio IDE.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-112">[Get started with F# in Visual Studio for Mac](get-started/get-started-with-visual-studio-for-mac.md) if you're on macOS and want to use a Visual Studio IDE.</span></span>

<span data-ttu-id="ac9ae-113">[Začínáme s F # ve Visual Studio Code](get-started/get-started-vscode.md) Pokud chcete, aby lightweight, napříč platformami a prostředí IDE mnoha funkcemi.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-113">[Get Started with F# in Visual Studio Code](get-started/get-started-vscode.md) if you want a lightweight, cross-platform, and feature-packed IDE experience.</span></span>

<span data-ttu-id="ac9ae-114">[Začínáme s F # pomocí rozhraní příkazového řádku .NET Core](get-started/get-started-command-line.md) Pokud chcete pomocí nástroje příkazového řádku.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-114">[Get started with F# with the .NET Core CLI](get-started/get-started-command-line.md) if you want to use command-line tools.</span></span>

<span data-ttu-id="ac9ae-115">[Začínáme s F # a Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) pro mobilní programování s F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-115">[Get started with F# and Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) for mobile programming with F#.</span></span>

## <a name="references"></a><span data-ttu-id="ac9ae-116">Odkazy</span><span class="sxs-lookup"><span data-stu-id="ac9ae-116">References</span></span>

<span data-ttu-id="ac9ae-117">[Referenční dokumentace jazyka F #](language-reference/index.md) je odkaz na oficiální, komplexní pro všechny funkce jazyka F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-117">[F# Language Reference](language-reference/index.md) is the official, comprehensive reference for all F# language features.</span></span> <span data-ttu-id="ac9ae-118">Každý článek vysvětluje syntaxe a zobrazuje ukázky kódu.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-118">Each article explains the syntax and shows code samples.</span></span> <span data-ttu-id="ac9ae-119">Na panelu filtru v obsahu slouží k vyhledání konkrétní článků.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-119">You can use the filter bar in the table of contents to find specific articles.</span></span>

<span data-ttu-id="ac9ae-120">[F # referenční dokumentace hlavní knihovny](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) je referenční dokumentace rozhraní API pro základní knihovny F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-120">[F# Core Library Reference](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) is the API reference for the F# Core Library.</span></span>


## <a name="additional-guides"></a><span data-ttu-id="ac9ae-121">Další příručky</span><span class="sxs-lookup"><span data-stu-id="ac9ae-121">Additional guides</span></span>

<span data-ttu-id="ac9ae-122">[F # pro Fun a zisku](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) je komplexní a velmi podrobné adresáře na učení F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-122">[F# for Fun and Profit](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) is a comprehensive and very detailed book on learning F#.</span></span> <span data-ttu-id="ac9ae-123">Jeho obsah a Autor jsou milého komunitou F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-123">Its contents and author are beloved by the F# community.</span></span> <span data-ttu-id="ac9ae-124">Cílové skupiny je primárně vývojářům objektově orientované programování pozadí.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-124">The target audience is primarily developers with an object oriented programming background.</span></span>

<span data-ttu-id="ac9ae-125">[Programování Wikibook F #](https://en.wikibooks.org/wiki/F_Sharp_Programming) je wikibook o učení F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-125">[F# Programming Wikibook](https://en.wikibooks.org/wiki/F_Sharp_Programming) is a wikibook about learning F#.</span></span> <span data-ttu-id="ac9ae-126">Je také produktu komunity F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-126">It is also a product of the F# community.</span></span> <span data-ttu-id="ac9ae-127">Cílové skupiny je lidí, kteří jsou nové pro F #, s chvilku objektově orientované programování pozadí.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-127">The target audience is people who are new to F#, with a little bit of object oriented programming background.</span></span>

## <a name="learn-f-through-videos"></a><span data-ttu-id="ac9ae-128">Další informace F # prostřednictvím videa</span><span class="sxs-lookup"><span data-stu-id="ac9ae-128">Learn F# through videos</span></span>

<span data-ttu-id="ac9ae-129">[F # – tutoriál na YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) je skvělým Úvod do F # pomocí sady Visual Studio, zobrazuje v průběhu 1,5 hodiny velké množství skvělé příklady.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-129">[F# tutorial on YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) is a great introduction to F# using Visual Studio, showing lots of great examples over the course of 1.5 hours.</span></span> <span data-ttu-id="ac9ae-130">Cílové skupiny je Visual Studio vývojáře, kteří jsou nové F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-130">The target audience is Visual Studio developers who are new to F#.</span></span>

<span data-ttu-id="ac9ae-131">[Úvod do programování s F #](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) je skvělým video série, která používá Visual Studio Code jako hlavní editoru.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-131">[Introduction to Programming with F#](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) is a great video series that uses Visual Studio Code as the main editor.</span></span> <span data-ttu-id="ac9ae-132">Série videí začne nic a končí vytváření video hře RPG založený na textu.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-132">The video series starts from nothing and ends with building a text-based RPG video game.</span></span> <span data-ttu-id="ac9ae-133">Cílové skupiny je vývojáře, kteří raději Visual Studio Code (nebo lightweight IDE) a nový F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-133">The target audience is developers who prefer Visual Studio Code (or a lightweight IDE) and are new to F#.</span></span>

<span data-ttu-id="ac9ae-134">[Co je nového ve Visual Studio 2017 vývojářům F # pro](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) je video kurzu, které jsou uvedeny některé nové funkce pro F # v Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-134">[What's New in Visual Studio 2017 for F# For Developers](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) is a video course that shows some of the newer features for F# in Visual Studio 2017.</span></span> <span data-ttu-id="ac9ae-135">Cílové skupiny je Visual Studio vývojáře, kteří jsou nové F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-135">The target audience is Visual Studio developers who are new to F#.</span></span>

## <a name="other-useful-resources"></a><span data-ttu-id="ac9ae-136">Další užitečné zdroje</span><span class="sxs-lookup"><span data-stu-id="ac9ae-136">Other useful resources</span></span>

<span data-ttu-id="ac9ae-137">[F # fragmenty webu](http://www.fssnip.net) obsahuje sadu masivní znázorňující udělat jenom o něco v F #, od absolutní Začátečník až vysoce pokročilé fragmenty fragmenty kódu.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-137">The [F# Snippets Website](http://www.fssnip.net) contains a massive set of code snippets showing how to do just about anything in F#, ranging from absolute beginner to highly advanced snippets.</span></span>

<span data-ttu-id="ac9ae-138">[Slack Foundation softwaru F #](http://fsharp.org/guides/slack/) je skvělým místem pro začátečníky a odborníky agentem, je vysoce aktivní, a má některé světě nejlepší F # programátorů k dispozici pro ke konverzaci.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-138">The [F# Software Foundation Slack](http://fsharp.org/guides/slack/) is a great place for beginners and experts alike, is highly active, and has some of world's best F# programmers available for a chat.</span></span> <span data-ttu-id="ac9ae-139">Důrazně doporučujeme připojení.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-139">We highly recommend joining.</span></span>

## <a name="the-f-software-foundation"></a><span data-ttu-id="ac9ae-140">Foundation softwaru F #</span><span class="sxs-lookup"><span data-stu-id="ac9ae-140">The F# Software Foundation</span></span>

<span data-ttu-id="ac9ae-141">I když společnost Microsoft se primární vývojáře jazyka F # a jejích nástrojů v sadě Visual Studio, F # je také zálohován nezávislé foundation, F # softwaru Foundation (FSSF).</span><span class="sxs-lookup"><span data-stu-id="ac9ae-141">Although Microsoft is the primary developer of the F# language and its tools in Visual Studio, F# is also backed by an independent foundation, the F# Software Foundation (FSSF).</span></span>

<span data-ttu-id="ac9ae-142">Zvláště Foundation softwaru F # je povýšit, ochranu a zálohy programovací jazyk, F # a pro podporu a usnadnění růst různých a mezinárodní komunita programátory v jazyce F #.</span><span class="sxs-lookup"><span data-stu-id="ac9ae-142">The mission of the F# Software Foundation is to promote, protect, and advance the F# programming language, and to support and facilitate the growth of a diverse and international community of F# programmers.</span></span>

<span data-ttu-id="ac9ae-143">Další informace a zahrňte, podívejte se na [fsharp.org](http://fsharp.org). Je bezplatná a síť F # vývojářů v základ je něco, které nechcete neproběhly out v!</span><span class="sxs-lookup"><span data-stu-id="ac9ae-143">To learn more and get involved, check out [fsharp.org](http://fsharp.org). It's free to join, and the network of F# developers in the foundation is something you don't want to miss out on!</span></span>
