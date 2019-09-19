---
title: Začínáme s nástrojem F# v aplikaci Visual Studio
description: Naučte se používat F# se sadou Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: e573af67a1fc00b0a340f8c73ab1ee0ed2b97810
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082702"
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

Pojďme začít vytvořením kódu jako prvního.  Ujistěte se, že `Program.fs` je soubor otevřený, a pak jeho obsah nahraďte následujícím:

[!code-fsharp[HelloSquare](~/samples/snippets/fsharp/getting-started/hello-square.fs)]

V předchozím příkladu kódu byla definována funkce `square` , která přebírá vstup s názvem `x` a násobí ho sám sebou.  F# Vzhledem`x` k tomu, že používá [odvození typu](../language-reference/type-inference.md), není třeba zadávat typ.  F# Kompilátor rozumí typům, kde je násobení platné, a přiřadí typ `x` podle toho, jak `square` je volána.  Pokud najedete `square`myší na, měli byste vidět následující:

```fsharp
val square: x:int -> int
```

Jedná se o to, co se říká signatura typu funkce.  Dá se číst takto: "Square je funkce, která přebírá celé číslo s názvem x a vytvoří celé číslo".  Všimněte si, že kompilátor `square` tento `int` typ nyní přiřadil – je to proto, že násobení není obecné napříč *všemi* typy, ale spíše je obecné napříč uzavřenou sadou typů.  F# Kompilátor vybral `int` v tomto okamžiku, ale upraví signaturu typu, pokud voláte `square` s jiným typem vstupu, jako je `float`například.

Je definována jiná `main`funkce,,, která je upravena `EntryPoint` s atributem, aby F# informovala kompilátor, že by měl spustit program, který by měl spustit.  Odpovídá stejné konvenci jako jiné [programovací jazyky ve stylu jazyka C](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde argumenty příkazového řádku lze předat této funkci a je vrácen celočíselný kód (obvykle `0`).

Je touto funkcí, která volá `square` funkci s `12`argumentem.  F# Kompilátor potom `square` přiřadí typ `int -> int` , který `int` je (to znamená `int`funkce, která přijímá a vytvoří).  Volání je naformátovaná funkce pro `printfn` tisk, která používá formátovací řetězec, podobně jako programovací jazyky ve stylu jazyka C, parametry, které odpovídají těm, které jsou zadány ve formátu řetězce, a pak vytiskne výsledek a nový řádek.

## <a name="running-your-code"></a>Spuštění kódu

Můžete spustit kód a zobrazit výsledky stisknutím klávesy **CTRL**+**F5**.  Tím se spustí program bez ladění a umožní vám zobrazit výsledky.  Alternativně můžete zvolit položku nabídky nejvyšší úrovně **ladění** v aplikaci Visual Studio a zvolit možnost **Spustit bez ladění**.

Nyní byste měli vidět následující vytištěné okno konzoly, ve kterém se zobrazila aplikace Visual Studio:

```console
12 squared is 144!
```

Blahopřejeme!  Vytvořili jste svůj první F# projekt v aplikaci Visual Studio, napsali F# jste funkci, která vytiskla výsledky volání této funkce, a spustí projekt, aby se zobrazily nějaké výsledky.

## <a name="next-steps"></a>Další postup

Pokud jste to ještě neudělali, podívejte se na [prohlídku F# ](../tour.md), která se zabývá některými základními F# funkcemi daného jazyka.  Poskytne vám přehled o některých možnostech aplikace F#a poskytuje podrobné ukázky kódu, které můžete zkopírovat do sady Visual Studio a spustit.  K dispozici jsou také některé skvělé externí prostředky, které můžete použít v [ F# průvodci](../index.md).

## <a name="see-also"></a>Viz také:

- [Prohlídka jazyka F#](../tour.md)
- [F#Referenční dokumentace jazyka](../language-reference/index.md)
- [Odvození typu](../language-reference/type-inference.md)
- [Reference k symbolům a operátorovi](../language-reference/symbol-and-operator-reference/index.md)
