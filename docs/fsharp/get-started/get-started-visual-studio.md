---
title: Začínáme s nástrojem F# v aplikaci Visual Studio
description: Naučte se používat F# se sadou Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 80b4fc5b7631eace719832fe32003cad578ead27
ms.sourcegitcommit: 93762e1a0dae1b5f64d82eebb7b705a6d566d839
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/27/2019
ms.locfileid: "74552819"
---
# <a name="get-started-with-f-in-visual-studio"></a>Začínáme s nástrojem F# v aplikaci Visual Studio

F#a vizuální F# nástroje jsou podporovány v integrovaném vývojovém prostředí sady Visual Studio.

Chcete-li začít, ujistěte se, že je [nainstalována F#aplikace Visual Studio s nástrojem ](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace

Jedním z nejběžnějších projektů v aplikaci Visual Studio je Konzolová aplikace.  Tady je postup, jak to provést.  Po otevření sady Visual Studio:

1. V nabídce **soubor** přejděte na příkaz **Nový**a zvolte možnost **projekt**.

2. V dialogovém okně Nový projekt, v části **šablony**byste měli vidět **vizuál F#** .  Tuto možnost vyberte, pokud F# chcete zobrazit šablony.

3. Vyberte buď **konzolovou aplikaci .NET Core** , nebo **konzolovou aplikaci**.

4. Kliknutím na tlačítko **OK** vytvořte F# projekt.  V Průzkumník řešení by se teď F# měl zobrazit projekt.

## <a name="writing-your-code"></a>Psaní kódu

Pojďme začít vytvořením kódu jako prvního.  Ujistěte se, že je soubor `Program.fs` otevřený, a pak jeho obsah nahraďte následujícím:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

V předchozím příkladu kódu byla definována funkce `square`, která přebírá vstup s názvem `x` a vynásobí jej sebou samým.  Vzhledem F# k tomu, že používá [odvození typu](../language-reference/type-inference.md), není nutné zadat typ `x`.  F# Kompilátor rozumí typům, kde je násobení platné, a přiřadí typ k `x` na základě toho, jak je volána `square`.  Pokud najedete myší na `square`, měli byste vidět následující:

```fsharp
val square: x:int -> int
```

Jedná se o to, co se říká signatura typu funkce.  Dá se číst takto: "čtvercem je funkce, která přebírá celé číslo s názvem x a vytváří celé číslo".  Všimněte si, že kompilátor `square` typ `int` pro tuto skutečnost, protože násobení není obecné napříč *všemi* typy, ale spíše je obecné napříč uzavřenou sadou typů.  F# Kompilátor vybral `int` v tomto okamžiku, ale upraví signaturu typu, pokud voláte `square` s jiným typem vstupu, jako je například `float`.

Je definována jiná funkce, `main`, která je upravena pomocí atributu `EntryPoint`, aby informovala F# kompilátor, že by měl spustit program pro spuštění programu.  Řídí se stejnou konvencí jako jiné [programovací jazyky ve stylu jazyka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku lze předat této funkci a je vrácen celočíselný kód (obvykle `0`).

Je v této funkci, která volá funkci `square` s argumentem `12`.  F# Kompilátor potom přiřadí typ `square`, který se má `int -> int` (to znamená funkce, která přijímá `int` a vytvoří `int`).  Volání `printfn` je naformátovaná funkce pro tisk, která používá formátovací řetězec, podobně jako programovací jazyky ve stylu jazyka C, parametry, které odpovídají těm, které jsou zadány ve formátu řetězce, a pak vypíše výsledek a nový řádek.

## <a name="running-your-code"></a>Spuštění kódu

Můžete spustit kód a zobrazit výsledky stisknutím **kombinace kláves Ctrl**+**F5**.  Tím se spustí program bez ladění a umožní vám zobrazit výsledky.  Alternativně můžete zvolit položku nabídky nejvyšší úrovně **ladění** v aplikaci Visual Studio a zvolit možnost **Spustit bez ladění**.

Nyní byste měli vidět následující vytištěné okno konzoly, ve kterém se zobrazila aplikace Visual Studio:

```console
12 squared is 144!
```

Blahopřejeme!  Vytvořili jste svůj první F# projekt v aplikaci Visual Studio, napsali F# jste funkci, která vytiskla výsledky volání této funkce, a spustí projekt, aby se zobrazily nějaké výsledky.

## <a name="next-steps"></a>Další kroky

Pokud jste to ještě neudělali, podívejte se na [prohlídku F# ](../tour.md), která se zabývá některými základními F# funkcemi daného jazyka.  Poskytne vám přehled o některých možnostech aplikace F#a poskytuje podrobné ukázky kódu, které můžete zkopírovat do sady Visual Studio a spustit.  Další informace o F# dokumentaci můžete také získat na [ F# domovské stránce docs](../index.yml).

## <a name="see-also"></a>Viz také:

- [Prohlídka jazyka F#](../tour.md)
- [F#Referenční dokumentace jazyka](../language-reference/index.md)
- [Odvození typu](../language-reference/type-inference.md)
- [Reference k symbolům a operátorovi](../language-reference/symbol-and-operator-reference/index.md)
