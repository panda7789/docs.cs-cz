---
title: '?: operátor- C# reference'
ms.date: 11/20/2018
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: 6e8fde8c210b2c33cc514167be7face657cbb618
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239376"
---
# <a name="-operator-c-reference"></a>?: – operátorC# (Referenční dokumentace)

Podmíněný operátor `?:`, označovaný také jako Ternární podmíněný operátor, vyhodnotí logický výraz a vrátí výsledek jednoho ze dvou výrazů, v závislosti na tom, zda se logický výraz vyhodnotí jako `true` nebo `false`. Počínaje C# 7,2, [podmíněný výraz ref](#conditional-ref-expression) vrátí odkaz na výsledek jednoho ze dvou výrazů.

Syntaxe podmíněného operátoru je následující:

```csharp
condition ? consequent : alternative
```

Výraz `condition` musí být vyhodnocen jako `true` nebo `false`. Je-li `condition` vyhodnocen jako `true`, je vyhodnocen výraz `consequent` a jeho výsledek se projeví v důsledku operace. Je-li `condition` vyhodnocen jako `false`, je vyhodnocen výraz `alternative` a jeho výsledek se projeví v důsledku operace. Vyhodnotí se jenom `consequent` nebo `alternative`.

Typ `consequent` a `alternative` musí být stejný, nebo musí být implicitní převod z jednoho typu na druhý.

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

[!code-csharp-interactive[non ref conditional](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Podmíněný výraz ref

Počínaje C# 7,2 můžete použít výraz podmíněného odkazu k vrácení odkazu na výsledek jednoho ze dvou výrazů. Tento odkaz můžete přiřadit k místní proměnné [ref](../keywords/ref.md#ref-locals) nebo [ref jen pro čtení](../keywords/ref.md#ref-readonly-locals) nebo použít jako [návratovou hodnotu odkazu](../keywords/ref.md#reference-return-values) nebo jako [parametr metody`ref`](../keywords/ref.md#passing-an-argument-by-reference).

Syntaxe pro podmíněný výraz ref je následující:

```csharp
condition ? ref consequent : ref alternative
```

Podobně jako původní podmíněný operátor, podmíněný výraz ref vyhodnocuje pouze jeden ze dvou výrazů: buď `consequent`, nebo `alternative`.

V případě podmíněného výrazu ref musí být typ `consequent` a `alternative` stejný.

Následující příklad ukazuje použití podmíněného ref výrazu:

[!code-csharp-interactive[conditional ref](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Podmíněný operátor a příkaz `if..else`

Použití podmíněného operátoru namísto příkazu [if-else](../keywords/if-else.md) může mít za následek výstižnější kód v případech, kdy budete potřebovat podmíněně k výpočtu hodnoty. Následující příklad ukazuje dva způsoby, jak klasifikovat celé číslo jako záporné nebo nezáporné:

[!code-csharp[conditional and if-else](~/samples/snippets/csharp/language-reference/operators/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ nemůže přetížit podmíněný operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [podmíněný operátor](~/_csharplang/spec/expressions.md#conditional-operator) ve [ C# specifikaci jazyka](~/_csharplang/spec/introduction.md).

Další informace o podmíněném výrazu ref najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Viz také

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [if-else – příkaz](../keywords/if-else.md)
- [?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)
- [?? a?? = – operátory](null-coalescing-operator.md)
- [ref – klíčové slovo](../keywords/ref.md)
