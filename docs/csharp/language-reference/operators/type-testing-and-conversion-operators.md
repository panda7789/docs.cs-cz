---
title: Typové zkoušky a převod operators – C# odkaz
description: Další informace o C# operátory, které můžete použít ke kontrole typu výsledek výrazu a v případě potřeby ji převést na jiného typu.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: a9e5139e6d650aa6935bff934ca25502fdc14775
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744070"
---
# <a name="type-testing-and-conversion-operators-c-reference"></a>Typové zkoušky a převod operátorů (C# odkaz)

K provedení kontroly typu nebo konverze typu můžete použít následující operátory:

- [je operátor](#is-operator): Chcete-li zkontrolovat, jestli je kompatibilní s daným typem modulu runtime typu výrazu
- [jako operátor](#as-operator): k explicitnímu převodu výrazu na daný typ, pokud je jeho typ runtime kompatibilní s tímto typem
- [přetypování () operátor](#cast-operator-): k provedení explicitního převodu
- [operátor typeof](#typeof-operator): získání <xref:System.Type?displayProperty=nameWithType> instance typu

## <a name="is-operator"></a>is – operátor

`is` Operátor ověří, zda modul runtime typu výsledek výrazu kompatibilní s daným typem. Počínaje C# 7.0, `is` operátor také testy výsledek výrazu se vzorem.

Výraz s typové zkoušky `is` operátor má následující podobu.

```csharp
E is T
```

kde `E` je výraz, který vrací hodnotu a `T` je název typu nebo parametrem typu. `E` nemůže být anonymní metody nebo výrazu lambda.

`E is T` Výraz vrátí `true` Pokud výsledek `E` je jiná než null a je možné převést na typ `T` převod odkazu, převodu zabalení nebo unboxingového převodu; v opačném případě vrátí `false`. `is` Operátor nebere v úvahu uživatelem definovaných převodů.

Následující příklad ukazuje, že `is` operátor vrátí `true` Pokud běhového typu výsledek výrazu je odvozena z daného typu, to znamená, že existuje odkaz na převod mezi typy:

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Následující příklad ukazuje, že `is` operátor bere v úvahu zabalení a rozbalení převody, ale nezahrne číselných převodů:

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Informace o C# převody, naleznete v tématu [převody](~/_csharplang/spec/conversions.md) kapitoly [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Typ testování pomocí porovnávání vzorů

Počínaje C# 7.0, `is` operátor také testy výsledek výrazu se vzorem. Konkrétně se podporuje vzor typu v následujícím tvaru:

```csharp
E is T v
```

kde `E` je výraz, který vrátí hodnotu, která `T` je název typu nebo parametr typu a `v` je nová místní proměnná typu `T`. Pokud výsledek `E` je jiná než null a je možné převést na `T` odkazem, zabalení a rozbalení převodu `E is T v` výraz vrátí `true` a převedená hodnota výsledku `E` přiřazen Proměnná `v`.

Následující příklad ukazuje použití `is` operátor se vzorem typu:

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Další informace o typu model a jiné podporované vzory najdete v tématu [porovnávání vzorů s je](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>jako operátor

`as` Operátor explicitně převádí výsledek výrazu na daný odkaz nebo typ s možnou hodnotou Null. Pokud převod není možné, `as` operátor vrátí `null`. Na rozdíl od [přetypování () operátor](#cast-operator-), `as` operátor nikdy nevyvolá výjimku.

Výraz tvaru

```csharp
E as T
```

kde `E` je výraz, který vrací hodnotu a `T` je název typu nebo parametr typu, vytvoří stejný výsledek jako

```csharp
E is T ? (T)(E) : (T)null
```

s tím rozdílem, že `E` se jenom vyhodnotí jednou.

`as` Operátor bere v úvahu jenom převody odkazů, s možnou hodnotou Null, zabalení a rozbalení. Nelze použít `as` operátor uživatelsky definovaný převod. Chcete-li to mohli udělat, použijte [přetypování () operátor](#cast-operator-).

Následující příklad ukazuje použití `as` operátor:

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Jak ukazuje předchozí příklad, potřebujete porovnat výsledek `as` výraz s `null` ke kontrole, pokud převod není úspěšná. Počínaje C# 7.0, můžete použít [je operátor](#type-testing-with-pattern-matching) i k testování v případě, že převod je úspěšný, a pokud se aktivace podaří, přiřadit výsledek do nové proměnné.

## <a name="cast-operator-"></a>Operátor přetypování)

Přetypování výrazu v podobě `(T)E` provádí explicitní převod výsledku výrazu `E` na typ `T`. Pokud neexistuje žádný explicitní převod z typu `E` na typ `T`, dojde k chybě kompilace. V době běhu by se nemusela podařit explicitní převod a výraz přetypování může vyvolat výjimku.

Následující příklad ukazuje explicitní převody číselné a odkaz:

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Informace o podporovaných explicitní převody, naleznete v tématu [explicitních převodů](~/_csharplang/spec/conversions.md#explicit-conversions) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md). Informace o tom, jak definovat vlastní typ explicitní nebo implicitní převod, naleznete v tématu [uživatelsky definovaný převod operátorů](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Další využití)

Také při použití závorek k [volání metody nebo vyvolat delegáta](member-access-operators.md#invocation-operator-).

Další závorky slouží k určení pořadí, ve kterém se má vyhodnotit operací ve výrazu. Další informace najdete v tématu [závorek](../../programming-guide/statements-expressions-operators/operators.md#adding-parentheses) část [operátory](../../programming-guide/statements-expressions-operators/operators.md) článku. Seznam operátorů seřazené podle úrovně priority, naleznete v tématu [ C# operátory](index.md).

## <a name="typeof-operator"></a>typeof – operátor

`typeof` Získá operátor <xref:System.Type?displayProperty=nameWithType> instanci typu. Argument `typeof` operator musí být název typu nebo parametr typu, jako v následujícím příkladu:

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

Můžete také použít `typeof` operátor s nevázaného obecných typů. Název nevázaný parametr generického typu musí obsahovat odpovídající počet čárkami, které je menší než počet parametrů typu. Následující příklad ukazuje použití `typeof` operátor s nevázaný parametr generického typu:

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Výraz nemůže být argument `typeof` operátor. Chcete-li získat <xref:System.Type?displayProperty=nameWithType> instance modulu runtime typu výsledku výrazu, použijte <xref:System.Object.GetType%2A?displayProperty=nameWithType> – metoda.

### <a name="type-testing-with-the-typeof-operator"></a>Typ testování se `typeof` – operátor

Použití `typeof` operátor ke kontrole, pokud modul runtime typu výsledku výrazu přesně odpovídá daného typu. Následující příklad ukazuje rozdíl mezi kontrola typu pomocí provádí `typeof` operátor a [je operátor](#is-operator):

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Overloadability – operátor

`is`, `as`, A `typeof` nejsou přetížitelné operátory.

Uživatelem definovaný typ nejde přetížit `()` operátoru, ale můžete definovat vlastní typ převody, které může provádět výraz přetypování. Další informace najdete v tématu [uživatelsky definovaný převod operátorů](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Is – operátor](~/_csharplang/spec/expressions.md#the-is-operator)
- [Operátor as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Výrazy přetypování](~/_csharplang/spec/expressions.md#cast-expressions)
- [Typeof – operátor](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Postupy: bezpečné vícesměrového vysílání pomocí porovnávání vzorů a je a jako operátory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
