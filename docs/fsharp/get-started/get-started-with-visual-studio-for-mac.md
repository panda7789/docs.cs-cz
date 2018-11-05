---
title: Začínáme s jazykem F# v sadě Visual Studio pro Mac
description: Další informace o použití F# pomocí sady Visual Studio pro Mac.
ms.date: 07/03/2018
ms.openlocfilehash: 6aceec299c29e04aecd7999cd1dda6a56dd2779a
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "44042320"
---
# <a name="get-started-with-f-in-visual-studio-for-mac"></a>Začínáme s jazykem F# v sadě Visual Studio pro Mac

F# a nástrojů Visual F# jsou podporovány v sadě Visual Studio pro Mac integrovaného vývojového prostředí. Ujistěte se, že máte [Visual Studio for Mac nainstalovat](install-fsharp.md#install-f-with-visual-studio-for-mac).

## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace

Jeden z nejzákladnější projektů v sadě Visual Studio for Mac je konzolová aplikace.  Tady je postup.  Jakmile se otevře Visual Studio pro Mac:

1. Na **souboru** nabídky, přejděte k **nové řešení**.

2.  V dialogovém okně Nový projekt existují 2 různé šablony služby pro konzolové aplikace.  V části Další existuje -> .NET, který cílí na .NET Framework.  Druhá šablona se v .NET Core -> aplikace, které cílí na .NET Core.  Buď šablona by měla fungovat pro účely tohoto článku.

3. V části konzolovou aplikaci C# do jazyka F# potřeby změňte.  Zvolte **Další** tlačítka vpřed!  

4. Pojmenujte svůj projekt a zvolte možnosti, které chcete pro aplikaci.  Všimněte si, v podokně náhledu na okraji obrazovky, který se zobrazí adresářovou strukturu, která bude vytvořena podle vybrané možnosti.  

5. Klikněte na tlačítko **vytvořit**.  Teď byste měli vidět projektu F# v Průzkumníku řešení.

## <a name="writing-your-code"></a>Psaní kódu

Začněme napsáním nějakého kódu.  Ujistěte se, že `Program.fs` soubor je otevřený a potom nahraďte jeho obsah následujícím kódem:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

V předchozí ukázce kódu, funkce `square` byla definována desetinný vstup s názvem `x` a vynásobí samostatně.  Vzhledem k tomu F# používá [odvození typu](../language-reference/type-inference.md), typ `x` nemusí být zadán.  Kompilátor F# rozumí typy, kde je platný násobení a to typu `x` podle toho, jak `square` je volána.  Pokud najedete myší `square`, byste měli vidět následující:

```
val square: x:int -> int
```

Je to, co se označuje jako typ signatury funkce.  Může být číst takto: "čtverec je funkce, která přebírá celočíselným parametrem s názvem x a vytváří integer".  Všimněte si, že kompilátor přiřadil `square` `int` typ prozatím - totiž násobení není obecná napříč *všechny* typy, ale místo toho je obecný zavřené sadě typy.  Kompilátor F# vyberou `int` v tomto bodu, ale budou upraveny podpis typu při volání `square` s jiným typ vstupu, například `float`.

Další funkci `main`, je definován, která je upravena pomocí `EntryPoint` atribut spuštění tohoto programu předat kompilátor F# by se měl spustit existuje.  Řídí stejnou konvencí jako ostatní [programovacích jazyků C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde můžete předávat argumenty příkazového řádku pro tuto funkci a vrátí kód celé číslo (obvykle `0`).

Je v této funkce, které označujeme jako `square` funkci s argumentem `12`.  Poté přiřadí typ kompilátoru jazyka F# `square` bude `int -> int` (to znamená, funkce, která přebírá `int` a vytváří `int`).  Volání `printfn` je formátovaný tisk funkci, která používá řetězec formátu, podobně jako C-style programovacích jazyků, parametry, které odpovídají jsou uvedeny ve formátovacím řetězci a potom zobrazí výsledek a nový řádek.

