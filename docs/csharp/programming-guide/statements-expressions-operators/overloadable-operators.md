---
title: Přetížitelné operátory - C# Průvodce programováním pro službu
ms.custom: seodec18
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: 63079569050a70f551887dae837e012044984f85
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/21/2019
ms.locfileid: "67306945"
---
# <a name="overloadable-operators-c-programming-guide"></a>Přetížitelné operátory (C# Programming Guide)

C# umožňuje uživatelem definované typy přetížení operátorů definováním statické členské funkce pomocí [operátor](../../language-reference/keywords/operator.md) – klíčové slovo. Ne všechny operátory mohou být přetíženy, ale a ostatní uživatelé mají omezení, jak je uvedeno v této tabulce:

| Operátory | Overloadability |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/boolean-logical-operators.md#logical-negation-operator-), [~](../../language-reference/operators/bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](../../language-reference/operators/arithmetic-operators.md#increment-operator-), [--](../../language-reference/operators/arithmetic-operators.md#decrement-operator---), [true](../../language-reference/operators/true-false-operators.md), [false](../../language-reference/operators/true-false-operators.md)|Tyto unární operátory můžete přetížit.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/arithmetic-operators.md#multiplication-operator-), [/](../../language-reference/operators/arithmetic-operators.md#division-operator-), [%](../../language-reference/operators/arithmetic-operators.md#remainder-operator-), [&](../../language-reference/operators/boolean-logical-operators.md#logical-and-operator-), [&#124;](../../language-reference/operators/boolean-logical-operators.md#logical-or-operator-), [^](../../language-reference/operators/boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](../../language-reference/operators/bitwise-and-shift-operators.md#left-shift-operator-), [>>](../../language-reference/operators/bitwise-and-shift-operators.md#right-shift-operator-)|Tyto binární operátory můžete přetížit.|
|[==](../../language-reference/operators/equality-operators.md#equality-operator-), [!=](../../language-reference/operators/equality-operators.md#inequality-operator-), [\<](../../language-reference/operators/comparison-operators.md#less-than-operator-), [>](../../language-reference/operators/comparison-operators.md#greater-than-operator-), [\<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-), [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-)|Operátory porovnání mohou být přetíženy (ale viz poznámka pod touto tabulkou).|
|[&&](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](../../language-reference/operators/boolean-logical-operators.md#conditional-logical-or-operator-)|Podmíněné logické operátory nemohou být přetíženy, ale vyhodnocují se pomocí `&` a <code>&#124;</code>, které můžou být přetížené.|
|[&#91;&#93;](../../language-reference/operators/member-access-operators.md#indexer-operator-)|Operátor indexování pole nemohou být přetíženy, ale můžete definovat [indexery](../indexers/index.md).|
|[(T)x](../../language-reference/operators/type-testing-and-conversion-operators.md#cast-operator-)|Nemůže být přetížený operátor přetypování, ale můžete definovat nové operátory převodu (viz [explicitní](../../language-reference/keywords/explicit.md) a [implicitní](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [-=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [\*=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [/=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [%=](../../language-reference/operators/arithmetic-operators.md#compound-assignment), [&=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [&#124;=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [^=](../../language-reference/operators/boolean-logical-operators.md#compound-assignment), [\<\<=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment), [>>=](../../language-reference/operators/bitwise-and-shift-operators.md#compound-assignment)|Nemůže být explicitně přetížené operátory přiřazení. Pokud přetížíte binární operátor odpovídající operátor přiřazení, pokud existuje, ale také implicitně přetížené. Například `+=` vyhodnotí pomocí `+`, které můžou být přetížené.|
|[=](../../language-reference/operators/assignment-operator.md), [. ](../../language-reference/operators/member-access-operators.md#member-access-operator-), [?:](../../language-reference/operators/conditional-operator.md), [?? ](../../language-reference/operators/null-coalescing-operator.md), [ -> ](../../language-reference/operators/pointer-related-operators.md#pointer-member-access-operator--), [ => ](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/member-access-operators.md#invocation-operator-), [jako](../../language-reference/operators/type-testing-and-conversion-operators.md#as-operator), [zaškrtnuto ](../../language-reference/keywords/checked.md), [Nekontrolovaná](../../language-reference/keywords/unchecked.md), [výchozí](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [je](../../language-reference/operators/type-testing-and-conversion-operators.md#is-operator), [nové](../../language-reference/keywords/new.md), [sizeof](../../language-reference/keywords/sizeof.md), [typeof](../../language-reference/operators/type-testing-and-conversion-operators.md#typeof-operator)|Tyto operátory nemohou být přetíženy.|

> [!NOTE]
> Operátory porovnání Pokud přetížena, musí být přetíženy dvojice; To znamená pokud `==` je přetížena, `!=` musí také být přetíženy. Platí to i hodnotu true, pokud přetížení `!=` vyžaduje přetížení pro `==`. Totéž platí pro operátory porovnání `<` a `>` a `<=` a `>=`.

Informace o tom, jak přetížení operátoru, najdete v článku [operátor](../../language-reference/keywords/operator.md) článku – klíčové slovo.

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [Příkazy, výrazy a operátory](index.md)
- [Operátory](operators.md)
- [Operátory jazyka C#](../../language-reference/operators/index.md)
- [Proč jsou přetížené operátory vždy statické v jazyce C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
