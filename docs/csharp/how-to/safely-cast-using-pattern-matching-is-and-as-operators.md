---
title: Jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů is a as
description: Naučte se používat techniky porovnávání vzorů k bezpečnému přetypování proměnných na jiný typ. Můžete použít porovnávání vzorů a také operátory is a as pro bezpečné převod typů.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 762f8135063f7256ce7a167c65013703d9249039
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973096"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů is a as

Vzhledem k tomu, že objekty jsou polymorfní, je možné, že proměnná typu základní třídy bude uchovávat odvozený [typ](../programming-guide/types/index.md). Chcete-li získat přístup ke členům instance odvozeného typu, je nutné [přetypovat](../programming-guide/types/casting-and-type-conversions.md) hodnotu zpět na odvozený typ. Přetypování však vytvoří riziko vyvolání <xref:System.InvalidCastException>. C#poskytuje příkazy pro [porovnávání vzorů](../pattern-matching.md) , které provádějí přetypování podmíněně pouze v případě, že budou úspěšné. C#také poskytuje operátor [is](../language-reference/operators/type-testing-and-cast.md#is-operator) a [as](../language-reference/operators/type-testing-and-cast.md#as-operator) k testování, zda je hodnota určitého typu.

Následující kód demonstruje `is` příkazu porovnávání vzorů. Obsahuje metody, které testují argument metody pro určení, zda se jedná o jeden z možných odvozených typů:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Předchozí příklad ukazuje několik funkcí syntaxe porovnávání vzorů. Příkazy `if (a is Mammal m)` a `if (o is Mammal m)` spojují test s přiřazením inicializace. Přiřazení probíhá pouze v případě, že test proběhl úspěšně. Proměnná `m` je v rozsahu vloženého příkazu `if` pouze v případě, že byl přiřazen. Ke `m` později ve stejné metodě nemáte přístup. Zkuste to v interaktivním okně.

Můžete také použít stejnou syntaxi pro testování, pokud [typ hodnoty s možnou hodnotou null](../language-reference/builtin-types/nullable-value-types.md) má hodnotu, jak je znázorněno v následujícím ukázkovém kódu:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Předchozí příklad ukazuje další funkce porovnávání vzorů pro použití s převody. Můžete otestovat proměnnou pro vzor null tím, že zkontrolujete specifickou hodnotu `null`. Pokud je běhová hodnota proměnné `null`, kontrola příkazu `is` pro typ vždy vrátí `false`. Příkaz `is` porovnávání vzorů nepovoluje typ hodnoty s možnou hodnotou null, například `int?` nebo `Nullable<int>`, ale můžete ho otestovat pro jakýkoli jiný typ hodnoty. Vzorce `is` z předchozího příkladu nejsou omezeny na typy hodnot s možnou hodnotou null. Tyto vzory můžete také použít k otestování, zda proměnná typu odkazu má hodnotu nebo je `null`.

Předchozí ukázka také ukazuje, jak použít `is` výraz porovnávání vzorů v příkazu `switch`, kde proměnná může být jedním z mnoha různých typů.

Pokud chcete otestovat, zda je proměnná daný typ, ale nechcete ji přiřadit k nové proměnné, můžete použít operátory `is` a `as` pro typy odkazů a typy s možnou hodnotou null. Následující kód ukazuje, jak použít `is` a `as` příkazy, které byly součástí C# jazyka před zavedením vzorového porovnávání za účelem testování, zda je proměnná daného typu:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak vidíte pomocí porovnání tohoto kódu s kódem porovnávání vzorů, syntaxe porovnávání vzorů poskytuje robustnější funkce kombinací testu a přiřazení v rámci jednoho příkazu. Pokud je to možné, použijte syntaxi porovnávání vzorů.

Tyto ukázky můžete vyzkoušet na základě kódu v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
