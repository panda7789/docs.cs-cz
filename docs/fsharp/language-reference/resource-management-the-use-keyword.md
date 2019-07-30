---
title: 'Správa prostředků: Klíčové slovo use'
description: Přečtěte si F# o klíčovém slově use a funkci using, která může řídit inicializaci a vydání prostředků.
ms.date: 05/16/2016
ms.openlocfilehash: 5e0838401bee02050343b2f6dcc646a8dc8b4dc0
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627254"
---
# <a name="resource-management-the-use-keyword"></a>Správa prostředků: Klíčové slovo use

Toto téma popisuje klíčové slovo `use` `using` a funkci, která může řídit inicializaci a vydání prostředků.

## <a name="resources"></a>Prostředky

Pojem *prostředku* je používán více než jedním způsobem. Ano, prostředky mohou být data, která aplikace používá, jako jsou například řetězce, grafika a podobně, ale v tomto kontextu *prostředky* odkazují na prostředky softwaru nebo operačního systému, jako jsou například kontexty grafických zařízení, popisovače souborů, síť a databáze. připojení, objekty souběžnosti, například obslužné rutiny čekání a tak dále. Použití těchto prostředků podle aplikací zahrnuje získání prostředku z operačního systému nebo jiného poskytovatele prostředků, za nímž následuje pozdější vydání prostředku, aby bylo možné ho poskytnout jiné aplikaci. K problémům dochází, když aplikace neuvolní prostředky zpátky do společného fondu.

## <a name="managing-resources"></a>Správa prostředků

Aby bylo možné efektivně a zodpovědnou spravovat prostředky v aplikaci, je třeba uvolnit prostředky bez výzvy a předvídatelným způsobem. .NET Framework to usnadňuje tím, že poskytuje `System.IDisposable` rozhraní. Typ, který implementuje `System.IDisposable` , `System.IDisposable.Dispose` má metodu, která správně uvolňuje prostředky. Správné zapsané aplikace zaručují, `System.IDisposable.Dispose` že se říká výzva, když už nebude potřeba libovolný objekt, který obsahuje omezený prostředek. Naštěstí většina jazyků .NET poskytuje podporu, aby to bylo snazší, a F# nejedná se o žádnou výjimku. Existují dvě užitečné jazykové konstrukce, které podporují vzor Dispose: `use` vazbu `using` a funkci.

## <a name="use-binding"></a>použití vazby

Klíčové slovo má formulář, který se podobá `let` vazbě: `use`

*výraz* použití *hodnoty* = 

Poskytuje stejné funkce jako `let` vazby, ale přidává `Dispose` volání na hodnotu, když se hodnota překročí rozsahu. Všimněte si, že kompilátor vloží u hodnoty hodnotu null, takže pokud je `null`hodnota, `Dispose` volání není prováděno.

Následující příklad ukazuje, jak automaticky zavřít soubor pomocí `use` klíčového slova.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

> [!NOTE]
> Můžete použít `use` ve výrazech výpočtu. v takovém případě se používá přizpůsobená verze `use` výrazu. Další informace najdete v tématu [sekvence](sequences.md), [asynchronní pracovní postupy](asynchronous-workflows.md)a [výpočetní výrazy](computation-expressions.md).

## <a name="using-function"></a>použití funkce

`using` Funkce má následující tvar:

`using`(*expression1*) *Function nebo lambda*

Ve výrazu Výraz1 vytvoří objekt, který musí být uvolněn. `using` Výsledek *Výraz1* (objekt, který musí být vyřazen), se může jednat o argument, *hodnotu*, *funkci nebo-lambda*, což je funkce, která očekává jeden zbývající argument typu, který odpovídá hodnotě vytvořené  *Výraz1*nebo lambda výraz, který očekává argument tohoto typu. Na konci provádění funkce zavolá `Dispose` modul runtime a uvolní prostředky (Pokud hodnota není `null`, v takovém případě se volání metody Dispose nezkouší).

Následující příklad ukazuje `using` výraz s výrazem lambda.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

Následující příklad ukazuje `using` výraz s funkcí.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Všimněte si, že funkce může být funkce, která již používá některé argumenty. Následující příklad kódu to demonstruje. Vytvoří soubor, který obsahuje řetězec `XYZ`.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` Funkce`use` a vazba jsou skoro ekvivalentní způsob, jak dosáhnout stejné věci. Klíčové slovo poskytuje větší kontrolu nad tím `Dispose` , kdy je volána. `using` Když použijete `using`, `Dispose` je volána na konci funkce nebo výrazu lambda `use` ; při použití klíčového slova `Dispose` je volána na konci obsahujícího bloku kódu. Obecně byste měli raději použít `use` místo `using` funkce.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka F#](index.md)
