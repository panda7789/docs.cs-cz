---
title: Průvodce jazykem F#
description: 'Tato příručka poskytuje přehled o různých studijních materiálů F # je funkční programovací jazyk, který běží na rozhraní .NET.'
author: jackfoxy
ms.author: phcart
ms.date: 03/19/2018
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 9c03148d42f3cf8731580e36990aa21c68f705f6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="f-guide"></a>Průvodce jazykem F#

F # je funkční programovací jazyk, který běží na rozhraní .NET. Je také plnou podporu pro objekty, že vám dovolí blend funkční a objekt programování pro protokol řešení jakýkoli problém.

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

F # je o produktivitu svou podstatou. Podpora nástrojů pro F # je všudypřítomná a úplné pokročilých funkcí.

## <a name="learning-f"></a>Learning F # #

[Prohlídka F #](tour.md) shrnovat hlavní jazykové funkce s mnoha ukázek kódu. To se doporučuje, když jste nový F # a chcete se podívat, jak jazyk funguje.

[Začínáme s F # v sadě Visual Studio](get-started/get-started-visual-studio.md) Pokud jste v systému Windows a chcete úplné prostředí Visual Studio IDE (Integraded Development Environment).

[Začínáme s F # v sadě Visual Studio pro Mac](get-started/get-started-with-visual-studio-for-mac.md) Pokud jste v systému macOS a chcete použít Visual Studio IDE.

[Začínáme s F # ve Visual Studio Code](get-started/get-started-vscode.md) Pokud chcete, aby lightweight, napříč platformami a prostředí IDE mnoha funkcemi.

[Začínáme s F # pomocí rozhraní příkazového řádku .NET Core](get-started/get-started-command-line.md) Pokud chcete pomocí nástroje příkazového řádku.

[Začínáme s F # a Xamarin](https://docs.microsoft.com/xamarin/cross-platform/platform/fsharp/) pro mobilní programování s F #.

## <a name="references"></a>Odkazy

[Referenční dokumentace jazyka F #](language-reference/index.md) je odkaz na oficiální, komplexní pro všechny funkce jazyka F #. Každý článek vysvětluje syntaxe a zobrazuje ukázky kódu. Na panelu filtru v obsahu slouží k vyhledání konkrétní článků.

[F # referenční dokumentace hlavní knihovny](https://msdn.microsoft.com/visualfsharpdocs/conceptual/fsharp-core-library-reference) je referenční dokumentace rozhraní API pro základní knihovny F #.


## <a name="additional-guides"></a>Další příručky

[F # pro Fun a zisku](https://swlaschin.gitbooks.io/fsharpforfunandprofit/content/) je komplexní a velmi podrobné adresáře na učení F #. Jeho obsah a Autor jsou milého komunitou F #. Cílové skupiny je primárně vývojářům objektově orientované programování pozadí.

[Programování Wikibook F #](https://en.wikibooks.org/wiki/F_Sharp_Programming) je wikibook o učení F #. Je také produktu komunity F #. Cílové skupiny je lidí, kteří jsou nové pro F #, s chvilku objektově orientované programování pozadí.

## <a name="learn-f-through-videos"></a>Další informace F # prostřednictvím videa

[F # – tutoriál na YouTube](https://www.youtube.com/watch?v=c7eNDJN758U) je skvělým Úvod do F # pomocí sady Visual Studio, zobrazuje v průběhu 1,5 hodiny velké množství skvělé příklady. Cílové skupiny je Visual Studio vývojáře, kteří jsou nové F #.

[Úvod do programování s F #](https://www.youtube.com/watch?v=Teak30_pXHk&list=PLEoMzSkcN8oNiJ67Hd7oRGgD1d4YBxYGC) je skvělým video série, která používá Visual Studio Code jako hlavní editoru. Série videí začne nic a končí vytváření video hře RPG založený na textu. Cílové skupiny je vývojáře, kteří raději Visual Studio Code (nebo lightweight IDE) a nový F #.

[Co je nového ve Visual Studio 2017 vývojářům F # pro](https://www.linkedin.com/learning/what-s-new-in-visual-studio-2017-for-f-sharp-for-developers) je video kurzu, které jsou uvedeny některé nové funkce pro F # v Visual Studio 2017. Cílové skupiny je Visual Studio vývojáře, kteří jsou nové F #.

## <a name="other-useful-resources"></a>Další užitečné zdroje

[F # fragmenty webu](http://www.fssnip.net) obsahuje sadu masivní znázorňující udělat jenom o něco v F #, od absolutní Začátečník až vysoce pokročilé fragmenty fragmenty kódu.

[Slack Foundation softwaru F #](http://fsharp.org/guides/slack/) je skvělým místem pro začátečníky a odborníky agentem, je vysoce aktivní, a má některé světě nejlepší F # programátorů k dispozici pro ke konverzaci. Důrazně doporučujeme připojení.

## <a name="the-f-software-foundation"></a>Foundation softwaru F #

I když společnost Microsoft se primární vývojáře jazyka F # a jejích nástrojů v sadě Visual Studio, F # je také zálohován nezávislé foundation, F # softwaru Foundation (FSSF).

Zvláště Foundation softwaru F # je povýšit, ochranu a zálohy programovací jazyk, F # a pro podporu a usnadnění růst různých a mezinárodní komunita programátory v jazyce F #.

Další informace a zahrňte, podívejte se na [fsharp.org](http://fsharp.org). Je bezplatná a síť F # vývojářů v základ je něco, které nechcete neproběhly out v!
