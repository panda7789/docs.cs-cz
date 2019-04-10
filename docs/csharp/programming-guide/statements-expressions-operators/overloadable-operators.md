---
title: Přetížitelné operátory - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: d0a5555bbe68aa82218c1dbe3d24705b26aff9c8
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296573"
---
# <a name="overloadable-operators-c-programming-guide"></a>Přetížitelné operátory (C# Programming Guide)

C# umožňuje uživatelem definované typy přetížení operátorů definováním statické členské funkce pomocí [operátor](../../language-reference/keywords/operator.md) – klíčové slovo. Ne všechny operátory mohou být přetíženy, ale a ostatní uživatelé mají omezení, jak je uvedeno v této tabulce:

| Operátory | Overloadability |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/boolean-logical-operators.md#logical-negation-operator-), [~](../../language-reference/operators/bitwise-complement-operator.md), [++](../../language-reference/operators/arithmetic-operators.md#increment-operator-), [--](../../language-reference/operators/arithmetic-operators.md#decrement-operator---), [true](../../language-reference/keywords/true-false-operators.md), [false](../../language-reference/keywords/true-false-operators.md)|Tyto unární operátory můžete přetížit.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/arithmetic-operators.md#multiplication-operator-), [/](../../language-reference/operators/arithmetic-operators.md#division-operator-), [%](../../language-reference/operators/arithmetic-operators.md#remainder-operator-), [&](../../language-reference/operators/and-operator.md), [&#124;](../../language-reference/operators/or-operator.md), [^](../../language-reference/operators/xor-operator.md), [\<\<](../../language-reference/operators/left-shift-operator.md), [>>](../../language-reference/operators/right-shift-operator.md)|Tyto binární operátory můžete přetížit.|
|[==](../../language-reference/operators/equality-operators.md#equality-operator-), [!=](../../language-reference/operators/equality-operators.md#inequality-operator-), [\<](../../language-reference/operators/less-than-operator.md), [>](../../language-reference/operators/greater-than-operator.md), [\<=](../../language-reference/operators/less-than-equal-operator.md), [>=](../../language-reference/operators/greater-than-equal-operator.md)|Operátory porovnání mohou být přetíženy (ale viz poznámka pod touto tabulkou).|
|[&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|Podmíněné logické operátory nemohou být přetíženy, ale vyhodnocují se pomocí `&` a <code>&#124;</code>, které můžou být přetížené.|
|[&#91;&#93;](../../language-reference/operators/index-operator.md)|Operátor indexování pole nemohou být přetíženy, ale můžete definovat [indexery](../indexers/index.md).|
|[(T)x](../../language-reference/operators/invocation-operator.md)|Nemůže být přetížený operátor přetypování, ale můžete definovat nové operátory převodu (viz [explicitní](../../language-reference/keywords/explicit.md) a [implicitní](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/addition-assignment-operator.md), [-=](../../language-reference/operators/subtraction-assignment-operator.md), [\*=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [/=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [%=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [&=](../../language-reference/operators/and-assignment-operator.md), [&#124;=](../../language-reference/operators/or-assignment-operator.md), [^=](../../language-reference/operators/xor-assignment-operator.md), [\<\<=](../../language-reference/operators/left-shift-assignment-operator.md), [>>=](../../language-reference/operators/right-shift-assignment-operator.md)|Nemůže být explicitně přetížené operátory přiřazení. Pokud přetížíte binární operátor odpovídající operátor přiřazení, pokud existuje, ale také implicitně přetížené. Například `+=` vyhodnotí pomocí `+`, které můžou být přetížené.|
|[=](../../language-reference/operators/assignment-operator.md), [. ](../../language-reference/operators/member-access-operator.md), [?:](../../language-reference/operators/conditional-operator.md), [?? ](../../language-reference/operators/null-coalescing-operator.md), [ -> ](../../language-reference/operators/dereference-operator.md), [ => ](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/invocation-operator.md), [jako](../../language-reference/keywords/as.md), [zaškrtnuto ](../../language-reference/keywords/checked.md), [Nekontrolovaná](../../language-reference/keywords/unchecked.md), [výchozí](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [je](../../language-reference/keywords/is.md), [nové](../../language-reference/keywords/new.md), [sizeof](../../language-reference/keywords/sizeof.md), [typeof](../../language-reference/keywords/typeof.md)|Tyto operátory nemohou být přetíženy.|

> [!NOTE]
> Operátory porovnání Pokud přetížena, musí být přetíženy dvojice; To znamená pokud `==` je přetížena, `!=` musí také být přetíženy. Platí to i hodnotu true, pokud přetížení `!=` vyžaduje přetížení pro `==`. Totéž platí pro operátory porovnání `<` a `>` a `<=` a `>=`.

Informace o tom, jak přetížení operátoru, najdete v článku [operátor](../../language-reference/keywords/operator.md) článku – klíčové slovo.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../index.md)
- [Příkazy, výrazy a operátory](index.md)
- [Operátory](operators.md)
- [Operátory jazyka C#](../../language-reference/operators/index.md)
- [Proč jsou přetížené operátory vždy statické v jazyce C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
