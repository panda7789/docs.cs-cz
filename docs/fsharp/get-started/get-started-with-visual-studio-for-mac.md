---
title: Začínáme s nástrojem F# v Visual Studio pro Mac
description: Naučte se používat F# s Visual Studio pro Mac.
ms.date: 07/03/2018
ms.openlocfilehash: 679ed1ea28f5d0e0d910dbd407b38d1d2f0314f6
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68629750"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Začínáme s nástrojem F# v Visual Studio pro Mac

F#a vizuální F# nástroje jsou podporovány v Visual Studio pro Mac integrovaném vývojovém prostředí. Ujistěte se, že máte [nainstalovanou Visual Studio pro Mac](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace

Jedním z nejvíce základních projektů v Visual Studio pro Mac je Konzolová aplikace.  Tady je postup, jak to provést.  Jakmile Visual Studio pro Mac otevřete:

1. V nabídce **soubor** přejděte na příkaz **nové řešení**.

2. V dialogovém okně Nový projekt existují 2 různé šablony pro konzolovou aplikaci.  Existuje jeden pod > .NET, který cílí na .NET Framework.  Druhá šablona je v rámci aplikace .NET Core->, která cílí na .NET Core.  Každá šablona by měla fungovat pro účely tohoto článku.

3. V části Konzolová aplikace C# v F# případě potřeby změňte na.  Kliknutím na tlačítko **Další** přesunete vpřed.  

4. Zadejte název vašeho projektu a vyberte požadované možnosti pro aplikaci.  Všimněte si, že podokno náhledu na stranu obrazovky, ve kterém se zobrazí struktura adresáře, která bude vytvořena na základě vybraných možností.  

5. Klikněte na možnost **Vytvořit**.  V Průzkumník řešení by se teď F# měl zobrazit projekt.

## <a name="writing-your-code"></a>Psaní kódu

Pojďme začít vytvořením kódu jako prvního.  Ujistěte se, že `Program.fs` je soubor otevřený, a pak jeho obsah nahraďte následujícím:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

V předchozím příkladu kódu byla definována funkce `square` , která přebírá vstup s názvem `x` a násobí ho sám sebou.  Vzhledem F# [k tomu](../language-reference/type-inference.md), že používá odvození typu, nenítřebazadávattyp.`x`  F# Kompilátor rozumí typům, kde je násobení platné, a přiřadí typ `x` podle toho, jak `square` je volána.  Pokud najedete `square`myší na, měli byste vidět následující:

```
val square: x:int -> int
```

Jedná se o to, co se říká signatura typu funkce.  Dá se číst takto: "Square je funkce, která přebírá celé číslo s názvem x a vytvoří celé číslo".  Všimněte si, že kompilátor `square` tento `int` typ nyní přiřadil – je to proto, že násobení není obecné napříč *všemi* typy, ale spíše je obecné napříč uzavřenou sadou typů.  F# Kompilátor vybral `int` v tomto okamžiku, ale upraví signaturu typu, pokud voláte `square` s jiným typem vstupu, jako je `float`například.

Je definována jiná `main`funkce,,, která je upravena `EntryPoint` s atributem, aby F# informovala kompilátor, že by měl spustit program, který by měl spustit.  Odpovídá stejné konvenci jako jiné [programovací jazyky ve stylu jazyka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku lze předat této funkci a je vrácen celočíselný kód (obvykle `0`).

Je touto funkcí, která volá `square` funkci s `12`argumentem.  F# Kompilátor potom `square` přiřadí typ `int -> int` , který `int` je (to znamená `int`funkce, která přijímá a vytvoří).  Volání je naformátovaná funkce pro `printfn` tisk, která používá formátovací řetězec, podobně jako programovací jazyky ve stylu jazyka C, parametry, které odpovídají těm, které jsou zadány ve formátu řetězce, a pak vytiskne výsledek a nový řádek.

## <a name="running-your-code"></a>Spuštění kódu

Můžete spustit kód a zobrazit výsledky kliknutím na **Spustit** v nabídce nejvyšší úrovně a pak **Spustit bez ladění**.  Tím se spustí program bez ladění a umožní vám zobrazit výsledky.

Nyní byste měli vidět následující vytištěné okno konzoly, které Visual Studio pro Mac odebráno:

```
12 squared is 144!
```

Blahopřejeme!  Vytvořili jste svůj první F# projekt v Visual Studio pro Mac, napsali jste F# funkci, která vytiskla výsledky volání funkce a spustí projekt, aby se zobrazily nějaké výsledky.

## <a name="using-f-interactive"></a>Pomocí F# Interactive

Jednou z nejlepších funkcí vizuálních F# nástrojů v Visual Studio pro Mac je F# interaktivní okno.  Umožňuje odeslat kód do procesu, kde můžete zavolat tento kód a interaktivně zobrazit výsledek.

Pokud ho chcete začít používat, zvýrazněte `square` funkci definovanou ve vašem kódu.  Potom v nabídce nejvyšší úrovně klikněte na **Upravit** .  V dalším kroku vyberte **Odeslat F# výběr do interaktivního**.  Tím se spustí kód v F# interaktivním okně.  Případně můžete kliknout pravým tlačítkem na výběr a vybrat **Odeslat výběr do F# interaktivní**.  Mělo by se zobrazit F# interaktivní okno s následujícím:

```
>

val square : x:int -> int

>
```

To ukazuje stejnou signaturu funkce pro `square` funkci, kterou jste viděli dříve při přechodu na funkci.  Vzhledem `square` k tomu, že je F# nyní definováno v interaktivním procesu, můžete ho zavolat s různými hodnotami:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Tím se spustí funkce, vytvoří se výsledek k novému názvu `it`a zobrazí typ a `it`hodnotu.  Všimněte si, že je nutné ukončit každý `;;`řádek pomocí.  To je způsob F# , jak interaktivní ví, kdy bylo volání funkce dokončeno.  Můžete také definovat nové funkce v F# Interactive:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Výše uvedený postup definuje novou funkci, `isOdd`která `int` přijímá a kontroluje, jestli je lichá.  Voláním této funkce můžete zjistit, co se vrátí s různými vstupy.  Můžete volat funkce v volání funkce:

```
> isOdd (square 15);;
val it : bool = true
```

K zřetězení hodnoty do dvou funkcí můžete použít také [operátor předávání kanálu](../language-reference/symbol-and-operator-reference/index.md) :

```
> 15 |> square |> isOdd;;
val it : bool = true
```

Operátor s přesměrováním na kanál a další jsou uvedené v dalších kurzech.

To je jenom nakoukněte, co můžete dělat s F# interaktivními.  Pokud se chcete dozvědět víc, podívejte [se na F#interaktivní programování pomocí ](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Další postup

Pokud jste to ještě neudělali, podívejte se na prohlídku [ F# ](../tour.md), která se zabývá některými základními F# funkcemi daného jazyka.  Poskytne vám přehled některých možností F#nástroje a poskytne vám podrobné ukázky kódu, které můžete zkopírovat do Visual Studio pro Mac a spustit.  K dispozici jsou také některé skvělé externí prostředky, které můžete použít v [ F# průvodci](../index.md).

## <a name="see-also"></a>Viz také:

- [Visual F#](../index.md)
- [Prohlídka jazyka F#](../tour.md)
- [F#Referenční dokumentace jazyka](../language-reference/index.md)
- [Odvození typu](../language-reference/type-inference.md)
- [Reference k symbolům a operátorovi](../language-reference/symbol-and-operator-reference/index.md)
