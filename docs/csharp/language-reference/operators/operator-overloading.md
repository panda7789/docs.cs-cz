---
title: Přetížení operátoru – C# odkaz
description: Přečtěte si, jak C# přetížit operátor a C# které operátory jsou přetížené.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 130eb4be66d13b43e5605ef98a647fa9f4223014
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71116109"
---
# <a name="operator-overloading-c-reference"></a>Přetížení operátoru (C# reference)

Uživatelsky definovaný typ může přetížit předdefinovaný C# operátor. To znamená, že typ může poskytnout vlastní implementaci operace, když jeden nebo oba operandy jsou tohoto typu. Oddíl [přetížené operátory](#overloadable-operators) ukazuje, které C# operátory mohou být přetíženy.

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
|[+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [! x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [--](arithmetic-operators.md#decrement-operator---), [true](true-false-operators.md), [false](true-false-operators.md)|Tyto unární operátory mohou být přetíženy.|
|[x + y](addition-operator.md), [x-y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \< \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x > > y](bitwise-and-shift-operators.md#right-shift-operator-), [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-), [x \< y](comparison-operators.md#less-than-operator-), [x > y](comparison-operators.md#greater-than-operator-), [x \<= y](comparison-operators.md#less-than-or-equal-operator-), [x > = y](comparison-operators.md#greater-than-or-equal-operator-)|Tyto binární operátory mohou být přetíženy. Některé operátory musí být v páru přetížené. Další informace najdete v poznámce, které následují po této tabulce.|
|[x & & y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124; &#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Podmíněné logické operátory nelze přečítat. Nicméně pokud typ s přetíženou `&` [ `true` a `false` operátory](true-false-operators.md) také přetěžuje operátor OR <code>&#124;</code> určitým způsobem, `&&` může být operátor OR <code>&#124;&#124;</code> (v uvedeném pořadí) vyhodnocen pro operandy daného typu. Další informace naleznete v části [uživatelsky definované Podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).|
|[a&#91;&#93;](member-access-operators.md#indexer-operator-)|Přístup k prvku není považován za přetížený operátor, ale můžete definovat [indexer](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-cast.md#cast-operator-)|Operátor přetypování nemůže být přetížen, ale lze definovat nové operátory převodu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment), [\*=](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment), [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment), [\<\<=](bitwise-and-shift-operators.md#compound-assignment), [>>=](bitwise-and-shift-operators.md#compound-assignment)|Operátory složeného přiřazení nelze explicitně přečítat. Nicméně při přetížení binárního operátoru je odpovídající složený operátor přiřazení, pokud existuje, také implicitně přetížený. Například `+=` je vyhodnocen pomocí `+`, který může být přetížen.|
|[^ x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x. y](member-access-operators.md#member-access-operator-), [c? t: f](conditional-operator.md), [x?? y](null-coalescing-operator.md), [x?? = y](null-coalescing-operator.md), [x... y](member-access-operators.md#range-operator-), [x-> y](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md), [f (x)](member-access-operators.md#invocation-operator-), [jako](type-testing-and-cast.md#as-operator), [await](await.md), [zaškrtnuto](../keywords/checked.md), [nezaškrtnuto](../keywords/unchecked.md), [Default](default.md), [Delegate](delegate-operator.md), [is](type-testing-and-cast.md#is-operator), [nameof](nameof.md), [New](new-operator.md), [sizeof ](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Tyto operátory nemůžou být přetížené.|

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
