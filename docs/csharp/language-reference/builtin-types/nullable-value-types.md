---
title: Nullable typy hodnot - C# odkaz
description: Informace o typech hodnot s možnou hodnotou c# s možnou hodnotou a jejich použití
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: c13ef6a091ec6aebd4608c5ed8d2c03b067c7312
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888069"
---
# <a name="nullable-value-types-c-reference"></a>Typy hodnot s hodnotou Null (odkaz jazyka C# )

`T?` *Typ hodnoty s možnou hodnotou null* představuje všechny hodnoty jeho [základního typu](value-types.md) `T` hodnoty a další [hodnotu null.](../keywords/null.md) Můžete například přiřadit `bool?` libovolnou z následujících tří `true` `false`hodnot `null`proměnné: , , nebo . Základní typ `T` hodnoty nemůže být samotný typ hodnoty s možnou hodnotou s možnou hodnotou.

> [!NOTE]
> C# 8.0 zavádí funkci typů odkazů s možnou hodnotou null. Další informace naleznete v [tématu Nullable reference types](nullable-reference-types.md). Null hodnoty typy jsou k dispozici počínaje C# 2.

Libovolný typ hodnoty s možnou <xref:System.Nullable%601?displayProperty=nameWithType> hodnotou null je instancí obecné struktury. Můžete odkazovat na typ hodnoty s `T` možnou hodnotou s hodnotou `Nullable<T>` `T?`s hodnotou s podkladovým typem v některém z následujících zaměnitelných formulářů: nebo .

Typ hodnoty s možnou hodnotou s možnou hodnotou s možnou hodnotou, pokud potřebujete reprezentovat nedefinovanou hodnotu základního typu hodnoty. Například boolean, nebo `bool`, proměnná `true` může `false`být pouze buď nebo . V některých aplikacích však může být hodnota proměnné nedefinovaná nebo chybí. Například databázové pole `true` může `false`obsahovat nebo , nebo může obsahovat žádnou hodnotu vůbec, to znamená . `NULL` Můžete použít `bool?` typ v tomto scénáři.

## <a name="declaration-and-assignment"></a>Prohlášení a postoupení

Jako typ hodnoty je implicitně převoditelný na odpovídající typ hodnoty s hodnotou s hodnotou s hodnotou, můžete přiřadit hodnotu proměnné typu hodnoty s hodnotou s možnou hodnotou, jako byste to udělali pro jeho základní typ hodnoty. Můžete také přiřadit `null` hodnotu. Příklad:

