---
title: 'Postupy: bezpečné vícesměrového vysílání pomocí porovnávání vzorů a je a jako operátory'
description: Zjistěte, jak pomocí porovnávání vzorů techniky pro bezpečné přetypování proměnné jiného typu. Porovnávání vzorů můžete použít stejně jako je a jako operátory bezpečně převést typy.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 2e81628930afaca62a8614df8ca0f458238c23d6
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306350"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Postupy: bezpečné vícesměrového vysílání pomocí porovnávání vzorů a je a jako operátory

Protože objekty jsou polymorfní, je možné pro proměnné typu základní třídy pro uložení odvozený [typ](../programming-guide/types/index.md). Pro přístup ke členům instance odvozeného typu, je potřeba [přetypování](../programming-guide/types/casting-and-type-conversions.md) hodnotu zpět na odvozeného typu. Však přetypování vytvoří riziko vyvolání <xref:System.InvalidCastException>. Jazyk C# poskytuje [porovnávání vzorů](../pattern-matching.md) příkazy, které provést přetypování podmíněně jenom v případě, že proběhne úspěšně. C# obsahuje také [je](../language-reference/operators/type-testing-and-conversion-operators.md#is-operator) a [jako](../language-reference/operators/type-testing-and-conversion-operators.md#as-operator) operátory, který testuje, jestli je hodnota určitého typu.

Následující kód ukazuje porovnávání vzorů `is` příkazu. Obsahuje metody, které testují argumentu metody k určení, pokud je jedním z možných sadu odvozené typy:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Předchozí příklad znázorňuje několik funkcí syntaxe porovnávání vzoru. `if (a is Mammal m)` a `if (o is Mammal m)` příkazy v kombinaci s přiřazení inicializace testu. Přiřazení dochází, pouze pokud test proběhne úspěšně. Proměnná `m` jenom v oboru v vložený `if` příkaz, kde se přiřadila. Nejde získat přístup `m` dále v stejným způsobem. Vyzkoušejte v interaktivním okně.

Můžete také použít stejnou syntaxi pro testování, pokud je [typ připouštějící hodnotu Null](../programming-guide/nullable-types/index.md) má hodnotu, jak je znázorněno v následujícím ukázkovém kódu:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Předchozí příklad znázorňuje další prvky porovnávání vzorů pro použití s převody. Proměnné pro vzor null můžete otestovat tak, že zkontrolujete speciálně pro `null` hodnotu. Pokud je hodnota runtime proměnné `null`, `is` příkaz kontrolu pro typ vždy vrátí `false`. Porovnávání vzorů `is` příkaz nepovoluje jako typ s možnou hodnotou Null, `int?` nebo `Nullable<int>`, ale můžete testovat žádný jiný typ hodnoty.

V předchozím příkladu také ukazuje, jak použít porovnávání vzorů `is` výrazu `switch` příkaz, kde proměnná může být jedna z mnoha různých typů.

Pokud chcete otestovat, pokud je proměnná daného typu, ale ne přiřazení nové proměnné, můžete použít `is` a `as` operátory pro typy odkazů a typy připouštějící hodnotu Null. Následující kód ukazuje způsob použití `is` a `as` příkazy, které byly součástí jazyka C# před porovnávání vzorů byl zaveden, který testuje, jestli je proměnná daného typu:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak je vidět porovnáním tento kód s kódem odpovídající vzor syntaxe porovnávání vzoru poskytuje robustnější funkce kombinací testů a přiřazení v jediném příkazu. Použití porovnávání vzorů syntaxe, kdykoli je to možné.

Tyto ukázky můžete zkusit pohledem na kód v našich [úložiště GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
