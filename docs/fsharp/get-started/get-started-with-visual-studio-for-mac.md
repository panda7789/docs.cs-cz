---
title: "Začínáme s F # v sadě Visual Studio pro Mac"
description: "Další informace o použití F # pomocí sady Visual Studio for Mac."
keywords: "Visual f #, f #, funkční programování"
author: mizzle-mo
ms.author: phcart
ms.date: 02/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 8db75596-19a9-4eda-b20d-a12d517c8cc1
ms.openlocfilehash: 776a2ddf5563a954e462b3888ebf05da90241e4b
ms.sourcegitcommit: 655fd4f78741967f80c409cef98347fdcf77857d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Začínáme s F # v sadě Visual Studio pro Mac

F # a nástrojů Visual F # jsou podporovány v sadě Visual Studio pro Mac IDE.  Pokud chcete začít, měli byste [stažení sady Visual Studio pro Mac](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs), pokud jste tak ještě neučinili.  Tento článek používá 2017 pro komunity Visual Studio pro Mac, ale můžete použít F # verzí podle svého výběru.

## <a name="installing-f"></a>Instalace F # #

Po stažení sady Visual Studio pro Mac, vás vyzve k výběru chcete nainstalovat.  Pro účely tohoto článku jsme se ponechat výchozí hodnoty.  Na rozdíl od Visual Studio pro Windows není potřeba konkrétně nainstalovat podporu F #.  Stiskněte klávesu "Instalaci", aby bylo možné pokračovat.

Po dokončení instalace, vyberte "Spusťte Visual Studio".  Také ho můžete spustit v systému macOS prostřednictvím funkce hledání.

## <a name="creating-a-console-application"></a>Vytvoření aplikace konzoly

Jeden z nejzákladnější projektů v sadě Visual Studio pro Mac je konzolová aplikace.  Chcete-li to provést.  Po otevřete Visual Studio pro Mac:

1. Na **soubor** nabídky, přejděte na příkaz **nové řešení**.

2.  V dialogovém okně Nový projekt jsou 2 různé šablony pro konzolové aplikace.  Je v části Další -> .NET, která cílí rozhraní .NET Framework.  Jiné šablony je pod .NET Core -> aplikace, která cílí na .NET Core.  Buď šablona by měla fungovat pro účely tohoto článku.

3. V části konzolovou aplikaci změňte C# na F # v případě potřeby.  Vyberte **Další** tlačítko Předat dál přesunout!  

4. Pojmenujte projekt a zvolte možnosti, které chcete pro aplikaci.  Všimněte si, v podokně náhledu na stranu obrazovky, který se zobrazí strukturu adresáře, který bude vytvořen založené na vybrané možnosti.  

5. Klikněte na tlačítko **vytvořit**.  Teď byste měli vidět projektu F # v Průzkumníku řešení.

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

Můžete spustit kód a zobrazit výsledky, klikněte na **spustit** z nabídky nejvyšší úrovně a potom **spustit bez ladění**.  Tento program se spustí bez ladění a umožňuje zobrazit výsledky.

Teď byste měli vidět následující vytisknout do okna konzoly, která Visual Studio pro Mac odebrány až:

```
12 squared is 144!
```

Blahopřejeme!  Jste vytvořili svůj první projekt F # v sadě Visual Studio pro Mac, zapisovat že funkce F # vytisknout výsledky volání této funkce a spusťte projekt zobrazíte některé výsledky.

## <a name="using-f-interactive"></a>Pomocí F # interaktivní

Jedním z nejlepší funkce z Visual F # nástrojů v sadě Visual Studio pro Mac je interaktivních okna F #.  Umožňuje odeslat kód prostřednictvím procesu, kde můžete volat tento kód a zobrazit výsledky interaktivně.

Chcete-li začít používat ji, zvýrazněte `square` funkci definovanou v kódu.  Klikněte na tlačítko na **upravit** z nabídky nejvyšší úrovně.  Dále vyberte **poslat výběr F # interaktivní**.  To spustí kód v okně interaktivní F #.  Alternativně můžete klikněte pravým tlačítkem na výběr a zvolte **poslat výběr F # interaktivní**.  Měli byste vidět F # interaktivních okna zobrazují se v něm následující:

```
>

val square : x:int -> int

>
```

Zobrazí se stejným podpisem funkce pro `square` funkce, které jste předtím viděli při při přechodu myší nad funkce.  Protože `square` je nyní definována v F # interaktivní proces, můžete ji volat s různými hodnotami:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Tato funkce spustí, váže výsledek na nový název `it`a zobrazí typu a hodnoty `it`.  Všimněte si, že musí být ukončen každý řádek s `;;`.  Toto je, jak F # interaktivní zná dokončení volání funkce.  Můžete také definovat nové funkce v F # interaktivní:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Výše definuje novou funkci, `isOdd`, které trvá `int` a kontroluje, zda se jedná o liché!  Můžete volat této funkci můžete zjistit, co vrací s různými vstupy.  Můžete volat funkce v rámci volání funkce:

```
> isOdd (square 15);;
val it : bool = true
```

Můžete také [operátor kanálu dopředného](../language-reference/symbol-and-operator-reference/index.md) do kanálu hodnotu do dvě funkce:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

Operátor kanálu dopředného a další, jsou popsané v dalších kurzech.

Toto je pouze balíčku glimpse do co můžete dělat s F # interaktivní.  Další informace, podívejte se na [interaktivní programování s F #](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Další kroky

Pokud jste to ještě neudělali, podívejte se [prohlídka z F #](../tour.md), které zahrnuje některé základní funkce jazyka F #.  Bude vám poskytl přehled některých možností F # a zadejte ukázky dostatečným kódu, které můžete zkopírovat do sady Visual Studio pro Mac a spustit.  Existují také některé skvělé externím prostředkům, můžete použít, showcased v [Průvodce F #](../index.md).

## <a name="see-also"></a>Viz také
 [Visual F#](../index.md)  
 [Prohlídka jazyka F#](../tour.md)  
 [Referenční dokumentace jazyka F #](../language-reference/index.md)  
 [Odvození typu](../language-reference/type-inference.md)  
 [Referenční dokumentace symbolů a – operátor](../language-reference/symbol-and-operator-reference/index.md)  
