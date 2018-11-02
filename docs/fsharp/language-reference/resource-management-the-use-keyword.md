---
title: 'Správa prostředků: Klíčové slovo use (F#)'
description: 'Další informace o F # – klíčové slovo "použití" a "pomocí" funkce, která můžete řídit, inicializace a uvolnění prostředků.'
ms.date: 05/16/2016
ms.openlocfilehash: ffa1cb515139a3705920d9d9f79be1a69602f7d8
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/02/2018
ms.locfileid: "45616059"
---
# <a name="resource-management-the-use-keyword"></a>Správa prostředků: Klíčové slovo use

Toto téma popisuje klíčové slovo `use` a `using` funkce, která můžete řídit, inicializace a uvolnění prostředků.

## <a name="resources"></a>Prostředky

Termín *prostředků* se používá více než jedním způsobem. Ano, prostředky můžou být data, která aplikace používá, jako jsou řetězce, grafiku a podobně, ale v tomto kontextu *prostředky* odkazuje na software nebo operační systém prostředky, jako je například kontexty zařízení grafiky, popisovače souborů, sítě a databáze připojení, objekty souběžnosti, jako je například obslužné rutiny čekání a tak dále. Využívání těchto prostředků v aplikacích zahrnuje získání prostředku z operačního systému nebo jiné poskytovatele prostředků, za nímž následuje v novějších verzích prostředku do fondu tak, aby je poskytnout jiná aplikace. Když aplikace není uvolnit prostředky zpět do společného fondu dojít k problémům.

## <a name="managing-resources"></a>Správa prostředků

Pokud chcete efektivně a zodpovědně spravovat prostředky v aplikaci, musí uvolnit prostředky o tom bezodkladně informuje a předvídatelným způsobem. Můžete to provést tím, že poskytuje rozhraní .NET Framework pomáhá `System.IDisposable` rozhraní. Typ, který implementuje `System.IDisposable` má `System.IDisposable.Dispose` metodu, která správně uvolní prostředky. Kvalitně napsané aplikace zaručit, že `System.IDisposable.Dispose` se okamžitě volá, když už nepotřebujete libovolný objekt, který obsahuje prostředek omezený. Naštěstí Většina jazyků .NET poskytují podporu pro lepší pochopení a F # není žádná výjimka. Existují dvě užitečné jazykovým konstrukcím, které podporují vzor dispose: `use` vazby a `using` funkce.

## <a name="use-binding"></a>Použít vazbu

`use` – Klíčové slovo má formulář, který vypadá podobně jako u `let` vazby:

použít *hodnotu* = *výraz*

Funguje stejně jako `let` vazby, ale přidá volání `Dispose` na hodnotu, pokud hodnota dostane mimo rozsah. Všimněte si, že kompilátor vloží kontrolu hodnot null na základě hodnoty tak, že pokud je hodnota `null`, volání `Dispose` nebyl prováděn.

Následující příklad ukazuje, jak automaticky zavřete soubor stisknutím kombinace kláves `use` – klíčové slovo.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
Můžete použít `use` ve výrazech výpočtu. v takovém případě přizpůsobenou verzi `use` výraz je použit. Další informace najdete v tématu [pořadí](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md), a [výrazech výpočtu](computation-expressions.md).

## <a name="using-function"></a>pomocí funkce

`using` Funkce má následující formát:

`using` (*expression1*) *lambda nebo funkce*

V `using` výrazu, *expression1* vytvoří objekt, který musí být odstraněn. Výsledek *expression1* (objekt, který musí být uvolněn) stane argument, *hodnotu*do *funkce nebo lambda*, což je buď funkci, která očekává, že jeden Zbývající argument typu, který se shoduje s hodnotou vytvářených *expression1*, nebo výraz lambda, který očekává argument daného typu. Na konci spuštění funkce, modul runtime volá `Dispose` a uvolní prostředky (Pokud není hodnota `null`, v takovém případě se pokus o volání metody Dispose).

Následující příklad ukazuje, `using` výrazem lambda výraz.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

Další příklad ukazuje `using` výraz s funkcí.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Všimněte si, že funkce může být funkce, která obsahuje některé argumenty již použity. Následující příklad kódu ukazuje to. Vytvoří soubor, který obsahuje řetězec `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` Funkce a `use` vazby jsou téměř ekvivalentní způsoby, jak provést totéž. `using` – Klíčové slovo poskytuje větší kontrolu nad tím, kdy `Dispose` je volána. Při použití `using`, `Dispose` je volána na konci funkce nebo lambda výraz; při použití `use` – klíčové slovo, `Dispose` je volána na konci bloku kódu. Obecně platí, měli byste radši chtěli použít `use` místo `using` funkce.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
