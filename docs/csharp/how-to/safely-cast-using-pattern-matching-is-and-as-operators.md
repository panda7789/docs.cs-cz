---
title: 'Postupy: Bezpečné přetypování pomocí porovnávání vzorů a operátorů is a as'
description: Naučte se používat techniky porovnávání vzorů k bezpečnému přetypování proměnných na jiný typ. Můžete použít porovnávání vzorů a také operátory is a as pro bezpečné převod typů.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 764a69869b8a5b8f76e2f58aced51761af73e50e
ms.sourcegitcommit: 29a9b29d8b7d07b9c59d46628da754a8bff57fa4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2019
ms.locfileid: "69566287"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Postupy: Bezpečné přetypování pomocí porovnávání vzorů a operátorů is a as

Vzhledem k tomu, že objekty jsou polymorfní, je možné, že proměnná typu základní třídy bude uchovávat odvozený [typ](../programming-guide/types/index.md). Chcete-li získat přístup ke členům instance odvozeného typu, je nutné [přetypovat](../programming-guide/types/casting-and-type-conversions.md) hodnotu zpět na odvozený typ. Přetypování však vytvoří riziko vyvolání <xref:System.InvalidCastException>. C#poskytuje příkazy pro [porovnávání vzorů](../pattern-matching.md) , které provádějí přetypování podmíněně pouze v případě, že budou úspěšné. C#také poskytuje operátor [is](../language-reference/operators/type-testing-and-cast.md#is-operator) a [as](../language-reference/operators/type-testing-and-cast.md#as-operator) k testování, zda je hodnota určitého typu.

Následující kód demonstruje příkaz pro `is` porovnávání se vzorem. Obsahuje metody, které testují argument metody pro určení, zda se jedná o jeden z možných odvozených typů:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Předchozí příklad ukazuje několik funkcí syntaxe porovnávání vzorů. Příkazy `if (a is Mammal m)` a`if (o is Mammal m)` spojují test s přiřazením inicializace. Přiřazení probíhá pouze v případě, že test proběhl úspěšně. Proměnná `m` je pouze v oboru vloženého `if` příkazu, kde byla přiřazena. Ke stejné metodě `m` nemůžete získat přístup později. Zkuste to v interaktivním okně.

Můžete také použít stejnou syntaxi pro testování, pokud typ s [možnou hodnotou null](../programming-guide/nullable-types/index.md) má hodnotu, jak je znázorněno v následujícím ukázkovém kódu:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Předchozí příklad ukazuje další funkce porovnávání vzorů pro použití s převody. Můžete otestovat proměnnou pro vzorec null tak, že zkontrolujete specifickou `null` hodnotu. Pokud je `null`běhová hodnota proměnné `is` , kontrola příkazu pro typ vždy vrátí `false`. Příkaz porovnávání `is` vzorů nepovoluje typ hodnoty s možnou hodnotou null `int?` , `Nullable<int>`jako je například nebo, ale můžete ho otestovat na jakýkoli jiný typ hodnoty.

Předchozí ukázka také ukazuje, jak použít výraz porovnávání `is` vzorů `switch` v příkazu, kde proměnná může být jedním z mnoha různých typů.

Pokud chcete otestovat, zda je proměnná daný typ, ale nechcete ji přiřadit k nové proměnné, můžete použít `is` operátory a `as` pro typy odkazů a typy s možnou hodnotou null. Následující kód ukazuje, jak použít `is` příkazy a `as` , které byly součástí C# jazyka před tím, než byly zavedeny vzorové porovnávání za účelem testování, zda je proměnná daného typu:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak vidíte pomocí porovnání tohoto kódu s kódem porovnávání vzorů, syntaxe porovnávání vzorů poskytuje robustnější funkce kombinací testu a přiřazení v rámci jednoho příkazu. Pokud je to možné, použijte syntaxi porovnávání vzorů.

Tyto ukázky můžete vyzkoušet na základě kódu v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Nebo si můžete stáhnout ukázky [jako soubor zip](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
