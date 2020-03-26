---
title: Operátory testování typů a přetypování – odkaz C#
description: Další informace o operátory Jazyka C#, které můžete použít ke kontrole typu výsledku výrazu a převést jej na jiný typ v případě potřeby.
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
ms.openlocfilehash: 2dc215a91c55be15e8eee488f0030f41e3492af5
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507084"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Operátory testování typů a přetypování (odkaz C#

K provedení kontroly typu nebo převodu typu můžete použít následující operátory:

- [je operátor](#is-operator): kontrola, zda je typ runtime výrazu kompatibilní s daným typem
- [jako operátor](#as-operator): explicitně převést výraz na daný typ, pokud je jeho typ runtime kompatibilní s tímto typem
- [operátor obsazení ()](#cast-operator-): provést explicitní převod
- [typeof operátor](#typeof-operator): <xref:System.Type?displayProperty=nameWithType> získat instanci pro typ

## <a name="is-operator"></a>je operátor

Operátor `is` zkontroluje, zda je typ runtime výsledku výrazu kompatibilní s daným typem. Počínaje C# 7.0, `is` operátor také testuje výsledek výrazu proti vzoru.

Výraz s operátorem `is` typ-testing má následující formulář

```csharp
E is T
```

kde `E` je výraz, který `T` vrací hodnotu a je název typu nebo typu parametr. `E`nemůže být anonymní metoda nebo lambda výraz.

Výraz `E is T` vrátí, `true` pokud `E` výsledek je non-null a lze `T` převést na typ odkaz převodu, zabalení převodu nebo unboxing převodu; v opačném `false`případě vrátí . Operátor `is` nebere v úvahu uživatelem definované převody.

Následující příklad ukazuje, `is` že `true` operátor vrátí, pokud typ runtime výsledku výrazu pochází z daného typu, to znamená, že existuje převod odkazu mezi typy:

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Následující příklad ukazuje, `is` že operátor bere v úvahu převody zabalení a rozbalení, ale nebere v úvahu [číselné převody](../builtin-types/numeric-conversions.md):

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

Informace o převodech jazyka C# naleznete v kapitole [Převody](~/_csharplang/spec/conversions.md) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Testování typů s porovnáváním vzorů

Počínaje C# 7.0, `is` operátor také testuje výsledek výrazu proti vzoru. Zejména podporuje vzor typu v následujícím formuláři:

```csharp
E is T v
```

kde `E` je výraz, který `T` vrací hodnotu, je název typu `v` nebo parametru typu `T`a je novou místní proměnnou typu . `E` Pokud je výsledek nenulové a lze jej `T` převést na převod odkazu, zabalení nebo rozbalení, `E is T v` výraz vrátí `true` a převedená hodnota výsledku `E` je přiřazena proměnné `v`.

Následující příklad ukazuje použití operátoru `is` se vzorem typu:

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Další informace o vzoru typu a dalších podporovaných vzorech naleznete v [tématu Pattern matching with is](../keywords/is.md#pattern-matching-with-is).

## <a name="as-operator"></a>jako operátor

Operátor `as` explicitně převede výsledek výrazu na daný odkaz nebo typ hodnoty s hodnotou, kterou lze hodnotit s hodnotou s hodnotou s možnou hodnotou. Pokud převod není možný, `as` operátor `null`vrátí . Na rozdíl od `as` [operátoru přetypádka ()](#cast-operator-)operátor nikdy nevyvolá výjimku.

Vyjádření formuláře

```csharp
E as T
```

kde `E` je výraz, který `T` vrací hodnotu a je název typu nebo parametru typu, vytváří stejný výsledek jako

```csharp
E is T ? (T)(E) : (T)null
```

kromě `E` toho, že se vyhodnocuje pouze jednou.

Operátor `as` považuje pouze odkaz, null, zabalení a unboxing převody. `as` Operátor nelze použít k provedení převodu definovaného uživatelem. Chcete-li to provést, použijte [operátor přetypádka ()](#cast-operator-).

Následující příklad ukazuje použití operátoru: `as`

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Jak ukazuje předchozí příklad, je třeba porovnat `as` výsledek `null` výrazu s ke kontrole, zda je převod úspěšný. Počínaje C# 7.0, můžete použít [operátor is](#type-testing-with-pattern-matching) jak k testování, pokud je převod úspěšný, a pokud je úspěšný, přiřadit jeho výsledek nové proměnné.

## <a name="cast-operator-"></a>Operátor přetypápku ()

Výraz přetypování `(T)E` formuláře provádí explicitní převod výsledku `E` `T`výrazu na typ . Pokud neexistuje žádný explicitní převod `E` z `T`typu typu na typ , dojde k chybě v době kompilace. V době běhu explicitní převod nemusí být úspěšné a výraz přetypování může vyvolat výjimku.

Následující příklad ukazuje explicitní číselné a referenční převody:

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

Informace o podporovaných explicitních konverzích naleznete v části [Explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions) [ve specifikaci jazyka C#](~/_csharplang/spec/introduction.md). Informace o tom, jak definovat vlastní explicitní nebo implicitní převod typu, naleznete v [tématu Uživatelem definované operátory převodu](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Ostatní použití ()

Závorky můžete také použít k [volání metody nebo vyvolání delegáta](member-access-operators.md#invocation-expression-).

Jiné použití závorek je upravit pořadí, ve kterém chcete vyhodnotit operace ve výrazu. Další informace naleznete v tématu [C# operátory](index.md).

## <a name="typeof-operator"></a>typeof – operátor

Operátor `typeof` získá instanci <xref:System.Type?displayProperty=nameWithType> pro typ. Argument pro `typeof` operátor musí být název typu nebo parametr typu, jak ukazuje následující příklad:

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

Můžete také použít `typeof` operátor s nevázanými obecnými typy. Název nevázaného obecného typu musí obsahovat příslušný počet čárek, což je o jeden menší než počet parametrů typu. Následující příklad ukazuje použití `typeof` operátoru s nevázaným obecným typem:

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Výraz nemůže být argumentem `typeof` operátoru. Chcete-li <xref:System.Type?displayProperty=nameWithType> získat instanci pro typ runtime <xref:System.Object.GetType%2A?displayProperty=nameWithType> výsledku výrazu, použijte metodu.

### <a name="type-testing-with-the-typeof-operator"></a>Typové zkoušky `typeof` s obsluhou

Pomocí `typeof` operátoru zkontrolujte, zda typ runtime výsledku výrazu přesně odpovídá danému typu. Následující příklad ukazuje rozdíl mezi kontrolou typu `typeof` provedenou s operátorem a [operátorem is](#is-operator):

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Přetížení obsluhy

V `is` `as`, `typeof` , a operátory nelze přetíženy.

Uživatelem definovaný typ nemůže `()` přetížit operátor, ale může definovat převody vlastního typu, které lze provést výrazem přetypování. Další informace naleznete v [tématu User-defined operátory převodu](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Operátor is](~/_csharplang/spec/expressions.md#the-is-operator)
- [Jako operátor](~/_csharplang/spec/expressions.md#the-as-operator)
- [Výrazy obsazení](~/_csharplang/spec/expressions.md#cast-expressions)
- [Typ operátoru](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Jak bezpečně obsazení pomocí porovnávání vzorů a je a jako operátory](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
