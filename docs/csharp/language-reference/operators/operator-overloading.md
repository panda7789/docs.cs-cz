---
title: Operátor přetížení - C# odkaz
description: Zjistěte, jak přetížení C# operátor a které C# jsou přetížitelné operátory.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: e225acedde5f097fd12680080c7f6b242e882b04
ms.sourcegitcommit: 4d8efe00f2e5ab42e598aff298d13b8c052d9593
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68235921"
---
# <a name="operator-overloading-c-reference"></a>Přetížení operátoru (C# odkaz)

Uživatelem definovaný typ může přetížit i předdefinovanou C# operátor. To znamená typ může poskytnout vlastní implementaci operace, pokud jeden nebo oba operandy jsou daného typu. [Přetížitelné operátory](#overloadable-operators) část ukazuje, které C# můžou být přetížené operátory.

Použití `operator` – klíčové slovo pro operátor deklaraci. Deklarace operátoru musí splňovat následující pravidla:

- To zahrnuje i `public` a `static` modifikátor.
- Unární operátor přijímá jeden parametr. Binární operátor používá dva parametry. V obou případech musí mít nejmíň jeden parametr typu `T` nebo `T?` kde `T` je typ, který obsahuje deklarace operátoru.

Následující příklad definuje zjednodušenou strukturu představující racionální číslo. Struktura přetížení některé [aritmetické operátory](arithmetic-operators.md):

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

V předchozím příkladu můžete rozšířit definováním implicitní převod z `int` k `Fraction`. Přetížené operátory by pak podporují argumentů těchto dvou typů. To znamená by být možné přidat celé číslo zlomek a v důsledku získat zlomek.

Můžete také použít `operator` – klíčové slovo definovat převod vlastního typu. Další informace najdete v tématu [uživatelsky definovaný převod operátorů](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Přetížitelné operátory

Následující tabulka obsahuje informace o overloadability z C# operátory:

| Operátory | Overloadability |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [!](boolean-logical-operators.md#logical-negation-operator-), [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---) , [true](true-false-operators.md), [false](true-false-operators.md)|Tyto unární operátory můžete přetížit.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [& ](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-), [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-), [>=](comparison-operators.md#greater-than-or-equal-operator-)|Tyto binární operátory můžete přetížit. Některé operátory musí být přetíženy v párech; Další informace viz poznámka pod touto tabulkou.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|Podmíněné logické operátory nemohou být přetíženy. Ale pokud typ s přetížené [ `true` a `false` operátory](true-false-operators.md) také přetížení `&` nebo <code>&#124;</code> operátor určitým způsobem, `&&` nebo <code>&#124;&#124;</code> operátor v uvedeném pořadí může být vyhodnocen pro operandy typu. Další informace najdete v tématu [podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|Přístup k prvkům se nepovažuje za očekával se přetěžovatelný operátor, ale můžete definovat [indexer](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|Nemůže být přetížený operátor přetypování, ale můžete definovat nové operátory převodu. Další informace najdete v tématu [uživatelsky definovaný převod operátorů](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Složené přiřazení, které explicitně nemohou být přetíženy operátory. Pokud přetížíte binární operátor odpovídající operátor složeného přiřazení, pokud existuje, ale také implicitně přetížené. Například `+=` vyhodnotí pomocí `+`, které můžou být přetížené.|
|[=](assignment-operator.md), [. ](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [?? ](null-coalescing-operator.md), [ -> ](pointer-related-operators.md#pointer-member-access-operator--), [ => ](lambda-operator.md), [f(x)](member-access-operators.md#invocation-operator-), [jako](type-testing-and-conversion-operators.md#as-operator), [zaškrtnuto ](../keywords/checked.md), [Nekontrolovaná](../keywords/unchecked.md), [výchozí](../../programming-guide/statements-expressions-operators/default-value-expressions.md), [delegovat](../../programming-guide/statements-expressions-operators/anonymous-methods.md), [je](type-testing-and-conversion-operators.md#is-operator), [nameof](nameof.md), [nové](new-operator.md), [sizeof](../keywords/sizeof.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|Tyto operátory nemohou být přetíženy.|

> [!NOTE]
> Musí být přetíženy operátory porovnání v párech. To znamená pokud buď operátor páru je přetížena, další operátor musí být přetíženy také. Tyto páry jsou následující:
>
> - `==` a `!=` operátory
> - `<` a `>` operátory
> - `<=` a `>=` operátory

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následující částech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Přetížení operátoru](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operátory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Viz také:

- [C#referenční dokumentace](../index.md)
- [Operátory jazyka C#](index.md)
- [Uživatelem definovaný převod operátorů](user-defined-conversion-operators.md)
- [Proč jsou přetížené operátory vždy statické v jazyce C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
