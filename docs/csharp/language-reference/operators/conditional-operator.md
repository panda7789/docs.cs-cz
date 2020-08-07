---
title: '?: operator-reference jazyka C#'
ms.date: 03/06/2020
f1_keywords:
- ?:_CSharpKeyword
- ?_CSharpKeyword
- :_CSharpKeyword
helpviewer_keywords:
- '?: operator [C#]'
- conditional operator (?:) [C#]
ms.assetid: e83a17f1-7500-48ba-8bee-2fbc4c847af4
ms.openlocfilehash: fcde0476935108122d7f7e825d701e48952873f6
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916859"
---
# <a name="-operator-c-reference"></a>?: – operátor (Referenční dokumentace jazyka C#)

Podmíněný operátor `?:` , označovaný také jako Ternární podmíněný operátor, vyhodnocuje logický výraz a vrátí výsledek jednoho ze dvou výrazů, v závislosti na tom, zda je logický výraz vyhodnocen jako `true` nebo `false` .

Syntaxe podmíněného operátoru je následující:

```csharp
condition ? consequent : alternative
```

`condition`Výraz musí být vyhodnocen jako `true` nebo `false` . Pokud se `condition` vyhodnotí jako `true` , `consequent` vyhodnotí se výraz a jeho výsledek se projeví v důsledku operace. Pokud se `condition` vyhodnotí jako `false` , `alternative` vyhodnotí se výraz a jeho výsledek se projeví v důsledku operace. `consequent` `alternative` Je vyhodnocena pouze nebo.

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

[!code-csharp-interactive[non ref conditional](snippets/shared/ConditionalOperator.cs#ConditionalValue)]

## <a name="conditional-ref-expression"></a>Podmíněný výraz ref

Počínaje jazykem C# 7,2 lze místně přiřadit místní proměnnou ref nebo [ref pouze pro](../keywords/ref.md#ref-readonly-locals) [místní](../keywords/ref.md#ref-locals) proměnnou s podmíněným výrazem ref. Podmíněný výraz ref můžete použít také jako [návratovou hodnotu odkazu](../keywords/ref.md#reference-return-values) nebo jako [ `ref` argument metody](../keywords/ref.md#passing-an-argument-by-reference).

Syntaxe pro podmíněný výraz ref je následující:

```csharp
condition ? ref consequent : ref alternative
```

Podobně jako původní podmíněný operátor, podmíněný výraz ref vyhodnocuje pouze jeden ze dvou výrazů: `consequent` nebo `alternative` .

V případě podmíněného výrazu ref `consequent` `alternative` musí být typ a.

Následující příklad ukazuje použití podmíněného ref výrazu:

[!code-csharp-interactive[conditional ref](snippets/shared/ConditionalOperator.cs#ConditionalRef)]

## <a name="conditional-operator-and-an-ifelse-statement"></a>Podmíněný operátor a `if..else` příkaz

Použití podmíněného operátoru namísto příkazu [if-else](../keywords/if-else.md) může mít za následek výstižnější kód v případech, kdy budete potřebovat podmíněně k výpočtu hodnoty. Následující příklad ukazuje dva způsoby, jak klasifikovat celé číslo jako záporné nebo nezáporné:

[!code-csharp[conditional and if-else](snippets/shared/ConditionalOperator.cs#CompareWithIf)]

## <a name="operator-overloadability"></a>Přetížení operátoru

Uživatelsky definovaný typ nemůže přetížit podmíněný operátor.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v části [podmíněný operátor](~/_csharplang/spec/expressions.md#conditional-operator) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).

Další informace o podmíněném výrazu ref najdete v [poznámce k návrhu funkcí](~/_csharplang/proposals/csharp-7.2/conditional-ref.md).

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [if-else – příkaz](../keywords/if-else.md)
- [?. ani? [] – operátory](member-access-operators.md#null-conditional-operators--and-)
- [?? a?? = – operátory](null-coalescing-operator.md)
- [ref – klíčové slovo](../keywords/ref.md)
