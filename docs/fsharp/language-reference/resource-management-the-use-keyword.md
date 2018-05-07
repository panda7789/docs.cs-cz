---
title: 'Správa prostředků: Klíčové slovo use (F#)'
description: "Další informace o F # – klíčové slovo 'použití' a 'pomocí, funkce, která můžete ovládat inicializace a verzi zdroje."
ms.date: 05/16/2016
ms.openlocfilehash: c75783080d1d87c6ee75aede500d3d0b3fdf8355
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="resource-management-the-use-keyword"></a>Správa prostředků: Klíčové slovo use

Toto téma popisuje klíčové slovo `use` a `using` funkce, které můžete ovládat inicializace a verzi zdroje.

## <a name="resources"></a>Prostředky
Termín *prostředků* se používá více než jedním způsobem. Ano, prostředky mohou být data, která používá aplikace, jako je například řetězce, grafiky a podobně, ale v tomto kontextu *prostředky* odkazuje na prostředky softwaru nebo operačního systému, například kontexty zařízení grafiky, obslužných rutin souborů síť a databáze připojení, objekty souběžnosti jako obslužné rutiny čekání atd. Použití těchto prostředků ve aplikace zahrnuje získání prostředků z operačního systému nebo jiných prostředků poskytovatele, následuje v novějších verzích prostředku do fondu, aby ho lze zadat do jiné aplikace. Pokud aplikace není uvolnění prostředků zpět do fondu běžné dojde k problémům.

## <a name="managing-resources"></a>Správa prostředků
Efektivní a jeho zodpovědné spravovat prostředky v aplikaci, je nutné uvolnit prostředky okamžitě a předvídatelný způsobem. Rozhraní .NET Framework, pomůže vám to tím, že poskytuje `System.IDisposable` rozhraní. Typ, který implementuje `System.IDisposable` má `System.IDisposable.Dispose` metodu, která správně uvolní prostředky. Správně vytvořené aplikace zaručit, že `System.IDisposable.Dispose` je volána okamžitě, když libovolný objekt, který obsahuje omezené prostředek již není potřeba. Naštěstí většině jazyků .NET poskytuje podporu pro zjednodušení a F # není žádná výjimka. Existují dva užitečné jazykové konstrukty, které podporují vzor uvolnění: `use` vazby a `using` funkce.

## <a name="use-binding"></a>Vazbu používají
`use` – Klíčové slovo má formulář, který se podobá se `let` vazby:

použít *hodnotu* = *výraz*

Poskytuje stejné funkce jako `let` vazby, ale přidá volání `Dispose` na hodnotu, pokud hodnota mimo rozsah. Všimněte si, že kompilátor vloží kontrolu hodnotu null na základě hodnoty, že pokud je hodnota `null`, volání `Dispose` není pokus.

Následující příklad ukazuje, jak zavřít soubor automaticky pomocí `use` – klíčové slovo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
Můžete použít `use` v výpočetní výrazy, v takovém případě přizpůsobená verze `use` použit výraz. Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výpočetní výrazy](computation-expressions.md).


## <a name="using-function"></a>pomocí funkce
`using` Funkce má následující formát:

`using` (*expression1*) *funkce nebo lambda*

V `using` výrazu *expression1* vytvoří objekt, který je nutné odstranit. Výsledek *expression1* (objekt, který je nutné odstranit) se změní na argument, *hodnotu*do *funkce nebo lambda*, který je buď funkci, která očekává jedné argument typu, který odpovídá hodnotě zbývající vyprodukované *expression1*, nebo výrazu lambda, která očekává argument daného typu. Na konci provádění funkce volá modul runtime `Dispose` a uvolní prostředky (Pokud není hodnota `null`, v takovém případě není pokus o volání metody Dispose).

Následující příklad ukazuje `using` výraz s výrazem lambda.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

Další příklad ukazuje `using` výraz obsahující funkci.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Upozorňujeme, že funkce může být funkci, která má některé argumenty již použita. Následující příklad kódu ukazuje to. Vytvoří soubor, který obsahuje řetězec `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` Funkce a `use` vazby způsoby téměř ekvivalentní totéž provést. `using` – Klíčové slovo poskytuje větší kontrolu nad tím, kdy `Dispose` je volána. Při použití `using`, `Dispose` nazývá na konci výrazu funkce nebo lambda; při použití `use` – klíčové slovo, `Dispose` nazývá na konci jsou obsaženy v bloku kódu. Obecně platí, měli byste radši chtěli použít `use` místo `using` funkce.


## <a name="see-also"></a>Viz také
[Referenční dokumentace jazyka F#](index.md)
