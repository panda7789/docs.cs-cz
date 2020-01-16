---
title: Typy hodnot s možnou hodnotou null – C# referenční informace
description: Další informace C# o typech hodnot s možnou hodnotou null a jejich použití
ms.date: 11/04/2019
helpviewer_keywords:
- nullable value types [C#]
ms.openlocfilehash: 3b9a29e75fe894f7d8a0751feefa9eb0a39baa2c
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964313"
---
# <a name="nullable-value-types-c-reference"></a>Typy hodnot s možnou hodnotou null (C# Referenční dokumentace)

Typ hodnoty s možnou hodnotou null `T?` představuje všechny hodnoty svého základního [typu hodnoty](../keywords/value-types.md) `T` a další hodnotu [null](../keywords/null.md) . Můžete například přiřadit libovolné z následujících tří hodnot `bool?` proměnné: `true`, `false`nebo `null`. Základní typ hodnoty `T` nemůže být typ hodnoty s možnou hodnotou null.

> [!NOTE]
> C#8,0 zavádí funkci typů odkazů s možnou hodnotou null. Další informace naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md). Typy s C# možnou hodnotou null jsou k dispozici od 2.

Libovolný typ hodnoty s možnou hodnotou null je instance obecné <xref:System.Nullable%601?displayProperty=nameWithType> struktury. Můžete odkazovat na typ hodnoty s možnou hodnotou null s podkladovým typem `T` v některém z následujících formulářů, které lze zaměnit: `Nullable<T>` nebo `T?`.

Pokud potřebujete reprezentovat nedefinovanou hodnotu základního typu hodnoty, obvykle se používá typ hodnoty s možnou hodnotou null. Například logická hodnota nebo `bool`proměnná může být pouze `true` nebo `false`. V některých aplikacích však může být hodnota proměnné nedefinovaná nebo chybí. Pole databáze může například obsahovat `true` nebo `false`, nebo nemusí vůbec obsahovat žádnou hodnotu, to znamená `NULL`. V tomto scénáři můžete použít `bool?` typ.

## <a name="declaration-and-assignment"></a>Deklarace a přiřazení

Typ hodnoty je implicitně převoditelný na odpovídající typ hodnoty s možnou hodnotou null, takže můžete přiřadit hodnotu proměnné typu hodnoty s možnou hodnotou null, jako byste to proznamenali pro svůj základní typ hodnoty. Můžete také přiřadit hodnotu `null`. Příklad:

[!code-csharp[declare and assign](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Declaration)]

Výchozí hodnota typu hodnoty s možnou hodnotou null představuje `null`, to znamená, že se jedná o instanci, jejíž vlastnost <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> vrací `false`.

## <a name="examination-of-an-instance-of-a-nullable-value-type"></a>Zkoumání instance typu hodnoty s možnou hodnotou null

Počínaje C# 7,0 můžete použít [operátor`is` se vzorkem typu](../operators/type-testing-and-cast.md#type-testing-with-pattern-matching) pro prohlédnutí instance typu hodnoty s možnou hodnotou null pro `null` a načtení hodnoty nadřazeného typu:

[!code-csharp-interactive[use pattern matching](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#PatternMatching)]

Vždy můžete použít následující vlastnosti jen pro čtení k prohlédnutí a získání hodnoty proměnné typu s možnou hodnotou null:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> určuje, zda instance typu hodnoty s možnou hodnotou null má hodnotu svého nadřízeného typu.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> Získá hodnotu základního typu, pokud je <xref:System.Nullable%601.HasValue%2A> `true`. Pokud je <xref:System.Nullable%601.HasValue%2A> `false`, vlastnost <xref:System.Nullable%601.Value%2A> vyvolá <xref:System.InvalidOperationException>.

Následující příklad používá vlastnost `HasValue` k otestování, zda proměnná obsahuje hodnotu před jejich zobrazením:

[!code-csharp-interactive[use HasValue](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#HasValue)]

Můžete také porovnat proměnnou typu hodnoty s možnou hodnotou null s `null` namísto použití vlastnosti `HasValue`, jak ukazuje následující příklad:

[!code-csharp-interactive[use comparison with null](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#CompareWithNull)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Převod z typu hodnoty s možnou hodnotou null na nadřízený typ

Pokud chcete přiřadit hodnotu typu hodnoty s možnou hodnotou null na proměnnou typu hodnoty, která není null, možná budete muset zadat hodnotu, která má být přiřazena místo `null`. Použijte [operátor slučování s hodnotou null `??`](../operators/null-coalescing-operator.md) k tomu, abyste to mohli udělat (můžete také použít metodu <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> pro stejný účel):

[!code-csharp-interactive[?? operator](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#NullCoalescing)]

Pokud chcete použít [výchozí](default-values.md) hodnotu základního typu hodnoty místo `null`, použijte metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>.

Typ hodnoty s možnou hodnotou null můžete také explicitně přetypovat na typ, který není null, jak ukazuje následující příklad:

[!code-csharp[explicit cast](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Cast)]

V době běhu, pokud je hodnota typu hodnoty s možnou hodnotou null `null`, vyvolá explicitní přetypování <xref:System.InvalidOperationException>.

Typ hodnoty, která není null, `T`, se implicitně převodit na odpovídající typ hodnoty s možnou hodnotou null `T?`.

## <a name="lifted-operators"></a>Zrušené operátory

Předdefinované unární a binární operátory nebo jakékoli přetížené operátory, které jsou podporovány hodnotou typu `T`, jsou podporovány také odpovídajícím typem hodnoty s možnou hodnotou null `T?`. Tyto operátory, označované také jako přenesené *operátory*, vyvolávají `null`, pokud jsou jeden nebo oba operandy `null`; v opačném případě operátor používá k výpočtu výsledku obsažené hodnoty operandů. Příklad:

[!code-csharp[lifted operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#LiftedOperator)]

> [!NOTE]
> Pro `bool?` typ `&` předdefinované operátory a `|` nepostupují podle pravidel popsaných v této části: výsledek vyhodnocení operátoru může být bez hodnoty null, i když je jeden z operandů `null`. Další informace naleznete v části s [možnou hodnotou null logických operátorů](../operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../operators/boolean-logical-operators.md) .

Pro [operátory porovnání](../operators/comparison-operators.md) `<`, `>`, `<=`a `>=`platí, že pokud je jeden nebo oba operandy `null`, výsledek je `false`; v opačném případě jsou obsažené hodnoty operandů porovnány. Nepředpokládáme, že protože konkrétní porovnání (například `<=`) vrátí `false`, opačné porovnání (`>`) vrátí `true`. Následující příklad ukazuje, že 10

- ani větší než nebo rovno `null`
- bez `null`

[!code-csharp-interactive[relational and equality operators](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#ComparisonOperators)]

Předchozí příklad také ukazuje, že porovnání rovnosti dvou instancí typu s možnou hodnotou null, které jsou `null` vyhodnoceny jako `true`.

Pokud existuje [uživatelem definovaný převod](../operators/user-defined-conversion-operators.md) mezi dvěma typy hodnot, stejný převod lze použít také mezi odpovídajícími typy hodnot s možnou hodnotou null.

## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení

Instance typu hodnoty s možnou hodnotou null `T?` je [zabalená](../../programming-guide/types/boxing-and-unboxing.md) takto:

- Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `false`, je vytvořen odkaz s hodnotou null.
- Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`, odpovídající hodnota typu podkladové hodnoty `T` je zabalená, nikoli instance <xref:System.Nullable%601>.

Můžete unbox zabalenou hodnotu typu hodnoty `T` k odpovídajícímu typu hodnoty s možnou hodnotou null `T?`, jak ukazuje následující příklad:

[!code-csharp-interactive[boxing and unboxing](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#Boxing)]

## <a name="how-to-identify-a-nullable-value-type"></a>Jak identifikovat typ hodnoty s možnou hodnotou null

Následující příklad ukazuje, jak určit, zda <xref:System.Type?displayProperty=nameWithType> instance představuje konstruovaný typ hodnoty s možnou hodnotou null, tj. <xref:System.Nullable%601?displayProperty=nameWithType> typ se zadaným parametrem typu `T`:

[!code-csharp-interactive[whether Type is nullable](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsTypeNullable)]

Jak ukazuje příklad, použijte operátor [typeof](../operators/type-testing-and-cast.md#typeof-operator) k vytvoření instance <xref:System.Type?displayProperty=nameWithType>.

Chcete-li určit, zda je instance typu s možnou hodnotou null, nepoužívejte metodu <xref:System.Object.GetType%2A?displayProperty=nameWithType> k získání <xref:System.Type> instance, která má být testována pomocí předchozího kódu. Při volání metody <xref:System.Object.GetType%2A?displayProperty=nameWithType> u instance typu hodnoty s možnou hodnotou null je instance [zabalena](#boxing-and-unboxing) do <xref:System.Object>. Jako zabalení instance typu s možnou hodnotou null je ekvivalentem zabalení hodnoty nenulového typu, <xref:System.Object.GetType%2A> vrátí instanci <xref:System.Type>, která představuje nadřízený typ hodnoty s možnou hodnotou null:

[!code-csharp-interactive[GetType example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#GetType)]

Nepoužívejte také operátor [is](../operators/type-testing-and-cast.md#is-operator) k určení, zda je instance typu hodnot s možnou hodnotou null. Jak ukazuje následující příklad, nelze odlišit typy instance typu s možnou hodnotou null a její základní typ instance s operátorem `is`:

[!code-csharp-interactive[is operator example](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsOperator)]

K určení, zda je instance typu s možnou hodnotou null, lze použít kód prezentovaný v následujícím příkladu:

[!code-csharp-interactive[whether an instance is of a nullable type](~/samples/csharp/language-reference/builtin-types/NullableValueTypes.cs#IsInstanceNullable)]

> [!NOTE]
> Metody popsané v této části se nevztahují na [typy odkazů s možnou hodnotou null](../../nullable-references.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Typy s možnou hodnotou null](~/_csharplang/spec/types.md#nullable-types)
- [Zrušené operátory](~/_csharplang/spec/expressions.md#lifted-operators)
- [Implicitní převody s možnou hodnotou null](~/_csharplang/spec/conversions.md#implicit-nullable-conversions)
- [Explicitní převody s možnou hodnotou null](~/_csharplang/spec/conversions.md#explicit-nullable-conversions)
- [Zrušené operátory převodu](~/_csharplang/spec/conversions.md#lifted-conversion-operators)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Co přesně znamená "vyvoláno"?](https://docs.microsoft.com/archive/blogs/ericlippert/what-exactly-does-lifted-mean)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
- <xref:System.Nullable.GetUnderlyingType%2A?displayProperty=nameWithType>
- [Odkazové typy s možnou hodnotou null](../../nullable-references.md)
