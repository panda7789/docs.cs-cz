---
title: je - C# odkaz
ms.custom: seodec18
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: 45e37dcb15e178fe37907e00cc14ef48c1bf230d
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306596"
---
# <a name="is-c-reference"></a>is (Referenční dokumentace jazyka C#)

`is` Operátor zkontroluje, zda výsledek výrazu je kompatibilní s daným typem, nebo (počínaje C# 7.0) testuje výraz se vzorem. Informace o typu testování `is` operátor viz [je operátor](../operators/type-testing-and-conversion-operators.md#is-operator) část [typové zkoušky a převod operátorů](../operators/type-testing-and-conversion-operators.md) článku.

## <a name="pattern-matching-with-is"></a>Porovnávání vzorů s `is`

Od verze C# 7.0, `is` a [přepnout](switch.md) příkazy podpory porovnávání vzorů. `is` – Klíčové slovo podporuje následující způsoby:

- [Typ vzorku](#type-pattern), který testuje, jestli výraz lze převést na zadaný typ a, pokud jej lze přetypování pro proměnnou daného typu.

- [Konstantní vzorek](#constant-pattern), který testuje, jestli je výraz vyhodnocen jako na zadanou hodnotu konstanty.

- [vzor var](#var-pattern), shoda, který je vždy úspěšné a přiřazuje hodnotu výrazu nové místní proměnné.

### <a name="type-pattern"></a>Vzorek typu

Při použití typu modelu k provádění porovnávání vzorů, `is` testuje výraz lze převést na zadaný typ a pokud jej lze přetypování pro proměnnou daného typu. Je jednoduché rozšíření `is` příkaz, který umožňuje stručný typ vyhodnocení a převodu. Obecný tvar `is` vzor typu je:

```csharp
   expr is type varname
```

kde *expr* je výraz, který se vyhodnotí na instanci typu, *typ* je název typu, na který výsledek *expr* se má převést a *název_proměnné* je objekt, na který výsledek *expr* je převedena, pokud `is` test je `true`. 

`is` Výraz je `true` Pokud *expr* není `null`, a je splněna některá z následujících akcí:

- *výraz* je instance stejného typu jako *typ*.

- *výraz* je instance typu, který je odvozen od *typ*. Jinými slovy, výsledek *expr* může být k instanci povýšení *typ*.

- *výraz* má typ za kompilace, která je základní třídou *typ*, a *expr* má typ modulu runtime, který je *typ* nebo odvozený od *typ*. *Typu v době kompilace* proměnné je typ proměnné definované v jeho deklaraci. *Typu prostředí runtime* proměnné je typ instance, který je přiřazen k této proměnné.

- *výraz* je instance typu, který implementuje *typ* rozhraní.

Počínaje C# 7.1, *expr* může mít za kompilace typu definované v parametru obecného typu a jeho omezení.

Pokud *expr* je `true` a `is` se používá s `if` příkazu *název_proměnné* přiřazují v rámci `if` pouze příkaz. Rozsah *název_proměnné* z `is` výraz na konci uzavírající blok `if` příkazu. Pomocí *název_proměnné* v jiném umístění vygeneruje chybu kompilace pro použití proměnné, která nebyla přiřazena.

V následujícím příkladu `is` vzor typu k dispozici implementace typu <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez porovnávání vzorů, může být napsán takto následujícím způsobem. Použití porovnávání vzorů typu produkuje kompaktnějším čitelné kódu pomocí tím eliminuje nutnost otestovat, jestli je výsledek převodu `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

`is` Vzor typu také vytvoří kompaktnějším kód při určování typu hodnotového typu. V následujícím příkladu `is` vzor typu k určení, zda je objekt `Person` nebo `Dog` instance před zobrazením hodnota příslušné vlastnosti.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, který obsahuje explicitní přetypování.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Konstantní vzorek

Při provádění porovnávání vzorů s konstantní vzorek `is` testuje, zda výraz rovná zadané – konstanta. V jazyce C# 6 a starší verze, je podporován konstantní vzorek [přepnout](switch.md) příkazu. Počínaje C# 7.0, je podporována `is` také příkaz. Syntaxe je:

```csharp
   expr is constant
```

kde *expr* je výraz k vyhodnocení, a *konstantní* je hodnota pro testování. *konstantní* může být následující konstantní výrazy:

- Hodnota literálu.

- Název deklarovanou `const` proměnné.

- Konstanta výčtu.

Konstantní výraz je vyhodnocen následujícím způsobem:

- Pokud *expr* a *konstantní* integrální typy jsou operátor rovnosti jazyka C# určuje, zda výraz vrací `true` (to znamená, zda `expr == constant`).

- V opačném případě je hodnota výrazu určena voláním statické [funkci Object.Equals (expr, konstantní)](xref:System.Object.Equals(System.Object,System.Object)) metody.  

Následující příklad kombinuje typ a konstantní vzory k ověření, zda je objekt `Dice` instance, a pokud se jedná, k určení, zda dice kumulativní hodnotu 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Kontrola `null` je možné provádět pomocí konstantní vzorek. `null` – Klíčové slovo je podporován `is` příkazu. Syntaxe je:

```csharp
   expr is null
```

Následující příklad ukazuje porovnání `null` ověří:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>vzor var

`var` Vzor je pokrývající vše pro libovolným typem nebo hodnotou. Hodnota *expr* se vždycky přiřazuje lokální proměnná stejný typ jako typ času kompilace *expr*. Výsledkem `is` výraz je vždycky `true`. Syntaxe je:

```csharp
   expr is var varname
```

Následující příklad používá vzor var výrazu přiřazení k proměnné s názvem `obj`. Potom zobrazí hodnotu a typ `obj`.

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

## <a name="c-language-specification"></a>specifikace jazyka C#
  
Další informace najdete v tématu [je operátor](~/_csharplang/spec/expressions.md#the-is-operator) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md) a následující C# jazykové návrhy:

- [Porovnávání vzorů](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Porovnávání vzorů s obecnými typy](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typové zkoušky a převod operátorů](../operators/type-testing-and-conversion-operators.md)
