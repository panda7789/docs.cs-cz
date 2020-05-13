---
title: Operátor Overloads – reference jazyka C#
description: Přečtěte si, jak přetížit operátor jazyka C# a které operátory jazyka C# jsou přetížené.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 29ae9fcec414af988019463a51c964d46b009534
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378922"
---
# <a name="operator-overloading-c-reference"></a>Overloads – operátor (Referenční dokumentace jazyka C#)

Uživatelsky definovaný typ může přetížit předdefinovaný operátor jazyka C#. To znamená, že typ může poskytnout vlastní implementaci operace v případě, že jeden nebo oba operandy jsou tohoto typu. Oddíl [přetížené operátory](#overloadable-operators) ukazuje, které operátory jazyka C# mohou být přetíženy.

Použijte `operator` klíčové slovo k deklarování operátoru. Deklarace operátoru musí splňovat následující pravidla:

- Zahrnuje jak a, tak i `public` `static` modifikátor.
- Unární operátor má jeden vstupní parametr. Binární operátor má dva vstupní parametry. V každém případě musí mít alespoň jeden parametr typ `T` `T?` , nebo kde `T` je typ, který obsahuje deklaraci operátoru.

Následující příklad definuje zjednodušenou strukturu, která představuje racionální číslo. Struktura přetěžuje některé [aritmetické operátory](arithmetic-operators.md):

[!code-csharp[fraction example](snippets/OperatorOverloading.cs)]

Předchozí příklad můžete zvětšit [definováním implicitního převodu](user-defined-conversion-operators.md) z `int` na `Fraction` . Přetížené operátory pak podporují argumenty těchto dvou typů. To znamená, že by bylo možné přidat celé číslo do zlomku a získat zlomek jako výsledek.

Klíčové slovo můžete také použít `operator` k definování vlastního převodu typu. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Přetížené operátory

Následující tabulka poskytuje informace o přetížení operátorů jazyka C#:

| Operátory | Přetížení |
| --------- | --------------- |
|[+ x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [! x](boolean-logical-operators.md#logical-negation-operator-), [~ x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-) , [--](arithmetic-operators.md#decrement-operator---) , [true](true-false-operators.md), [false](true-false-operators.md)|Tyto unární operátory mohou být přetíženy.|
|[x + y](addition-operator.md), [x-y](subtraction-operator.md), [x \* y](arithmetic-operators.md#multiplication-operator-), [x/y](arithmetic-operators.md#division-operator-), [x% y](arithmetic-operators.md#remainder-operator-), [x & y](boolean-logical-operators.md#logical-and-operator-), [x &#124; y](boolean-logical-operators.md#logical-or-operator-), [x ^ y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \< \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-), [x = = y](equality-operators.md#equality-operator-), [x! = y](equality-operators.md#inequality-operator-), [x \< y](comparison-operators.md#less-than-operator-), x [> y](comparison-operators.md#greater-than-operator-), [x \< = y](comparison-operators.md#less-than-or-equal-operator-), x [>= y](comparison-operators.md#greater-than-or-equal-operator-)|Tyto binární operátory mohou být přetíženy. Některé operátory musí být v páru přetížené. Další informace najdete v poznámce, které následují po této tabulce.|
|[x && y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Podmíněné logické operátory nelze přečítat. Nicméně pokud typ s přetíženou [ `true` a `false` operátory](true-false-operators.md) také přetěžuje `&` <code>&#124;</code> operátor OR určitým způsobem, `&&` <code>&#124;&#124;</code> lze pro operandy daného typu vyhodnotit operátor OR (v uvedeném pořadí). Další informace naleznete v části [Podmíněné logické operátory definované uživatelem](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) v tématu [specifikace jazyka C#](~/_csharplang/spec/introduction.md).|
|[&#93;&#91;](member-access-operators.md#indexer-operator-),[`a?[i]`](member-access-operators.md#null-conditional-operators--and-)|Přístup k prvku není považován za přetížený operátor, ale můžete definovat [indexer](../../programming-guide/indexers/index.md).|
|[(T) x](type-testing-and-cast.md#cast-expression)|Operátor přetypování nemůže být přetížen, ale můžete definovat vlastní převody typů, které mohou být provedeny výrazem přetypování. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment) , [\*=](arithmetic-operators.md#compound-assignment) , [/=](arithmetic-operators.md#compound-assignment) , [%=](arithmetic-operators.md#compound-assignment) , [&=](boolean-logical-operators.md#compound-assignment) , [&#124;=](boolean-logical-operators.md#compound-assignment), [^=](boolean-logical-operators.md#compound-assignment) , [\<\<=](bitwise-and-shift-operators.md#compound-assignment) ,[>>=](bitwise-and-shift-operators.md#compound-assignment)|Operátory složeného přiřazení nelze explicitně přečítat. Nicméně při přetížení binárního operátoru je odpovídající složený operátor přiřazení, pokud existuje, také implicitně přetížený. Například `+=` je vyhodnocen pomocí `+` , který může být přetížen.|
|[^ x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x. y](member-access-operators.md#member-access-expression-), [`x?.y`](member-access-operators.md#null-conditional-operators--and-) , [c? t: f](conditional-operator.md), [x?? y](null-coalescing-operator.md), [x?? = y](null-coalescing-operator.md), [x... y](member-access-operators.md#range-operator-), [x->y](pointer-related-operators.md#pointer-member-access-operator--), [=>](lambda-operator.md) , [f (x)](member-access-operators.md#invocation-expression-), [as](type-testing-and-cast.md#as-operator), [await](await.md), [zaškrtnutí](../keywords/checked.md), [nezaškrtnuto](../keywords/unchecked.md), [Default](default.md), [Delegate](delegate-operator.md), [is](type-testing-and-cast.md#is-operator), [nameof](nameof.md), [New](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Tyto operátory nemůžou být přetížené.|

> [!NOTE]
> Operátory porovnání musí být přetíženy v páru. To znamená, že pokud je jeden operátor páru přetížený, druhý operátor musí být přetížený. Tyto páry jsou následující:
>
> - `==``!=`operátory a
> - `<``>`operátory a
> - `<=``>=`operátory a

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Přetěžování operátoru](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operátory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Operátory převodu definované uživatelem](user-defined-conversion-operators.md)
- [Pokyny pro návrh – přetížení operátorů](../../../standard/design-guidelines/operator-overloads.md)
- [Pokyny pro návrh – operátory rovnosti](../../../standard/design-guidelines/equality-operators.md)
- [Proč jsou přetížené operátory vždycky statické v jazyce C#?](https://docs.microsoft.com/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