[!code-csharp[declare and assign](snippets/NullableValueTypes.cs#Declaration)]

Výchozí hodnota typu hodnoty s `null`možnou hodnotou s možnou <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> hodnotou s možnou hodnotou představuje , to znamená, že je to instance, jejíž vlastnost vrátí `false`.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Zkoumání instance typu hodnoty s možnou hodnotou, jejíž hodnotu lze

Počínaje C# 7.0, můžete použít [ `is` operátor s typem vzor](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) jak zkoumat instanci typu hodnoty s možnou hodnotou s hodnotou s hodnotou null `null` a načíst hodnotu základního typu:

[!code-csharp-interactive[use pattern matching](snippets/NullableValueTypes.cs#PatternMatching)]

Vždy můžete použít následující vlastnosti jen pro čtení prozkoumat a získat hodnotu proměnné typu hodnoty s hodnotou null:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>označuje, zda má instance typu hodnoty s možnou hodnotou, která má hodnotu, hodnotu svého základního typu.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>získá hodnotu základního <xref:System.Nullable%601.HasValue%2A> typu, pokud je `true`. Pokud <xref:System.Nullable%601.HasValue%2A> `false`je <xref:System.Nullable%601.Value%2A> , vlastnost <xref:System.InvalidOperationException>vyvolá .

Následující příklad používá `HasValue` vlastnost k testování, zda proměnná obsahuje hodnotu před zobrazením:

[!code-csharp-interactive[use HasValue](snippets/NullableValueTypes.cs#HasValue)]

Můžete také porovnat proměnnou typu hodnoty `null` s možnou `HasValue` hodnotou s hodnotou s hodnotou s namísto použití vlastnosti, jak ukazuje následující příklad:

[!code-csharp-interactive[use comparison with null](snippets/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Převod z typu hodnoty s možnou hodnotou s možnou hodnotou na podkladový typ

Pokud chcete přiřadit hodnotu typu hodnoty s možnou hodnotou s hodnotou s hodnotou, která nelze `null`použít, proměnné typu hodnoty, kterou nelze hodnotit, může být nutné zadat hodnotu, která bude přiřazena místo . K tomu použijte [operátor `??` null-coalescing](../operators/null-coalescing-operator.md) (metodu <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> můžete použít také ke stejnému účelu):

[!code-csharp-interactive[?? operator](snippets/NullableValueTypes.cs#NullCoalescing)]

Pokud chcete použít [výchozí](default-values.md) hodnotu základního typu `null`hodnoty místo <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , použijte metodu.

Můžete také explicitně přetypovat typ hodnoty s hodnotou s hodnotou, který nelze uvážit, jak ukazuje následující příklad:

[!code-csharp[explicit cast](snippets/NullableValueTypes.cs#Cast)]

V době běhu, pokud je `null`hodnota typu hodnoty s možnou <xref:System.InvalidOperationException>hodnotou null , explicitní přetypování vyvolá .

Typ `T` hodnoty s hodnotou, který neshovuje, je implicitně převoditelný na odpovídající typ `T?`hodnoty s možnou hodnotou, kterou lze hodnotu hodnotit .

## <a name="lifted-operators"></a>Zdvižené operátory

Předdefinované unární a binární [operátory](../operators/index.md) nebo všechny přetížené `T` operátory, které jsou podporovány `T?`typem hodnoty jsou také podporovány odpovídající typ hodnoty s možnou hodnotou null . Tito provozovatelé, také známí jako `null` *zdvižené obsluhy*, vyrábějí, pokud se jedná `null`o jeden nebo oba operandy ; v opačném případě operátor používá obsažené hodnoty svých operandů k výpočtu výsledku. Příklad:

[!code-csharp[lifted operators](snippets/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Pro `bool?` typ předdefinované `&` a `|` operátory nedodržují pravidla popsaná v této části: výsledek vyhodnocení operátoru může být non-null i v případě, že jeden z operandů je `null`. Další informace naleznete v části [Nullable Boolean logické operátory](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) článku [logické operátory logické.](../operators/boolean-logical-operators.md)

Pro [porovnávací operátory](../operators/comparison-operators.md) `<` `>`, `<=`, , a `null` `false` `>=`, pokud je jeden nebo oba operandy , je výsledkem ; jinak jsou porovnány obsažené hodnoty operandů. Nepředpokládejte, že vzhledem k `<=`tomu, `false`že konkrétní`>`porovnání `true`(například ) vrátí , opačné porovnání ( ) vrátí . Následující příklad ukazuje, že 10 je

- větší nebo rovno`null`
- ani méně než`null`

[!code-csharp-interactive[relational and equality operators](snippets/NullableValueTypes.cs#ComparisonOperators)]

Pro [operátor](../operators/equality-operators.md#equality-operator-) `==`rovnosti , pokud jsou `null`oba operandy , je `true`výsledkem `null`výsledek , `false`pokud je pouze jeden z operandů , výsledek je ; jinak jsou porovnány obsažené hodnoty operandů.

Pro [operátor](../operators/equality-operators.md#inequality-operator-) `!=`nerovnosti , pokud jsou `null`oba operandy , je `false`výsledkem `null`výsledek , `true`pokud je pouze jeden z operandů , výsledek je ; jinak jsou porovnány obsažené hodnoty operandů.

Pokud existuje [uživatelem definovaný převod](../operators/user-defined-conversion-operators.md) mezi dvěma typy hodnot, lze použít stejný převod také mezi odpovídajícími typy hodnot s možnou hodnotou, kterou lze použít.

## <a name="boxing-and-unboxing"></a>Box a rozbalení

Instance typu `T?` hodnoty s možnou hodnotou s hodnotou s možnou hodnotou null je [zabalena](../../programming-guide/types/boxing-and-unboxing.md) takto:

- Pokud <xref:System.Nullable%601.HasValue%2A> `false`vrátí , je vytvořen odkaz null.
- Pokud <xref:System.Nullable%601.HasValue%2A> `true`vrátí , odpovídající hodnota základního typu `T` hodnoty je <xref:System.Nullable%601>zabalena, nikoli instance .

Zabalenou hodnotu typu `T` hodnoty můžete rozbalit na odpovídající `T?`hodnotu s hodnotou s možnou hodnotou , jak ukazuje následující příklad:

[!code-csharp-interactive[boxing and unboxing](snippets/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Jak identifikovat typ hodnoty s možnou hodnotou s možnou hodnotou

Následující příklad ukazuje, jak <xref:System.Type?displayProperty=nameWithType> zjistit, zda instance představuje početný typ <xref:System.Nullable%601?displayProperty=nameWithType> hodnoty s možnou `T`hodnotou s možnou hodnotou, to znamená typ s parametrem zadaného typu :

[!code-csharp-interactive[whether Type is nullable](snippets/NullableValueTypes.cs#IsTypeNullable)]

Jak ukazuje příklad, pomocí [operátoru typeof](../operators/type-testing-and-cast.md#typeof-operator) vytvořte instanci. <xref:System.Type?displayProperty=nameWithType>

Pokud chcete určit, zda je instance typu hodnoty s možnou <xref:System.Object.GetType%2A?displayProperty=nameWithType> hodnotou, <xref:System.Type> kterou lze použít, nepoužívejte metodu k získání instance, která má být testována s předchozím kódem. Při volání <xref:System.Object.GetType%2A?displayProperty=nameWithType> metody na instanci typu hodnoty s možnou <xref:System.Object>hodnotou, kterou lze hodnotit, je instance [zabalena](#boxing-and-unboxing) do . Jako zabalení non-null instance typu hodnoty s hodnotou, kterou lze hodnotu <xref:System.Type> null je ekvivalentní zabalení hodnoty základního typu, vrátí instanci, <xref:System.Object.GetType%2A> která představuje základní typ typu hodnoty s možnou hodnotou null:

[!code-csharp-interactive[GetType example](snippets/NullableValueTypes.cs#GetType)]

Také nepoužívejte [is](../operators/type-testing-and-cast.md#is-operator) operátor k určení, zda je instance typu hodnoty s možnou hodnotou s hodnotou null. Jak ukazuje následující příklad, nelze rozlišit typy instance typu hodnoty s `is` možnou hodnotou s hodnotou s hodnotou s možnou hodnotou a její základní instanci typu s operátorem:

[!code-csharp-interactive[is operator example](snippets/NullableValueTypes.cs#IsOperator)]

Kód uvedený v následujícím příkladu můžete použít k určení, zda je instance typu hodnoty s možnou hodnotou s hodnotou s možnou hodnotou:

[!code-csharp-interactive[whether an instance is of a nullable type](snippets/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Metody popsané v této části nejsou použitelné v případě [typů odkazů s možnou hodnotou null](nullable-reference-types.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Typy s povolenou hodnotou Null](~/_csharplang/spec/types.md#nullable-types)
- [Zdvižené operátory](~/_csharplang/spec/expressions.md#lifted-operators)
- [Implicitní převody s možnou hodnotou null](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Explicitní převody s možnou hodnotou null](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Operátory zrušených konverzí](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Co přesně znamená "zvednutý"?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Odkazové typy s možnou hodnotou null](nullable-reference-types.md)
