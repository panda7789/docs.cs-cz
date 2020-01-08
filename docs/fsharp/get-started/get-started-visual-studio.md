---
title: Začínáme s nástrojem F# v aplikaci Visual Studio
description: Naučte se používat F# se sadou Visual Studio.
ms.date: 12/20/2019
ms.openlocfilehash: 9bf47fb08ea3df0aa0d5064043d94f030d45d568
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337346"
---
# <a name="get-started-with-f-in-visual-studio"></a>Začínáme s nástrojem F# v aplikaci Visual Studio

F#a vizuální F# nástroje jsou podporovány v integrovaném vývojovém prostředí (IDE) sady Visual Studio.

Pokud chcete začít, ujistěte se, že máte [nainstalovanou F# aplikaci Visual Studio s podporou](install-fsharp.md#install-f-with-visual-studio).

## <a name="create-a-console-application"></a>Vytvoření konzolové aplikace

Jedním z nejvíc základních projektů v aplikaci Visual Studio je aplikace konzoly. Tady je postup, jak ho vytvořit:

1. Otevřete Visual Studio 2019.

2. V okně Start vyberte možnost **vytvořit nový projekt**.

3. Na stránce **vytvořit nový projekt** vyberte **F#** ze seznamu jazyk.

4. Zvolte šablonu **Konzolová aplikace (.NET Core)** a klikněte na tlačítko **Další**.

5. Na stránce **Konfigurovat nový projekt** zadejte název do pole **název projektu** . Pak zvolte **vytvořit**.

   Visual Studio vytvoří nový F# projekt. Můžete ji zobrazit v okně Průzkumník řešení.

## <a name="write-the-code"></a>Zadejte kód

Pojďme začít psaním kódu. Ujistěte se, že je soubor `Program.fs` otevřený, a pak jeho obsah nahraďte následujícím:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

Předchozí ukázka kódu definuje funkci s názvem `square`, která přebírá vstup s názvem `x` a vynásobí ho samotným. Vzhledem F# k tomu, že používá [odvození typu](../language-reference/type-inference.md), není nutné zadat typ `x`. F# Kompilátor rozumí typům, kde je násobení platné, a přiřadí typ, který `x` na základě toho, jak je `square` volána. Pokud najedete myší na `square`, měli byste vidět následující:

```fsharp
val square: x:int -> int
```

Jedná se o to, co se říká signatura typu funkce. Dá se číst takto: "čtvercem je funkce, která přebírá celé číslo s názvem x a vytváří celé číslo". Kompilátor poskytl `square` `int` typ pro teď; Důvodem je, že násobení není obecné napříč *všemi* typy, ale spíše uzavřenou sadou typů. F# Kompilátor upraví signaturu typu při volání `square` s jiným typem vstupu, jako je například `float`.

Je definována jiná funkce, `main`, která je upravena atributem `EntryPoint`. Tento atribut oznamuje F# kompilátoru, že by měl spustit program pro spuštění programu. Řídí se stejnou konvencí jako jiné [programovací jazyky ve stylu jazyka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku lze předat této funkci a je vrácen celočíselný kód (obvykle `0`).

Je ve funkci vstupního bodu, `main`, která volá funkci `square` s argumentem `12`. F# Kompilátor potom přiřadí typ `square`, který se má `int -> int` (to znamená funkce, která přebírá `int` a vytvoří `int`). Volání `printfn` je naformátovaná funkce pro tisk, která používá formátovací řetězec a tiskne výsledek (a nový řádek). Řetězec formátu, podobně jako programovací jazyky ve stylu jazyka C, má parametry (`%d`), které odpovídají argumentům, které jsou předány, v tomto případě `12` a `(square 12)`.

## <a name="run-the-code"></a>Spuštění kódu

Můžete spustit kód a zobrazit výsledky stisknutím **kombinace kláves Ctrl**+**F5**. Alternativně můžete zvolit > **ladění** **Spustit bez ladění** z panelu nabídek nejvyšší úrovně. Tím se spustí program bez ladění.

Následující výstup vytiskne okno konzoly, které se otevřelo v aplikaci Visual Studio:

```console
12 squared is: 144!
```

Blahopřejeme! Vytvořili jste svůj první F# projekt v aplikaci Visual Studio, napsali jste F# funkci, která vypočítá a vytiskne hodnotu a spustí projekt, aby se zobrazily výsledky.

## <a name="next-steps"></a>Další kroky

Pokud jste to ještě neudělali, podívejte se na [prohlídku F# ](../tour.md), která se zabývá některými základními F# funkcemi daného jazyka. Poskytuje přehled některých funkcí a všech F# ukázek kódu, které můžete zkopírovat do sady Visual Studio a spustit.

> [!div class="nextstepaction"]
> [Prohlídka jazyka F#](../tour.md)

## <a name="see-also"></a>Viz také:

- [F#Referenční dokumentace jazyka](../language-reference/index.md)
- [Odvození typu](../language-reference/type-inference.md)
- [Reference k symbolům a operátorovi](../language-reference/symbol-and-operator-reference/index.md)