## <a name="running-your-code"></a>Spuštění kódu

Můžete spustit kód a zobrazit výsledky kliknutím na **spustit** z nabídky na nejvyšší úrovni a následně **spustit bez ladění**.  Tím se spustí program bez ladění a vám umožní vidět výsledky.

Teď byste měli vidět následující zobrazeny v okně konzoly, který Visual Studio for Mac odebrány nahoru:

```
12 squared is 144!
```

Blahopřejeme!  Jste vytvořit svůj první projekt F# v sadě Visual Studio pro Mac, zapsat, že funkce jazyka F# Tisk výsledků volání této funkce a spuštění projektu zobrazíte některé výsledky.

## <a name="using-f-interactive"></a>Používání jazyka F# Interactive

Jedním z nejlepších funkcí nástroje Visual F# nástroje v sadě Visual Studio pro Mac je F# interaktivní okno.  Umožňuje poslat kód prostřednictvím procesu, kde můžete tento kód a interaktivně zobrazit výsledek.

Chcete-li začít s používáním, zvýrazněte `square` funkci definovanou ve vašem kódu.  Pak klikněte na **upravit** z nabídky nejvyšší úrovně.  Dále vyberte **odeslat výběr do F# Interactive**.  To spustí kód v interaktivním okně F#.  Alternativně klikněte pravým tlačítkem na výběr a zvolte **odeslat výběr do F# Interactive**.  Měli byste vidět F# interaktivního okna následující v něm se zobrazí:

```
>

val square : x:int -> int

>
```

Zobrazí se stejným podpisem funkce pro `square` funkci, kterou jste předtím viděli při přechodu myši nad funkce.  Protože `square` je nyní definována v F# interaktivní proces, můžete ji volat s různými hodnotami:

```
> square 12;;
val it : int = 144
>square 13;;
val it : int = 169
```

To spustí funkci, sváže výsledek s novým názvem `it`a zobrazí se typ a hodnotu `it`.  Všimněte si, že každý řádek musí být ukončen `;;`.  To je, jak F# Interactive ví dokončení volání funkce.  Můžete také definovat nové funkce v jazyce F# Interactive:

```
> let isOdd x = x % 2 <> 0;;

val isOdd : x:int -> bool

> isOdd 12;;
val it : bool = false
```

Výše uvedené definuje novou funkci, `isOdd`, který přebírá `int` a kontroluje, jestli je liché!  Můžete volat tuto funkci chcete zobrazit, co vrátí s různými vstupy.  Bude možné volat funkce v rámci volání funkce:

```
> isOdd (square 15);;
val it : bool = true
```

Můžete také použít [operátor kanálu vpřed](../language-reference/symbol-and-operator-reference/index.md) do kanálu hodnotu do dvou funkcí:

```
> 15 |> square |> isOdd;;
val it : bool = true
```

Operátor kanálu vpřed a další, jsou popsané v dalších kurzech.

Toto je pouze se stručně zmíníme co můžete dělat s F# Interactive.  Další informace, podívejte se na [interaktivní programování s F#](../tutorials/fsharp-interactive/index.md).

## <a name="next-steps"></a>Další kroky

Pokud jste to ještě neudělali, podívejte se [Tour F#](../tour.md), která uvádí i některé základní funkce jazyka F#.  Bude vám poskytnou přehled o některé funkce jazyka F# a poskytovat ukázky ukázku kódu, které můžete zkopírovat do sady Visual Studio pro Mac a spustit.  Existují také některé skvělé externí prostředky můžete použít, zobrazují v [Průvodce jazykem F#](../index.md).

## <a name="see-also"></a>Viz také:

- [Visual F#](../index.md)  
- [Prohlídka jazyka F#](../tour.md)  
- [Referenční dokumentace jazyka F#](../language-reference/index.md)  
- [Odvození typu](../language-reference/type-inference.md)  
- [Referenční dokumentace symbolů a – operátor](../language-reference/symbol-and-operator-reference/index.md)  
