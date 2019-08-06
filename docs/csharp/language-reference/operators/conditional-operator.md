---
title: '?: operátor- C# reference'
ms.custom: seodec18
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 923591634599a6bbac74d43b105f4e46b492fa1a
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796463"
---
# <a name="-operator-c-reference"></a>?: – operátorC# (Referenční dokumentace)

Podmíněný operátor `?:`, který `true` se běžně označuje jako Ternární podmíněný operátor, vyhodnocuje logický výraz a vrátí výsledek vyhodnocení jednoho ze dvou výrazů v závislosti na tom, zda se logický výraz vyhodnotí jako nebo `false`. Počínaje C# 7,2, [podmíněný výraz ref](#conditional-ref-expression) vrátí odkaz na výsledek jednoho ze dvou výrazů.

Syntaxe podmíněného operátoru je následující:

```csharp
condition ? consequent : alternative
```

Výraz musí být vyhodnocen `true` jako `false`nebo. `condition` Pokud `condition` se vyhodnotí `true`jako `consequent` , vyhodnotí se výraz a jeho výsledek se projeví v důsledku operace. Pokud `condition` se vyhodnotí `false`jako `alternative` , vyhodnotí se výraz a jeho výsledek se projeví v důsledku operace. Je `consequent` vyhodnocena pouze nebo `alternative` .

Typ `consequent` a`alternative` musí být stejný, nebo musí být implicitní převod z jednoho typu na druhý.

Podmíněný operátor je asociativní zprava, to znamená výraz formuláře.

```csharp
a ? b : c ? d : e
```

je vyhodnocen jako

```csharp
a ? b : (c ? d : e)
```

> [!TIP]
> K zapamatování, jak podmíněný operátor je vyhodnoceno, můžete použít následující symbolické zařízení:
>
> ```text
> is this condition true ? yes : no
> ```

Následující příklad ukazuje použití podmíněného operátoru:

[!code-csharp-interactive[non ref conditional](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Podmíněný výraz ref

Počínaje C# 7,2 můžete použít výraz podmíněného odkazu k vrácení odkazu na výsledek jednoho ze dvou výrazů. Tento odkaz můžete přiřadit k místní proměnné [ref](../keywords/ref.md#ref-locals) nebo [ref jen pro čtení](../keywords/ref.md#ref-readonly-locals) nebo použít jako [návratovou](../keywords/ref.md#reference-return-values) [ `ref` ](../keywords/ref.md#passing-an-argument-by-reference)hodnotu odkazu nebo jako parametr metody.

Syntaxe pro podmíněný výraz ref je následující:

```csharp
condition ? ref consequent : ref alternative
```

Podobně jako původní podmíněný operátor, podmíněný výraz ref vyhodnocuje pouze jeden ze dvou výrazů: `consequent` nebo. `alternative`

V případě podmíněného výrazu ref musí být typ `consequent` a. `alternative`

Následující příklad ukazuje použití podmíněného ref výrazu:

[!code-csharp-interactive[conditional ref](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

Další informace najdete v poznámkách k [návrhu funkcí](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="conditional-operator-and-an-ifelse-statement"></a>Podmíněný operátor a `if..else` příkaz

Použití podmíněného operátoru přes příkaz [if-else](../keywords/if-else.md) může mít za následek přesnější kód v případech, kdy budete potřebovat podmíněně k výpočtu hodnoty. Následující příklad ukazuje dva způsoby, jak klasifikovat celé číslo jako záporné nebo nezáporné:

[!code-csharp[conditional and if-else](~/samples/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Přetížení operátoru

Podmiňovací operátor nelze přetížit.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [podmíněný operátor](~/_csharplang/spec/expressions.md#conditional-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [if-else – příkaz](../keywords/if-else.md)
- [?. a ?[] operátory](member-access-operators.md#null-conditional-operators--and-)
- [?? podnikatel](null-coalescing-operator.md)
- [ref – klíčové slovo](../keywords/ref.md)
