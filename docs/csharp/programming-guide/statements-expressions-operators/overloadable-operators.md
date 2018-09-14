---
title: Přetížitelné operátory (C# Programming Guide)
ms.date: 08/27/2018
helpviewer_keywords:
- C# language, operator overloading
- operator overloading [C#]
ms.assetid: 390d9d01-79fc-40ab-9ed3-0bf448da1b6a
ms.openlocfilehash: f819e94fd532c10478ac39da9485126aa4380dd5
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2018
ms.locfileid: "45520983"
---
# <a name="overloadable-operators-c-programming-guide"></a>Přetížitelné operátory (C# Programming Guide)

C# umožňuje uživatelem definované typy přetížení operátorů definováním statické členské funkce pomocí [operátor](../../language-reference/keywords/operator.md) – klíčové slovo. Ne všechny operátory mohou být přetíženy, ale a ostatní uživatelé mají omezení, jak je uvedeno v této tabulce:

| Operátory | Overloadability |
| --------- | --------------- |
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [!](../../language-reference/operators/logical-negation-operator.md), [~](../../language-reference/operators/bitwise-complement-operator.md), [++](../../language-reference/operators/increment-operator.md), [--](../../language-reference/operators/decrement-operator.md) , [true](../../language-reference/keywords/true.md), [false](../../language-reference/keywords/false.md)|Tyto unární operátory můžete přetížit.|
|[+](../../language-reference/operators/addition-operator.md), [-](../../language-reference/operators/subtraction-operator.md), [\*](../../language-reference/operators/multiplication-operator.md), [/](../../language-reference/operators/division-operator.md), [%](../../language-reference/operators/modulus-operator.md), [&](../../language-reference/operators/and-operator.md), [&#124;](../../language-reference/operators/or-operator.md), [^](../../language-reference/operators/xor-operator.md), [\<\<](../../language-reference/operators/left-shift-operator.md), [>>](../../language-reference/operators/right-shift-operator.md)|Tyto binární operátory můžete přetížit.|
|[==](../../language-reference/operators/equality-comparison-operator.md), [!=](../../language-reference/operators/not-equal-operator.md), [\<](../../language-reference/operators/less-than-operator.md), [>](../../language-reference/operators/greater-than-operator.md), [\<=](../../language-reference/operators/less-than-equal-operator.md), [>=](../../language-reference/operators/greater-than-equal-operator.md)|Operátory porovnání mohou být přetíženy (ale viz poznámka pod touto tabulkou).|
|[&&](../../language-reference/operators/conditional-and-operator.md), [&#124;&#124;](../../language-reference/operators/conditional-or-operator.md)|Podmíněné logické operátory nemohou být přetíženy, ale vyhodnocují se pomocí `&` a <code>&#124;</code>, které můžou být přetížené.|
|[&#91;&#93;](../../language-reference/operators/index-operator.md)|Operátor indexování pole nemohou být přetíženy, ale můžete definovat [indexery](../indexers/index.md).|
|[(T)x](../../language-reference/operators/invocation-operator.md)|Nemůže být přetížený operátor přetypování, ale můžete definovat nové operátory převodu (viz [explicitní](../../language-reference/keywords/explicit.md) a [implicitní](../../language-reference/keywords/implicit.md)).|
|[+=](../../language-reference/operators/addition-assignment-operator.md), [-=](../../language-reference/operators/subtraction-assignment-operator.md), [\*=](../../language-reference/operators/multiplication-assignment-operator.md), [/=](../../language-reference/operators/division-assignment-operator.md), [%=](../../language-reference/operators/modulus-assignment-operator.md), [&=](../../language-reference/operators/and-assignment-operator.md), [&#124;=](../../language-reference/operators/or-assignment-operator.md), [^=](../../language-reference/operators/xor-assignment-operator.md), [\<\<=](../../language-reference/operators/left-shift-assignment-operator.md), [>>=](../../language-reference/operators/right-shift-assignment-operator.md)|Nemůže být explicitně přetížené operátory přiřazení. Pokud přetížíte binární operátor odpovídající operátor přiřazení, pokud existuje, ale také implicitně přetížené. Například `+=` vyhodnotí pomocí `+`, které můžou být přetížené.|
|[=](../../language-reference/operators/assignment-operator.md), [. ](../../language-reference/operators/member-access-operator.md), [?:](../../language-reference/operators/conditional-operator.md), [?? ](../../language-reference/operators/null-coalescing-operator.md), [ -> ](../../language-reference/operators/dereference-operator.md), [ => ](../../language-reference/operators/lambda-operator.md), [f(x)](../../language-reference/operators/invocation-operator.md), [jako](../../language-reference/keywords/as.md), [zaškrtnuto ](../../language-reference/keywords/checked.md), [Nekontrolovaná](../../language-reference/keywords/unchecked.md), [výchozí](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [je](../../language-reference/keywords/is.md), [nové](../../language-reference/keywords/new.md), [sizeof](../../language-reference/keywords/sizeof.md), [typeof](../../language-reference/keywords/typeof.md)|Tyto operátory nemohou být přetíženy.|

> [!NOTE]
> Operátory porovnání Pokud přetížena, musí být přetíženy dvojice; To znamená pokud `==` je přetížena, `!=` musí také být přetíženy. Platí to i hodnotu true, pokud přetížení `!=` vyžaduje přetížení pro `==`. Totéž platí pro operátory porovnání `<` a `>` a `<=` a `>=`.

Informace o tom, jak přetížení operátoru, najdete v článku [operátor](../../language-reference/keywords/operator.md) článku – klíčové slovo.

## <a name="see-also"></a>Viz také

- [Průvodce programováním v jazyce C#](../index.md)
- [Příkazy, výrazy a operátory](index.md)
- [Operátory](operators.md)
- [Operátory jazyka C#](../../language-reference/operators/index.md)  
- [Proč jsou přetížené operátory vždy statické v jazyce C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
