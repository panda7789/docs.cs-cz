---
title: Jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů is a as
description: Naučte se používat techniky porovnávání vzorů k bezpečnému přetypování proměnných na jiný typ. Můžete použít porovnávání vzorů a také operátory is a as pro bezpečné převod typů.
ms.date: 09/05/2018
helpviewer_keywords:
- cast operators [C#], as and is operators
- as operator [C#]
- is operator [C#]
ms.openlocfilehash: f10ce837057cc61b84130f237a13af708849dfc5
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662963"
---
# <a name="how-to-safely-cast-by-using-pattern-matching-and-the-is-and-as-operators"></a>Jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů is a as

Vzhledem k tomu, že objekty jsou polymorfní, je možné, že proměnná typu základní třídy bude uchovávat odvozený [typ](../programming-guide/types/index.md). Chcete-li získat přístup ke členům instance odvozeného typu, je nutné [přetypovat](../programming-guide/types/casting-and-type-conversions.md) hodnotu zpět na odvozený typ. Přetypování však vytvoří riziko vyvolání <xref:System.InvalidCastException> . Jazyk C# poskytuje příkazy pro [porovnávání vzorů](../pattern-matching.md) , které provádějí přetypování podmíněně pouze v případě, že budou úspěšné. Jazyk C# také poskytuje operátory [is](../language-reference/operators/type-testing-and-cast.md#is-operator) a [as](../language-reference/operators/type-testing-and-cast.md#as-operator) k otestování, jestli je hodnota určitého typu.

Následující příklad ukazuje, jak použít příkaz pro porovnávání vzorů `is` :

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/patternmatching/Program.cs" id="PatternMatchingIs":::

Předchozí příklad ukazuje několik funkcí syntaxe porovnávání vzorů. `if (a is Mammal m)`Příkaz kombinuje test s přiřazením inicializace. Přiřazení probíhá pouze v případě, že test proběhl úspěšně. Proměnná `m` je pouze v oboru vloženého příkazu, `if` kde byla přiřazena. Ke stejné metodě nemůžete získat přístup `m` později. Předchozí příklad také ukazuje, jak použít [ `as` operátor](../language-reference/operators/type-testing-and-cast.md#as-operator) pro převod objektu na zadaný typ.

Můžete také použít stejnou syntaxi pro testování, pokud [typ hodnoty s možnou hodnotou null](../language-reference/builtin-types/nullable-value-types.md) má hodnotu, jak je znázorněno v následujícím příkladu:

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/nullablepatternmatching/Program.cs" id="PatternMatchingNullable":::

Předchozí příklad ukazuje další funkce porovnávání vzorů pro použití s převody. Můžete otestovat proměnnou pro vzorec null tak, že zkontrolujete specifickou `null` hodnotu. Pokud je běhová hodnota proměnné `null` , `is` Kontrola příkazu pro typ vždy vrátí `false` . Příkaz porovnávání vzorů `is` nepovoluje typ hodnoty s možnou hodnotou null, jako je například `int?` nebo `Nullable<int>` , ale můžete ho otestovat na jakýkoli jiný typ hodnoty. `is`Vzorce z předchozího příkladu nejsou omezeny na typy hodnot s možnou hodnotou null. Tyto vzory můžete také použít k otestování, zda proměnná typu odkazu má hodnotu nebo je `null` .

Předchozí ukázka také ukazuje, jak použít vzor typu v `switch` příkazu, kde proměnná může být jedním z mnoha různých typů.

Pokud chcete otestovat, zda je proměnná daný typ, ale nechcete ji přiřadit k nové proměnné, můžete použít `is` `as` operátory a pro typy odkazů a typy s možnou hodnotou null. Následující kód ukazuje, jak použít `is` `as` příkazy a, které byly součástí jazyka C# před zavedením vzorového porovnávání za účelem testování, zda je proměnná daného typu:

:::code language="csharp" source="../../../samples/snippets/csharp/how-to/safelycast/asandis/Program.cs" id="IsAndAs":::

Jak vidíte pomocí porovnání tohoto kódu s kódem porovnávání vzorů, syntaxe porovnávání vzorů poskytuje robustnější funkce kombinací testu a přiřazení v rámci jednoho příkazu. Pokud je to možné, použijte syntaxi porovnávání vzorů.
