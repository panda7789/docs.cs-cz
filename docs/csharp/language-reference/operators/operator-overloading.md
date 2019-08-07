---
title: Přetížení operátoru – C# odkaz
description: Přečtěte si, jak C# přetížit operátor a C# které operátory jsou přetížené.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: da1e47d7ebdf91084d94fc895f0ce46d773353d7
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796576"
---
# <a name="operator-overloading-c-reference"></a>Přetížení operátoru (C# reference)

Uživatelsky definovaný typ může přetížit předdefinovaný C# operátor. To znamená, že typ může poskytnout vlastní implementaci operace, když je jeden nebo oba operandy daného typu. Oddíl [přetížené operátory](#overloadable-operators) ukazuje, které C# operátory mohou být přetíženy.

`operator` Použijte klíčové slovo k deklarování operátoru. Deklarace operátoru musí splňovat následující pravidla:

- Zahrnuje jak `public` `static` a, tak i modifikátor.
- Unární operátor přijímá jeden parametr. Binární operátor používá dva parametry. V každém případě musí mít alespoň jeden parametr typ `T` , nebo `T?` kde `T` je typ, který obsahuje deklaraci operátoru.

Následující příklad definuje zjednodušenou strukturu, která představuje racionální číslo. Struktura přetěžuje některé [aritmetické operátory](arithmetic-operators.md):

[!code-csharp[fraction example](~/samples/csharp/language-reference/operators/OperatorOverloading.cs)]

Předchozí příklad můžete zvětšit definováním implicitního převodu z `int` na. `Fraction` Přetížené operátory pak podporují argumenty těchto dvou typů. To znamená, že by bylo možné přidat celé číslo do zlomku a získat zlomek jako výsledek.

`operator` Klíčové slovo můžete také použít k definování vlastního převodu typu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Přetížené operátory

Následující tabulka poskytuje informace o přetížení C# operátorů:

| Operátory | Přetížení |
| --------- | --------------- |
|[+](arithmetic-operators.md#unary-plus-and-minus-operators), [-](arithmetic-operators.md#unary-plus-and-minus-operators), [](boolean-logical-operators.md#logical-negation-operator-),! [~](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [,--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Tyto unární operátory mohou být přetíženy.|
|[+](addition-operator.md), [-](subtraction-operator.md), [\*](arithmetic-operators.md#multiplication-operator-), [/](arithmetic-operators.md#division-operator-), [%](arithmetic-operators.md#remainder-operator-), [&](boolean-logical-operators.md#logical-and-operator-), [&#124;](boolean-logical-operators.md#logical-or-operator-), [^](boolean-logical-operators.md#logical-exclusive-or-operator-), [\<\<](bitwise-and-shift-operators.md#left-shift-operator-), [>>](bitwise-and-shift-operators.md#right-shift-operator-), [==](equality-operators.md#equality-operator-), [!=](equality-operators.md#inequality-operator-), [\<](comparison-operators.md#less-than-operator-) , [>](comparison-operators.md#greater-than-operator-), [\<=](comparison-operators.md#less-than-or-equal-operator-),[>=](comparison-operators.md#greater-than-or-equal-operator-)|Tyto binární operátory mohou být přetíženy. Některé operátory musí být v páru přetížené. Další informace najdete v poznámce, které následují po této tabulce.|
|[&&](boolean-logical-operators.md#conditional-logical-and-operator-), [&#124;&#124;](boolean-logical-operators.md#conditional-logical-or-operator-)|Podmíněné logické operátory nelze přečítat. Nicméně pokud typ s přetíženou `&` [ `true` a `false` operátory](true-false-operators.md) také přetěžuje operátor OR <code>&#124;</code> určitým způsobem, `&&` může být operátor OR <code>&#124;&#124;</code> (v uvedeném pořadí) vyhodnocen pro operandy daného typu. Další informace naleznete v části [uživatelsky definované Podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).|
|[&#91;&#93;](member-access-operators.md#indexer-operator-)|Přístup k prvku není považován za přetížený operátor, ale můžete definovat [indexer](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-conversion-operators.md#cast-operator-)|Operátor přetypování nemůže být přetížen, ale lze definovat nové operátory převodu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Operátory složeného přiřazení nelze explicitně přečítat. Nicméně při přetížení binárního operátoru je odpovídající složený operátor přiřazení, pokud existuje, také implicitně přetížený. Například `+=` je vyhodnocen pomocí `+`, který může být přetížen.|
|[=](assignment-operator.md), [.](member-access-operators.md#member-access-operator-), [?:](conditional-operator.md), [??](null-coalescing-operator.md), [->](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f (x)](member-access-operators.md#invocation-operator-), [jako](type-testing-and-conversion-operators.md#as-operator), [](../keywords/checked.md)zaškrtnuté [](../keywords/unchecked.md), nezaškrtnuto, [výchozí](default.md), [delegát](delegate-operator.md), [is](type-testing-and-conversion-operators.md#is-operator), [nameof](nameof.md), [New](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-conversion-operators.md#typeof-operator)|Tyto operátory nemůžou být přetížené.|

> [!NOTE]
> Operátory porovnání musí být přetíženy v páru. To znamená, že pokud je jeden operátor páru přetížený, druhý operátor musí být přetížený. Tyto páry jsou následující:
>
> - `==`operátory `!=` a
> - `<`operátory `>` a
> - `<=`operátory `>=` a

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Přetížení operátoru](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operátory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Uživatelsky definované operátory převodu](user-defined-conversion-operators.md)
- [Proč jsou přetížené operátory vždycky statické C#?](https://blogs.msdn.microsoft.com/ericlippert/2007/05/14/why-are-overloaded-operators-always-static-in-c/)
