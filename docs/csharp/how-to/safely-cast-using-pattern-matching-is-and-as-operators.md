---
title: Jak bezpečně obsazení pomocí porovnávání vzorů a je a jako operátory
description: Naučte se používat techniky porovnávání vzorů k bezpečnému přetypování proměnných na jiný typ. Můžete použít porovnávání vzorů, stejně jako is a jako operátory bezpečně převést typy.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: 34c34865a2feece5fe037daeb035292aafd015b9
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249354"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Jak bezpečně obsazení pomocí porovnávání vzorů a je a jako operátory

Protože objekty jsou polymorfní, je možné, aby proměnná typu základní třídy držela odvozený [typ](../programming-guide/types/index.md). Pro přístup k členům instance odvozeného typu je nutné [přetypovat](../programming-guide/types/casting-and-type-conversions.md) hodnotu zpět na odvozený typ. Obsazení však vytváří riziko vyvolání <xref:System.InvalidCastException>. C# poskytuje [příkazy porovnávání vzorů,](../pattern-matching.md) které provádějí přetypování podmíněně pouze v případě, že bude úspěšné. C# také poskytuje [is](../language-reference/operators/type-testing-and-cast.md#is-operator) a [jako](../language-reference/operators/type-testing-and-cast.md#as-operator) operátory k testování, pokud je hodnota určitého typu.

Následující příklad ukazuje, jak používat `is` příkaz odpovídající vzorek:

[!code-csharp[Pattern matching is statement](../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs#PatternMatchingIs)]

Předchozí ukázka ukazuje několik funkcí syntaxe porovnávání vzorů. Příkaz `if (a is Mammal m)` kombinuje test s přiřazení inicializace. Přiřazení dochází pouze v případě, že test proběhne úspěšně. Proměnná `m` je pouze v oboru `if` v vloženém příkazu, kde byla přiřazena. Nelze získat `m` přístup později ve stejné metodě. Předchozí příklad také ukazuje, jak použít [ `as` operátor](../language-reference/operators/type-testing-and-cast.md#as-operator) k převodu objektu na zadaný typ.

Stejnou syntaxi můžete použít také pro testování, pokud má [hodnotu s možnou hodnotou s hodnotou s možnou hodnotou,](../language-reference/builtin-types/nullable-value-types.md) jak je znázorněno v následujícím příkladu:

[!code-csharp[Pattern matching with nullable types](../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs#PatternMatchingNullable)]

Předchozí ukázka ukazuje další funkce porovnávání vzorů pro použití s převody. Můžete otestovat proměnnou pro vzorek null kontrolou `null` konkrétně pro hodnotu. Pokud je `null`hodnota runtime proměnné `is` , příkaz kontrolu pro `false`typ vždy vrátí . Příkaz porovnávání `is` vzorů neumožňuje typ hodnoty s `int?` možnou hodnotou s hodnotou, kterou lze upustit, například nebo `Nullable<int>`, ale můžete otestovat jakýkoli jiný typ hodnoty. Vzory `is` z předchozího příkladu nejsou omezeny na typy hodnot s hodnotou null. Tyto vzorky můžete také použít k testování, pokud má proměnná `null`typu odkazu hodnotu nebo je .

Předchozí ukázka také ukazuje, jak použít `switch` vzorek typu v příkazu, kde proměnná může být jeden z mnoha různých typů.

Pokud chcete otestovat, zda je proměnná daný typ, ale nepřiřaďte ji nové proměnné, můžete použít `is` operátory a `as` pro typy odkazů a typy hodnot s možnou hodnotou, kterou lze použít. Následující kód ukazuje, jak `is` `as` používat příkazy a, které byly součástí jazyka C# před porovnávání vzorů byla zavedena k testování, pokud proměnná je daného typu:

[!code-csharp[testing variable types with the is and as statements](../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs#IsAndAs)]

Jak můžete vidět porovnáním tohoto kódu s kódem porovnávání vzorů, syntaxe porovnávání vzorů poskytuje robustnější funkce kombinací testu a přiřazení v jednom příkazu. Pokud je to možné, použijte syntaxi porovnávání vzorů.

Tyto ukázky můžete vyzkoušet tak, že se podíváte na kód v našem [úložišti GitHub](https://github.com/dotnet/samples/tree/master/snippets/csharp/how-to/safelycast). Nebo si můžete stáhnout ukázky [jako zip soubor](https://github.com/dotnet/samples/raw/master/snippets/csharp/how-to/safelycast.zip).
