---
title: 'Začínáme s jazykem F # v sadě Visual Studio'
description: 'Další informace o použití F # pomocí sady Visual Studio.'
ms.date: 07/03/2018
ms.openlocfilehash: a4a12a322d7e5144f2d720541f6ef65ca12737dd
ms.sourcegitcommit: 59b51cd7c95c75be85bd6ef715e9ef8c85720bac
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37874712"
---
# <a name="get-started-with-f-in-visual-studio"></a>Začínáme s jazykem F # v sadě Visual Studio

F # a nástrojů Visual F # jsou podporovány v integrovaném vývojovém prostředí sady Visual Studio.

Pokud chcete začít, ujistěte se, že máte [s jazykem F # nainstalovanou sadu Visual Studio](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace

Jeden z nejzákladnější projektů v sadě Visual Studio je konzolová aplikace.  Tady je postup.  Jakmile se Visual Studio otevře:

1. Na **souboru** nabídky, přejděte k **nový**a klikněte na tlačítko **projektu**.

2.  V nový projekt dialogového okna, v části **šablony**, měli byste vidět **Visual F #**.  Zvolte možnost, pokud chcete zobrazit šablony F #.

3. Vyberte buď **.NET Core konzolovou aplikaci** nebo **konzolovou aplikaci**.

3. Zvolte **dobře** pro vytvoření projektu jazyka F #!  Teď byste měli vidět projektu F # v Průzkumníku řešení.

## <a name="writing-your-code"></a>Psaní kódu

Začněme napsáním nějakého kódu.  Ujistěte se, že `Program.fs` soubor je otevřený a potom nahraďte jeho obsah následujícím kódem:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

V předchozí ukázce kódu, funkce `square` byla definována desetinný vstup s názvem `x` a vynásobí samostatně.  Vzhledem k tomu F # používá [odvození typu](../language-reference/type-inference.md), typ `x` nemusí být zadán.  Kompilátor F # rozumí typy, kde je platný násobení a to typu `x` podle toho, jak `square` je volána.  Pokud najedete myší `square`, byste měli vidět následující:

```
val square: x:int -> int
```

Je to, co se označuje jako typ signatury funkce.  Může být číst takto: "čtverec je funkce, která přebírá celočíselným parametrem s názvem x a vytváří integer".  Všimněte si, že kompilátor přiřadil `square` `int` typ prozatím - totiž násobení není obecná napříč *všechny* typy, ale místo toho je obecný zavřené sadě typy.  Kompilátor F # vyberou `int` v tomto bodu, ale budou upraveny podpis typu při volání `square` s jiným typ vstupu, například `float`.

Další funkci `main`, je definován, která je upravena pomocí `EntryPoint` atribut spuštění tohoto programu předat kompilátor F # by se měl spustit existuje.  Řídí stejnou konvencí jako ostatní [programovacích jazyků C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde můžete předávat argumenty příkazového řádku pro tuto funkci a vrátí kód celé číslo (obvykle `0`).

Je v této funkce, které označujeme jako `square` funkci s argumentem `12`.  Poté přiřadí typ kompilátoru jazyka F # `square` bude `int -> int` (to znamená, funkce, která přebírá `int` a vytváří `int`).  Volání `printfn` je formátovaný tisk funkci, která používá řetězec formátu, podobně jako C-style programovacích jazyků, parametry, které odpovídají jsou uvedeny ve formátovacím řetězci a potom zobrazí výsledek a nový řádek.

## <a name="running-your-code"></a>Spuštění kódu

Můžete spustit kód a zobrazit výsledky stisknutím kombinace kláves **ctrl-f5**.  Tím se spustí program bez ladění a vám umožní vidět výsledky.  Alternativně můžete použít **ladění** nabídek nejvyšší úrovně položku v sadě Visual Studio a zvolte **spustit bez ladění**.

Teď byste měli vidět následující zobrazeny v okně konzoly, který Visual Studio odebrány nahoru:

```
12 squared is 144!
```

Blahopřejeme!  Jste vytvořili svůj první projekt F # v sadě Visual Studio, zapsat, že funkce jazyka F # vytisknout výsledky volání funkce a spuštění projektu zobrazíte některé výsledky.

## <a name="next-steps"></a>Další kroky

Pokud jste to ještě neudělali, podívejte se [Tour F #](../tour.md), která uvádí i některé základní funkce jazyka F #.  Bude vám poskytnou přehled o některé funkce jazyka F # a poskytovat ukázky ukázku kódu, které můžete zkopírovat do sady Visual Studio a spustit.  Existují také některé skvělé externí prostředky můžete použít, zobrazují v [Průvodce jazykem F #](../index.md).

## <a name="see-also"></a>Viz také:
 [Prohlídka jazyka F #](../tour.md) [referenční dokumentace jazyka F #](../language-reference/index.md) [odvození typu](../language-reference/type-inference.md) [referenční dokumentace symbolů a – operátor](../language-reference/symbol-and-operator-reference/index.md)
