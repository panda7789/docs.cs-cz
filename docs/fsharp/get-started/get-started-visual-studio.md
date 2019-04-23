---
title: Začínáme s F# v sadě Visual Studio
description: Další informace o použití F# pomocí sady Visual Studio.
ms.date: 07/03/2018
ms.openlocfilehash: 020e5d32b3aa5d5a2195c19d70d8fe684fbd56ef
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59331907"
---
# <a name="get-started-with-f-in-visual-studio"></a>Začínáme s F# v sadě Visual Studio

F#a vizuál F# nástroje jsou podporovány v integrovaném vývojovém prostředí sady Visual Studio.

Pokud chcete začít, ujistěte se, že máte [nainstalované sady Visual Studio s F# ](install-fsharp.md#install-f-with-visual-studio).

## <a name="creating-a-console-application"></a>Vytvoření konzolové aplikace

Jeden z nejzákladnější projektů v sadě Visual Studio je konzolová aplikace.  Tady je postup.  Jakmile se Visual Studio otevře:

1. Na **souboru** nabídky, přejděte k **nový**a klikněte na tlačítko **projektu**.

2. V nový projekt dialogového okna, v části **šablony**, měli byste vidět **Visual F#** .  Chcete-li zobrazit tuto možnost zvolte, F# šablony.

3. Vyberte buď **.NET Core konzolovou aplikaci** nebo **konzolovou aplikaci**.

3. Zvolte **dobře** tlačítko vytvoříte F# projekt!  Teď byste měli vidět F# projekt v Průzkumníku řešení.

## <a name="writing-your-code"></a>Psaní kódu

Začněme napsáním nějakého kódu.  Ujistěte se, že `Program.fs` soubor je otevřený a potom nahraďte jeho obsah následujícím kódem:

[!code-fsharp[HelloSquare](../../../samples/snippets/fsharp/getting-started/hello-square.fs)]

V předchozí ukázce kódu, funkce `square` byla definována desetinný vstup s názvem `x` a vynásobí samostatně.  Protože F# používá [odvození typu](../language-reference/type-inference.md), typ `x` nemusí být zadán.  F# Kompilátoru rozumí typy, kde je platný násobení a to typu `x` podle toho, jak `square` je volána.  Pokud najedete myší `square`, byste měli vidět následující:

```
val square: x:int -> int
```

Je to, co se označuje jako typ signatury funkce.  Najdete takto: "Čtverec je funkce, která přebírá celočíselným parametrem s názvem x a vytváří integer".  Všimněte si, že kompilátor přiřadil `square` `int` typ prozatím - totiž násobení není obecná napříč *všechny* typy, ale místo toho je obecný zavřené sadě typy.  F# Kompilátoru vyberou `int` v tomto bodu, ale budou upraveny podpis typu při volání `square` s jiným typ vstupu, například `float`.

Další funkci `main`, je definován, která je upravena pomocí `EntryPoint` atribut říct F# kompilátor, který provádění programu by se měl spustit existuje.  Řídí stejnou konvencí jako ostatní [programovacích jazyků C-style](https://en.wikipedia.org/wiki/Entry_point#C_and_C.2B.2B), kde můžete předávat argumenty příkazového řádku pro tuto funkci a vrátí kód celé číslo (obvykle `0`).

Je v této funkce, které označujeme jako `square` funkci s argumentem `12`.  F# Kompilátor poté přiřadí typu `square` bude `int -> int` (to znamená, funkce, která přebírá `int` a vytváří `int`).  Volání `printfn` je formátovaný tisk funkci, která používá řetězec formátu, podobně jako C-style programovacích jazyků, parametry, které odpovídají jsou uvedeny ve formátovacím řetězci a potom zobrazí výsledek a nový řádek.

## <a name="running-your-code"></a>Spuštění kódu

Můžete spustit kód a zobrazit výsledky stisknutím kombinace kláves **Ctrl**+**F5**.  To spustí program bez ladění a vám umožní vidět výsledky.  Alternativně můžete použít **ladění** nabídek nejvyšší úrovně položku v sadě Visual Studio a zvolte **spustit bez ladění**.

Teď byste měli vidět následující zobrazeny v okně konzoly, který Visual Studio odebrány nahoru:

```
12 squared is 144!
```

Blahopřejeme!  Vytvoření vaší první F# projektu v sadě Visual Studio, zapisovat F# funkce vytisknout výsledky volání funkce, které funkce a spuštění projektu zobrazíte některé výsledky.

## <a name="next-steps"></a>Další kroky

Pokud jste to ještě neudělali, podívejte se [prohlídka F# ](../tour.md), která uvádí i některé základní funkce F# jazyka.  Poskytne vám přehled některých možností F#a poskytnout ukázky ukázku kódu, které můžete zkopírovat do sady Visual Studio a spustit.  Existují také některé skvělé externí prostředky můžete použít, zobrazují v [ F# průvodce](../index.md).

## <a name="see-also"></a>Viz také:

- [Prohlídka jazyka F#](../tour.md)
- [F#referenční dokumentace jazyka](../language-reference/index.md)
- [Odvození typu](../language-reference/type-inference.md)
- [Referenční dokumentace symbolů a – operátor](../language-reference/symbol-and-operator-reference/index.md)
