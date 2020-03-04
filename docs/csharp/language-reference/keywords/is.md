---
title: je C# odkaz
ms.date: 06/21/2019
f1_keywords:
- is_CSharpKeyword
- is
helpviewer_keywords:
- is keyword [C#]
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
ms.openlocfilehash: a72f3b87e7558c594ef8a94bd0eadcc4664206b9
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239648"
---
# <a name="is-c-reference"></a>is (Referenční dokumentace jazyka C#)

Operátor `is` kontroluje, zda je výsledek výrazu kompatibilní s daným typem nebo (počínaje C# 7,0) testuje výraz na vzor. Informace o operátoru `is` testování typu naleznete v článku [operátor is](../operators/type-testing-and-cast.md#is-operator) pro [operátory typu testování a přetypování](../operators/type-testing-and-cast.md) .

## <a name="pattern-matching-with-is"></a>Porovnávání vzorů s `is`

Počínaje C# 7,0, příkazy `is` a [Switch](switch.md) podporují porovnávání vzorů. Klíčové slovo `is` podporuje následující vzory:

- [Vzor typu](#type-pattern), který testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování jej na proměnnou daného typu.

- [Konstantní vzor](#constant-pattern), který testuje, zda je výraz vyhodnocen na zadanou konstantní hodnotu.

- [var Pattern](#var-pattern), porovnávání, které vždy uspěje a váže hodnotu výrazu k nové místní proměnné.

### <a name="type-pattern"></a>Vzor typu

Při použití vzoru typu k provedení porovnávání se vzorem `is` testuje, zda lze výraz převést na zadaný typ a, pokud může být, přetypování na proměnnou daného typu. Je to jasné rozšíření příkazu `is`, které umožňuje vyhodnocování a konverzi stručných typů. Obecná forma `is`ho vzoru typu je:

```csharp
   expr is type varname
```

Kde *expr* je výraz, který je vyhodnocen jako instance nějakého typu, *typ* je název typu, na který má být výsledek *výrazu* převeden, a *název_proměnné* je objekt, na který je výsledek *výrazu* převeden, pokud je `is` test `true`. 

Výraz `is` je `true`, pokud *výraz* není `null`a kterákoli z následujících možností je pravdivá:

- *výraz* je instancí stejného typu jako *typ*.

- *expr* je instance typu, která je odvozena z *typu*. Jinými slovy výsledek *výrazu* lze přetypování na instanci *typu*.

- *výraz* má typ při kompilaci, který je základní třídou *typu*, a *výraz* má typ modulu runtime, který je *typu* nebo je odvozen z *typu*. *Typ v čase kompilace* proměnné je typ proměnné definovaný v jeho deklaraci. *Typ modulu runtime* proměnné je typ instance, která je přiřazena této proměnné.

- *expr* je instance typu, který implementuje rozhraní *typu* .

Počínaje C# 7,1, *expr* může být typ kompilace definovaný parametrem obecného typu a jeho omezeními.

Je-li *výraz expr* `true` a je-li `is` použit s příkazem `if`, je příkaz *název_proměnné* přiřazen pouze v rámci příkazu `if`. Rozsah *název_proměnné* je z výrazu `is` na konec bloku ohraničujícího příkaz `if`. Použití *název_proměnné* v jakémkoli jiném umístění generuje chybu při kompilaci pro použití proměnné, která nebyla přiřazena.

Následující příklad používá vzor typu `is` k poskytnutí implementace <xref:System.IComparable.CompareTo(System.Object)?displayProperty=nameWithType> metody typu.

[!code-csharp[is#5](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern5.cs#5)]

Bez porovnávání vzorů může být tento kód napsán následujícím způsobem. Použití porovnávání vzorů typů vytváří více kompaktních čitelných kódů tím, že eliminuje nutnost testovat, zda je výsledek převodu `null`.  

[!code-csharp[is#6](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern6.cs#6)]

Vzor typu `is` také při určování typu hodnoty vytvoří více kompaktního kódu. V následujícím příkladu je použit vzor typu `is` k určení, zda je objekt `Person` nebo instance `Dog` před zobrazením hodnoty příslušné vlastnosti.

[!code-csharp[is#9](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern9.cs#9)]

Ekvivalentní kód bez porovnávání vzorů vyžaduje samostatné přiřazení, které obsahuje explicitní přetypování.

[!code-csharp[is#10](../../../../samples/snippets/csharp/language-reference/keywords/is/is-type-pattern10.cs#10)]

### <a name="constant-pattern"></a>Konstantní vzorek

Při provádění porovnávání vzorů s konstantním vzorem `is` testuje, zda výraz odpovídá zadané konstantě. V C# 6 a starších verzích je konstantní vzorek podporován příkazem [Switch](switch.md) . Počínaje C# 7,0 se podporuje i příkaz `is`. Jeho syntaxe je:

```csharp
   expr is constant
```

kde *expr* je výraz, který se má vyhodnotit, a *konstanta* je hodnota, která se má testovat. *konstanta* může být libovolný z následujících konstantních výrazů:

- Hodnota literálu.

- Název deklarované `const` proměnné.

- Konstanta výčtu.

Konstantní výraz je vyhodnocen následujícím způsobem:

- Je *-li výraz* a *konstanta* integrální typy C# , operátor rovnosti určuje, zda výraz vrátí hodnotu `true` (tj. zda `expr == constant`).

- V opačném případě je hodnota výrazu určena voláním statické metody [Object. Equals (Expr, konstanta)](xref:System.Object.Equals(System.Object,System.Object)) .  

Následující příklad kombinuje vzorce typu a konstanty k otestování, zda je objekt `Dice` instance a, pokud je, k určení, zda je hodnota indexu vrácena 6.

[!code-csharp[is#7](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern7.cs#7)]

Kontrolu `null` lze provést pomocí konstantního vzoru. Klíčové slovo `null` je podporováno příkazem `is`. Jeho syntaxe je:

```csharp
   expr is null
```

Následující příklad ukazuje porovnání `null` kontroly:

[!code-csharp[is#11](../../../../samples/snippets/csharp/language-reference/keywords/is/is-const-pattern11.cs#11)]

### <a name="var-pattern"></a>variabilní vzorek

Vzor porovnávání se vzorem `var` vždy proběhne úspěšně. Jeho syntaxe je:

```csharp
   expr is var varname
```

Kde hodnota *expr* je vždy přiřazena místní proměnné s názvem *název_proměnné*. *název_proměnné* je proměnná stejného typu jako typ *výrazu*při kompilaci. 

Pokud je *výraz* vyhodnocen jako `null`, výraz `is` vytvoří `true` a přiřadí `null` k *název_proměnné*. Vzor var je jedno z několika použití `is`, které vytváří `true` pro `null` hodnotu.

Pomocí vzoru `var` lze vytvořit dočasnou proměnnou v rámci logického výrazu, jak ukazuje následující příklad:

[!code-csharp[is#8](../../../../samples/snippets/csharp/language-reference/keywords/is/is-var-pattern8.cs#8)]

V předchozím příkladu se dočasná proměnná používá k uložení výsledku nákladné operace. Proměnnou je pak možné použít několikrát.

## <a name="c-language-specification"></a>specifikace jazyka C#
  
Další informace najdete v části [operátor is](~/_csharplang/spec/expressions.md#the-is-operator) v tématu [ C# specifikace jazyka](~/_csharplang/spec/introduction.md) a v následujících C# jazykových návrzích:

- [Porovnávání vzorů](~/_csharplang/proposals/csharp-7.0/pattern-matching.md)
- [Porovnávání vzorů s obecnými typy](~/_csharplang/proposals/csharp-7.1/generics-pattern-match.md)
  
## <a name="see-also"></a>Viz také

- [C#odkaz](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Operátory testování typů a přetypování](../operators/type-testing-and-cast.md)
