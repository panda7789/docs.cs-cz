---
title: Přetížení operátoru – C# odkaz
description: Přečtěte si, jak C# přetížit operátor a C# které operátory jsou přetížené.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: c59ae6960a77efd866db4748ca537d9e5218fd1e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78238972"
---
# <a name="operator-overloading-c-reference"></a>Přetížení operátoru (C# reference)

Uživatelsky definovaný typ může přetížit předdefinovaný C# operátor. To znamená, že typ může poskytnout vlastní implementaci operace v případě, že jeden nebo oba operandy jsou tohoto typu. Oddíl [přetížené operátory](#overloadable-operators) ukazuje, které C# operátory mohou být přetíženy.

K deklarování operátoru použijte klíčové slovo `operator`. Deklarace operátoru musí splňovat následující pravidla:

- Zahrnuje jak `public`, tak modifikátor `static`.
- Unární operátor má jeden vstupní parametr. Binární operátor má dva vstupní parametry. V každém případě musí mít alespoň jeden parametr typ `T` nebo `T?`, kde `T` je typ, který obsahuje deklaraci operátoru.

Následující příklad definuje zjednodušenou strukturu, která představuje racionální číslo. Struktura přetěžuje některé [aritmetické operátory](arithmetic-operators.md):

[!code-csharp[fraction example](~/samples/snippets/csharp/language-reference/operators/OperatorOverloading.cs)]

Předchozí příklad můžete zvětšit [definováním implicitního převodu](user-defined-conversion-operators.md) z `int` na `Fraction`. Přetížené operátory pak podporují argumenty těchto dvou typů. To znamená, že by bylo možné přidat celé číslo do zlomku a získat zlomek jako výsledek.

Pomocí klíčového slova `operator` také můžete definovat vlastní převod typu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Přetížené operátory

Následující tabulka poskytuje informace o přetížení C# operátorů:

| Operátory | Přetížení |
| --------- | --------------- |
|[+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [! x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Tyto unární operátory mohou být přetíženy.|
|[x + y](addition-operator.md), [x-y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \<\< y](bitwise-and-shift-operators.md#left-shift-operator-), [x > > y](bitwise-and-shift-operators.md#right-shift-operator-), [x = = y](equality-operators.md#equality-operator-), x [! = y](equality-operators.md#inequality-operator-), [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<=](comparison-operators.md#less-than-or-equal-operator-)y, [x > = y](comparison-operators.md#greater-than-or-equal-operator-)|Tyto binární operátory mohou být přetíženy. Některé operátory musí být v páru přetížené. Další informace najdete v poznámce, které následují po této tabulce.|
|[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Podmíněné logické operátory nelze přečítat. Nicméně pokud typ s přetíženými [`true` a `false` operátory](true-false-operators.md) přetěžuje `&` nebo <code>&#124;</code> operátor určitým způsobem, lze pro operandy daného typu vyhodnotit operátor `&&` nebo <code>&#124;&#124;</code>. Další informace naleznete v části [uživatelsky definované Podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).|
|[a&#91;&#93;](member-access-operators.md#indexer-operator-)|Přístup k prvku není považován za přetížený operátor, ale můžete definovat [indexer](../../programming-guide/indexers/index.md).|
|[(T) x](type-testing-and-cast.md#cast-operator-)|Operátor přetypování nemůže být přetížen, ale lze definovat nové operátory převodu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [ &#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<](bitwise-and-shift-operators.md#compound-assignment)\<=, [>>=](bitwise-and-shift-operators.md#compound-assignment)|Operátory složeného přiřazení nelze explicitně přečítat. Nicméně při přetížení binárního operátoru je odpovídající složený operátor přiřazení, pokud existuje, také implicitně přetížený. Například `+=` se vyhodnocuje pomocí `+`, která může být přetížena.|
|[^ x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x. y](member-access-operators.md#member-access-operator-), [c? t: f](conditional-operator.md), [x?? y](null-coalescing-operator.md), [x?? = y](null-coalescing-operator.md), [x... y](member-access-operators.md#range-operator-), [x-> y](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f (x)](member-access-operators.md#invocation-operator-), [jako](type-testing-and-cast.md#as-operator), [await](await.md), [zaškrtnutí](../keywords/checked.md), [nezaškrtnuto](../keywords/unchecked.md), [výchozí](default.md), [delegát](delegate-operator.md), [is](type-testing-and-cast.md#is-operator), [nameof](nameof.md), [New](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Tyto operátory nemůžou být přetížené.|

> [!NOTE]
> Operátory porovnání musí být přetíženy v páru. To znamená, že pokud je jeden operátor páru přetížený, druhý operátor musí být přetížený. Tyto páry jsou následující:
>
> - operátory `==` a `!=`
> - operátory `<` a `>`
> - operátory `<=` a `>=`

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Přetížení operátoru](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operátory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Viz také

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Uživatelsky definované operátory převodu](user-defined-conversion-operators.md)
- [Pokyny pro návrh – přetížení operátorů](../../../standard/design-guidelines/operator-overloads.md)
- [Pokyny pro návrh – operátory rovnosti](../../../standard/design-guidelines/equality-operators.md)
- [Proč jsou přetížené operátory vždycky statické C#?](https://docs.microsoft.com/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
