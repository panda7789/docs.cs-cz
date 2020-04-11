---
title: Přetížení operátoru - odkaz Jazyka C#
description: Zjistěte, jak přetížení C# operátor a které c# operátory jsou přetížení.
ms.date: 07/05/2019
f1_keywords:
- operator_CSharpKeyword
helpviewer_keywords:
- operator keyword [C#]
- operator overloading [C#]
ms.openlocfilehash: 18da3a22d22f338d2f319d394d50d08e4d35e7eb
ms.sourcegitcommit: 43cbde34970f5f38f30c43cd63b9c7e2e83717ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2020
ms.locfileid: "81121432"
---
# <a name="operator-overloading-c-reference"></a>Přetížení operátoru (odkaz C#)

Uživatelem definovaný typ může přetížit předdefinovaný operátor Jazyka C#. To znamená, že typ může poskytnout vlastní implementaci operace v případě, že jeden nebo oba operandy jsou tohoto typu. Overloadable [operátory](#overloadable-operators) část ukazuje, které operátory Jazyka C# může být přetížena.

Pomocí `operator` klíčového slova deklarujte operátor. Prohlášení hospodářského subjektu musí splňovat tato pravidla:

- Obsahuje `public` `static` modifikátor a modifikátor.
- Unární operátor má jeden vstupní parametr. Binární operátor má dva vstupní parametry. V každém případě musí mít alespoň `T` `T?` jeden `T` parametr typ nebo kde je typ, který obsahuje deklaraci operátora.

Následující příklad definuje zjednodušenou strukturu představující racionální číslo. Struktura přetíží některé [aritmetické operátory](arithmetic-operators.md):

[!code-csharp[fraction example](snippets/OperatorOverloading.cs)]

Předchozí příklad můžete rozšířit [definováním implicitního převodu](user-defined-conversion-operators.md) z `int` na `Fraction`. Přetížené operátory by pak podporovat argumenty těchto dvou typů. To znamená, že by bylo možné přidat celé číslo do zlomku a získat zlomek jako výsledek.

`operator` Klíčové slovo můžete také použít k definování převodu vlastního typu. Další informace naleznete v [tématu User-defined operátory převodu](user-defined-conversion-operators.md).

## <a name="overloadable-operators"></a>Přetížené operátory

Následující tabulka obsahuje informace o přetížení operátorů jazyka C#:

| Operátory | Přetížení |
| --------- | --------------- |
|[+x](arithmetic-operators.md#unary-plus-and-minus-operators), [-x](arithmetic-operators.md#unary-plus-and-minus-operators), [!x](boolean-logical-operators.md#logical-negation-operator-) [--](arithmetic-operators.md#decrement-operator---), [~x](bitwise-and-shift-operators.md#bitwise-complement-operator-), [++](arithmetic-operators.md#increment-operator-), [true](true-false-operators.md), [false](true-false-operators.md)|Tyto unární operátory mohou být přetíženy.|
|[x + y](addition-operator.md), [x - y](subtraction-operator.md), x [ \* y](arithmetic-operators.md#multiplication-operator-), x / [y](arithmetic-operators.md#division-operator-), x [% y](arithmetic-operators.md#remainder-operator-), x & [y](boolean-logical-operators.md#logical-and-operator-), x [&#124; y](boolean-logical-operators.md#logical-or-operator-), x ^ [y](boolean-logical-operators.md#logical-exclusive-or-operator-), [x \< \< y](bitwise-and-shift-operators.md#left-shift-operator-), [x >> y](bitwise-and-shift-operators.md#right-shift-operator-), x [== y](equality-operators.md#equality-operator-), x [!= y](equality-operators.md#inequality-operator-), x [ \< y](comparison-operators.md#less-than-operator-), x y , x > [y](comparison-operators.md#greater-than-operator-), [ \<x = y](comparison-operators.md#less-than-or-equal-operator-), x >= [y](comparison-operators.md#greater-than-or-equal-operator-)|Tyto binární operátory mohou být přetíženy. Některé operátory musí být přetíženy ve dvojicích; Další informace naleznete v poznámce, která následuje po této tabulce.|
|[x && y](boolean-logical-operators.md#conditional-logical-and-operator-), [x &#124;&#124; y](boolean-logical-operators.md#conditional-logical-or-operator-)|Podmíněné logické operátory nemohou být přetíženy. Pokud však typ s přetíženým `&` <code>&#124;</code> `&&` [ `true` a `false` operátory](true-false-operators.md) také určitým způsobem přetíží operátor nebo, operátor nebo <code>&#124;&#124;</code> může být vyhodnocen pro operandy tohoto typu. Další informace naleznete v části [Uživatelem definované podmíněné logické operátory](~/_csharplang/spec/expressions.md#user-defined-conditional-logical-operators) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).|
|[a&#91;i&#93;](member-access-operators.md#indexer-operator-)|Přístup k prvkům není považován za přetížený operátor, ale můžete definovat [indexer](../../programming-guide/indexers/index.md).|
|[(T)x](type-testing-and-cast.md#cast-expression)|Operátor přetypování nemůže být přetížen, ale můžete definovat převody vlastního typu, které lze provést výrazem přetypování. Další informace naleznete v [tématu User-defined operátory převodu](user-defined-conversion-operators.md).|
|[+=](arithmetic-operators.md#compound-assignment), [-=](arithmetic-operators.md#compound-assignment) [ \* ](arithmetic-operators.md#compound-assignment), [/=](arithmetic-operators.md#compound-assignment) [%=](arithmetic-operators.md#compound-assignment), [&=](boolean-logical-operators.md#compound-assignment), , [^=](boolean-logical-operators.md#compound-assignment) [ \< \< ](bitwise-and-shift-operators.md#compound-assignment) [,&#124;=](boolean-logical-operators.md#compound-assignment), ,[>>=](bitwise-and-shift-operators.md#compound-assignment)|Operátory složeného přiřazení nelze explicitně přetížit. Však při přetížení binární operátor, odpovídající složené přiřazení operátor, pokud existuje, je také implicitně přetížené. Například `+=` je vyhodnocenpomocí `+`, které mohou být přetíženy.|
|[^x](member-access-operators.md#index-from-end-operator-), [x = y](assignment-operator.md), [x.y](member-access-operators.md#member-access-expression-), [c ? t : f](conditional-operator.md), x [?? y](null-coalescing-operator.md), x [?? = y](null-coalescing-operator.md), [x.. y](member-access-operators.md#range-operator-), [x->y](pointer-related-operators.md#pointer-member-access-operator--) [=>](lambda-operator.md), , [f(x)](member-access-operators.md#invocation-expression-), [as](type-testing-and-cast.md#as-operator), [await](await.md), [checked](../keywords/checked.md), [unchecked](../keywords/unchecked.md), [default](default.md), [delegate](delegate-operator.md), [is](type-testing-and-cast.md#is-operator), [nameof](nameof.md), [new](new-operator.md), [sizeof](sizeof.md), [stackalloc](stackalloc.md), [typeof](type-testing-and-cast.md#typeof-operator)|Tyto operátory nelze přetížit.|

> [!NOTE]
> Operátory porovnání musí být přetížené v párech. To znamená, že pokud je přetížený některý z operátorů páru, musí být přetížen také druhý operátor. Tyto páry jsou následující:
>
> - `==`a `!=` provozovatelé
> - `<`a `>` provozovatelé
> - `<=`a `>=` provozovatelé

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Přetěžování operátoru](~/_csharplang/spec/expressions.md#operator-overloading)
- [Operátory](~/_csharplang/spec/classes.md#operators)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory jazyka C#](index.md)
- [Operátory převodu definované uživatelem](user-defined-conversion-operators.md)
- [Pokyny pro návrh - Přetížení obsluhy](../../../standard/design-guidelines/operator-overloads.md)
- [Pokyny pro návrh - Operátory rovnosti](../../../standard/design-guidelines/equality-operators.md)
- [Proč jsou přetížené operátory vždy statické v c#?](https://docs.microsoft.com/archive/blogs/ericlippert/why-are-overloaded-operators-always-static-in-c)
