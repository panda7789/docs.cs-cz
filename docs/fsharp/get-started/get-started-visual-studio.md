---
title: 'Začínáme s F # v sadě Visual Studio'
description: 'Další informace o použití F # pomocí sady Visual Studio.'
ms.date: 02/13/2017
ms.openlocfilehash: 22fbe8086ec133605e1d9b4b28e524fe2ed8ac28
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2018
ms.locfileid: "34728531"
---
# <a name="get-started-with-f-in-visual-studio"></a>Začínáme s F # v sadě Visual Studio

F # a nástrojů Visual F # jsou podporovány v prostředí Visual Studio IDE.  Pokud chcete začít, měli byste [Visual Studio Stáhnout](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), pokud jste tak ještě neučinili.  Tento článek používá Visual Studio 2017 Community Edition, ale můžete použít F # verzí podle svého výběru.

## <a name="installing-f"></a>Instalace F # #

Pokud probíhá stahování programu sady Visual Studio poprvé, bude nejprve nainstalovat Instalační program sady Visual Studio.  Všechny verze aplikace Visual Studio 2017 nainstalujte z instalačního programu. Pokud je již nainstalováno, klikněte na tlačítko **upravit**.

Dále se zobrazí seznam úloh. Můžete nainstalovat F # do některého z následujících úloh:

|zatížení|Akce|
|--------|------|
| Vývoj pro různé platformy .NET core | Ve výchozím nastavení je nainstalovaná žádná akce - F # |
| ASP.NET a vývoje | Ve výchozím nastavení je nainstalovaná žádná akce - F # |
| Vývoj pro Azure | Ve výchozím nastavení je nainstalovaná žádná akce - F # |
| Mobilní vývoj pomocí rozhraní .NET | Ve výchozím nastavení je nainstalovaná žádná akce - F # |
| Aplikace pro datové vědy a analýzy | Ve výchozím nastavení je nainstalovaná žádná akce - F # |
| Vývoj aplikací rozhraní .NET | Vyberte **podporu klientů jazyka F #** z pravé strany |
| Ukládání a zpracování dat | Vyberte **podporu klientů jazyka F #** z pravé strany |

Klikněte na tlačítko **upravit** v pravé straně dole.  Nainstaluje všechny objekty, které jste vybrali.  Pak můžete otevřít Visual Studio 2017 s podporou jazyka F # kliknutím **spusťte**.

## <a name="creating-a-console-application"></a>Vytvoření aplikace konzoly

Jeden z nejzákladnější projektů v sadě Visual Studio je konzolová aplikace.  Chcete-li to provést.  Po otevřete Visual Studio:

1. Na **soubor** nabídky, přejděte na příkaz **nový**a potom zvolte **projektu**.

2.  V nový projekt dialogové okno, v části **šablony**, měli byste vidět **Visual F #**.  Výběrem této zobrazíte šablony F #.

3. Vyberte buď **.NET základní konzolovou aplikaci** nebo **konzolovou aplikaci**.

3. Vyberte **nevadí** tlačítko pro vytvoření projektu F #!  Teď byste měli vidět projektu F # v Průzkumníku řešení.

## <a name="writing-your-code"></a>Psaní kódu

Můžeme začít napsáním nějakého kódu.  Ujistěte se, že `Program.fs` soubor je otevřený a poté nahraďte jeho obsah následujícím kódem:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

V předchozí ukázce kódu, funkce `square` byla definována což trvá vstup s názvem `x` a vynásobí samostatně.  Protože F # používá [odvození typu](../language-reference/type-inference.md), typ `x` není potřeba zadat.  Kompilátor jazyka F # rozumí typy, kde je platný násobení a přiřadí typ k `x` podle toho, jaký `square` je volána.  Pokud se ukazatel myši přesunete `square`, měli byste vidět následující:

```
val square: x:int -> int
```

Toto je, co se označuje jako typ podpis funkce.  Může být číst takto: "čtvercovou je funkce, která přebírá celé číslo s názvem x a vytváří celé číslo".  Všimněte si, že jste dali kompilátor `square` `int` typ prozatím - totiž násobení není obecná napříč *všechny* typy, ale spíše je obecný napříč uzavřené sadu typů.  Zaznamenání kompilátoru F # `int` na tomto bodu, ale upraví podpis typu při volání `square` s jiným typ vstupu, například `float`.

Jiné funkce, `main`, je definován, který je upraven pomocí `EntryPoint` atribut říct kompilátor jazyka F # spuštění tohoto programu by se měl spustit existuje.  Postupuje stejné konvence jako ostatní [programovací jazyky C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku se dá předat do této funkce a je vrácen kód celé číslo (obvykle `0`).

Je v této funkci, která se nazývá `square` funkce s argument `12`.  Kompilátor jazyka F # poté přiřadí typ `square` být `int -> int` (to znamená, funkci, která přebírá `int` a vytváří `int`).  Volání `printfn` je formátovaný tisk funkci, která používá řetězec formátu, podobně jako programovací jazyky C-style, parametry, které odpovídá platformám zadaným v řetězec formátu a potom zobrazí výsledek a nový řádek.

## <a name="running-your-code"></a>Spuštěním kódu

Můžete spustit kód a zobrazte výsledky stisknutím **ctrl + f5**.  Tento program se spustí bez ladění a umožňuje zobrazit výsledky.  Alternativně můžete **ladění** nabídka nejvyšší položku v sadě Visual Studio a zvolte **spustit bez ladění**.

Teď byste měli vidět následující vytisknout do okna konzoly, která sada Visual Studio odebrány až:

```
12 squared is 144!
```

Blahopřejeme!  Jste vytvořili svůj první projekt F # v sadě Visual Studio, zapisovat že funkce F # vytisknout výsledky volání této funkce a spusťte projekt zobrazíte některé výsledky.

## <a name="next-steps"></a>Další kroky

Pokud jste to ještě neudělali, podívejte se [prohlídka z F #](../tour.md), které zahrnuje některé základní funkce jazyka F #.  Bude vám poskytl přehled některých možností F # a zadejte ukázky dostatečným kódu, které můžete zkopírovat do sady Visual Studio a spustit.  Existují také některé skvělé externím prostředkům, můžete použít, showcased v [Průvodce F #](../index.md).

## <a name="see-also"></a>Viz také:
 [Visual F#](index.md)  
 [Prohlídka jazyka F#](../tour.md)  
 [Referenční dokumentace jazyka F #](../language-reference/index.md)  
 [Odvození typu](../language-reference/type-inference.md)  
 [Referenční dokumentace symbolů a – operátor](../language-reference/symbol-and-operator-reference/index.md)  
