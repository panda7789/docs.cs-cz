---
title: Začínáme s nástrojem F# v Visual Studio pro Mac
description: Naučte se používat F# s Visual Studio pro Mac.
ms.date: 07/03/2018
ms.openlocfilehash: cd45ab9c59cef76e4bf85a93f39d8e2ee063d200
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552373"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Začínáme s nástrojem F# v Visual Studio pro Mac

F#a vizuální F# nástroje jsou podporovány v Visual Studio pro Mac integrovaném vývojovém prostředí. Ujistěte se, že máte [nainstalovanou Visual Studio pro Mac](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace

Jedním z nejvíce základních projektů v Visual Studio pro Mac je Konzolová aplikace.  Tady je postup, jak to provést.  Jakmile Visual Studio pro Mac otevřete:

1. V nabídce **soubor** přejděte na příkaz **nové řešení**.

2. V dialogovém okně Nový projekt existují 2 různé šablony pro konzolovou aplikaci.  Existuje jeden pod > .NET, který cílí na .NET Framework.  Druhá šablona je v rámci aplikace .NET Core->, která cílí na .NET Core.  Každá šablona by měla fungovat pro účely tohoto článku.

3. V části Konzolová aplikace C# v F# případě potřeby změňte na.  Kliknutím na tlačítko **Další** přesunete vpřed.  

4. Zadejte název vašeho projektu a vyberte požadované možnosti pro aplikaci.  Všimněte si, že podokno náhledu na stranu obrazovky, ve kterém se zobrazí struktura adresáře, která bude vytvořena na základě vybraných možností.  

5. Klikněte na **vytvořit**.  V Průzkumník řešení by se teď F# měl zobrazit projekt.

## <a name="writing-your-code"></a>Psaní kódu

Pojďme začít vytvořením kódu jako prvního.  Ujistěte se, že je soubor `Program.fs` otevřený, a pak jeho obsah nahraďte následujícím:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

V předchozím příkladu kódu byla definována funkce `square`, která přebírá vstup s názvem `x` a vynásobí jej sebou samým.  Vzhledem F# k tomu, že používá [odvození typu](../language-reference/type-inference.md), není nutné zadat typ `x`.  F# Kompilátor rozumí typům, kde je násobení platné, a přiřadí typ k `x` na základě toho, jak je volána `square`.  Pokud najedete myší na `square`, měli byste vidět následující:

```console
val square: x:int -> int
```

Jedná se o to, co se říká signatura typu funkce.  Dá se číst takto: "čtvercem je funkce, která přebírá celé číslo s názvem x a vytváří celé číslo".  Všimněte si, že kompilátor `square` typ `int` pro tuto skutečnost, protože násobení není obecné napříč *všemi* typy, ale spíše je obecné napříč uzavřenou sadou typů.  F# Kompilátor vybral `int` v tomto okamžiku, ale upraví signaturu typu, pokud voláte `square` s jiným typem vstupu, jako je například `float`.

Je definována jiná funkce, `main`, která je upravena pomocí atributu `EntryPoint`, aby informovala F# kompilátor, že by měl spustit program pro spuštění programu.  Řídí se stejnou konvencí jako jiné [programovací jazyky ve stylu jazyka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku lze předat této funkci a je vrácen celočíselný kód (obvykle `0`).

Je v této funkci, která volá funkci `square` s argumentem `12`.  F# Kompilátor potom přiřadí typ `square`, který se má `int -> int` (to znamená funkce, která přijímá `int` a vytvoří `int`).  Volání `printfn` je naformátovaná funkce pro tisk, která používá formátovací řetězec, podobně jako programovací jazyky ve stylu jazyka C, parametry, které odpovídají těm, které jsou zadány ve formátu řetězce, a pak vypíše výsledek a nový řádek.

## <a name="running-your-code"></a>Spuštění kódu

Můžete spustit kód a zobrazit výsledky kliknutím na **Spustit** v nabídce nejvyšší úrovně a pak **Spustit bez ladění**.  Tím se spustí program bez ladění a umožní vám zobrazit výsledky.

Nyní byste měli vidět následující vytištěné okno konzoly, které Visual Studio pro Mac odebráno:

```console
12 squared is 144!
```

Blahopřejeme!  Vytvořili jste svůj první F# projekt v Visual Studio pro Mac, napsali jste F# funkci, která vytiskla výsledky volání funkce a spustí projekt, aby se zobrazily nějaké výsledky.

## <a name="using-f-interactive"></a>Pomocí F# Interactive

Jednou z nejlepších funkcí vizuálních F# nástrojů v Visual Studio pro Mac je F# interaktivní okno.  Umožňuje odeslat kód do procesu, kde můžete zavolat tento kód a interaktivně zobrazit výsledek.

Pokud ho chcete začít používat, zvýrazněte `square` funkci definovanou v kódu.  Potom v nabídce nejvyšší úrovně klikněte na **Upravit** .  V dalším kroku vyberte **Odeslat F# výběr do interaktivního**.  Tím se spustí kód v F# interaktivním okně.  Případně můžete kliknout pravým tlačítkem na výběr a vybrat **Odeslat výběr do F# interaktivní**.  Mělo by se zobrazit F# interaktivní okno s následujícím:

```console
>

val square : x:int -> int

>
```

Tím se zobrazí stejná signatura funkce funkce `square`, kterou jste viděli dříve při přechodu na funkci.  Vzhledem k tomu, že je nyní F# v interaktivním procesu definován `square`, můžete ji zavolat s různými hodnotami:

```console
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

Tím se spustí funkce, vytvoří se výsledek s novým názvem `it`a zobrazí typ a hodnotu `it`.  Všimněte si, že je nutné ukončit každý řádek pomocí `;;`.  To je způsob F# , jak interaktivní ví, kdy bylo volání funkce dokončeno.  Můžete také definovat nové funkce v F# Interactive:

```console
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Výše uvedený příkaz definuje novou funkci `isOdd`, která přebírá `int` a kontroluje, jestli je liché.  Voláním této funkce můžete zjistit, co se vrátí s různými vstupy.  Můžete volat funkce v volání funkce:

```console
> isOdd (square 15);;
val it : bool = true
```

K zřetězení hodnoty do dvou funkcí můžete použít také [operátor předávání kanálu](../language-reference/symbol-and-operator-reference/index.md) :

```console
> 15 |> square |> isOdd;;
val it : bool = true
```

Operátor s přesměrováním na kanál a další jsou uvedené v dalších kurzech.

To je jenom nakoukněte, co můžete dělat s F# interaktivními.  Pokud se chcete dozvědět víc, podívejte [se na F#interaktivní programování pomocí ](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Další kroky

Pokud jste to ještě neudělali, podívejte se na [prohlídku F# ](../tour.md), která se zabývá některými základními F# funkcemi daného jazyka.  Poskytne vám přehled některých možností F#nástroje a poskytne vám podrobné ukázky kódu, které můžete zkopírovat do Visual Studio pro Mac a spustit.  K dispozici jsou také některé skvělé externí prostředky, které můžete použít v [ F# průvodci](../index.yml).

## <a name="see-also"></a>Viz také:

- [F#program](../index.yml)
- [Prohlídka jazyka F#](../tour.md)
- [F#Referenční dokumentace jazyka](../language-reference/index.md)
- [Odvození typu](../language-reference/type-inference.md)
- [Reference k symbolům a operátorovi](../language-reference/symbol-and-operator-reference/index.md)
