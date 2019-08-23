---
title: Operátory typu testování a přetypování – C# reference
description: Přečtěte C# si o operátorech, pomocí kterých můžete kontrolovat typ výsledku výrazu a v případě potřeby ho převést na jiný typ.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
helpviewer_keywords:
- type-testing operators [C#]
- conversion operators [C#]
- type conversion [C#]
- is operator [C#]
- as operator [C#]
- cast operator [C#]
- cast expression [C#]
- () operator [C#]
- typeof operator [C#]
ms.openlocfilehash: 62186409fdc1abb2275af535be3ae939a1e63323
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922286"
---
# <a name="type-testing-and-cast-operators-c-reference"></a>Operátory testování typů a přetypování (C# Referenční dokumentace)

K provedení kontroly typu nebo převodu typu můžete použít následující operátory:

- [is – operátor](#is-operator): Pokud chcete zjistit, jestli je běhový typ výrazu kompatibilní s daným typem
- [as – operátor](#as-operator)pro explicitní převod výrazu na daný typ, pokud je jeho typ modulu runtime kompatibilní s daným typem
- [operátor přetypování ()](#cast-operator-): k provedení explicitního převodu
- [typeof – operátor](#typeof-operator): pro získání <xref:System.Type?displayProperty=nameWithType> instance pro typ

## <a name="is-operator"></a>is – operátor

`is` Operátor zkontroluje, zda je typ modulu runtime výsledku výrazu kompatibilní s daným typem. Počínaje C# 7,0, `is` operátor také testuje výsledek výrazu proti vzorci.

Výraz s operátorem testování `is` typu má následující formu.

```csharp
E is T
```

kde `E` je výraz, který vrací hodnotu a `T` je názvem typu nebo parametrem typu. `E`nemůže být anonymní metoda nebo výraz lambda.

`false` `T` Výraz vrátí `true` , pokud výsledek `E` není null a lze jej převést na typ pomocí převodu odkazu, převodu zabalení nebo převodu rozbalení. v opačném případě vrátí. `E is T` Operátor `is` nebere v úvahu uživatelsky definované převody.

Následující příklad ukazuje, že `is` operátor vrátí `true` , pokud typ modulu runtime výsledku výrazu je odvozen z daného typu, to znamená, že existuje převod odkazu mezi typy:

[!code-csharp[is with reference conversion](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Následující příklad ukazuje, že operátor `is` vezme v úvahu převody zabalení a rozbalení, ale nebere v úvahu číselné převody:

[!code-csharp-interactive[is with int](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsWithInt)]

Informace o C# převodech naleznete v kapitole [převody](~/_csharplang/spec/conversions.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Testování typu s porovnáváním vzorů

Počínaje C# 7,0, `is` operátor také testuje výsledek výrazu proti vzorci. Konkrétně podporuje vzor typu v následujícím tvaru:

```csharp
E is T v
```

kde `E` je výraz, který vrací hodnotu, `T` je název typu nebo parametr typu a `v` je nová lokální proměnná typu `T`. Pokud `E` výsledek je jiný než null a lze jej převést na `T` odkaz, zabalení nebo rozbalení `E is T v` , výraz se vrátí `true` a převedená hodnota výsledku `E` je přiřazena k proměnná `v`.

Následující příklad ukazuje použití `is` operátoru se vzorem typu:

[!code-csharp-interactive[is with type pattern](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Další informace o vzoru typu a dalších podporovaných vzorech naleznete v tématu [porovnávání vzorů s](../keywords/is.md#pattern-matching-with-is)parametrem is.

## <a name="as-operator"></a>as – operátor

`as` Operátor explicitně převede výsledek výrazu na daný odkaz nebo typ hodnoty s možnou hodnotou null. Pokud převod není možný, `as` vrátí `null`operátor. Na`as` rozdíl od [operátoru přetypování ()](#cast-operator-), operátor nikdy nevyvolá výjimku.

Výraz formuláře

```csharp
E as T
```

kde `E` je výraz, který vrací hodnotu a `T` je názvem typu nebo parametrem typu, vytvoří stejný výsledek jako

```csharp
E is T ? (T)(E) : (T)null
```

s výjimkou, že `E` je vyhodnocena pouze jednou.

`as` Operátor zohledňuje pouze odkazy, převody s možnou hodnotou null, zabalení a rozbalení. `as` Operátor nelze použít k provedení převodu definovaného uživatelem. K tomu použijte [operátor přetypování ()](#cast-operator-).

Následující příklad ukazuje použití `as` operátoru:

[!code-csharp-interactive[as operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Jak ukazuje předchozí příklad, je nutné porovnat výsledek `as` výrazu s `null` a zjistit, zda převod proběhl úspěšně. Počínaje C# 7,0 můžete použít [operátor is](#type-testing-with-pattern-matching) pro testování, zda je převod úspěšný, a pokud je úspěšný, přiřaďte výsledek k nové proměnné.

## <a name="cast-operator-"></a>Operátor přetypování ()

Výraz přetypování formuláře `(T)E` provádí explicitní převod výsledku výrazu `E` na typ `T`. Pokud neexistuje žádný explicitní převod z typu `E` na typ `T`, dojde k chybě při kompilaci. V době spuštění explicitní převod nemusí být úspěšný a výraz přetypování může vyvolat výjimku.

Následující příklad ukazuje explicitní číselné a referenční převody:

[!code-csharp-interactive[cast expression](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#Cast)]

Informace o podporovaných explicitních převodech naleznete v části [explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md). Informace o tom, jak definovat vlastní explicitní nebo implicitní převod typu, naleznete v části [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Další použití pro ()

K [volání metody nebo vyvolání delegáta](member-access-operators.md#invocation-operator-)můžete také použít kulaté závorky.

Jiné použití závorek je upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu. Další informace najdete v tématu [ C# operátory](index.md).

## <a name="typeof-operator"></a>typeof – operátor

`typeof` Operátor získá<xref:System.Type?displayProperty=nameWithType> instanci pro typ. Argument `typeof` operátoru musí být název typu nebo parametr typu, jak ukazuje následující příklad:

[!code-csharp-interactive[typeof operator](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOf)]

`typeof` Operátor můžete použít také s nevázanými obecnými typy. Název nevázaného obecného typu musí obsahovat odpovídající počet čárek, což je jedna hodnota, která je menší než počet parametrů typu. Následující příklad ukazuje použití `typeof` operátoru s nevázaným obecným typem:

[!code-csharp-interactive[typeof unbound generic](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Výraz nemůže být argumentem `typeof` operátoru. Chcete-li <xref:System.Type?displayProperty=nameWithType> získat instanci pro běhový typ výsledku výrazu, <xref:System.Object.GetType%2A?displayProperty=nameWithType> použijte metodu.

### <a name="type-testing-with-the-typeof-operator"></a>Testování typu pomocí `typeof` operátoru

`typeof` Použijte operátor ke kontrole, zda typ modulu runtime výsledku výrazu přesně odpovídá danému typu. Následující příklad ukazuje rozdíl mezi kontrolou typu provedenými s `typeof` operátorem a operátorem [is](#is-operator):

[!code-csharp[typeof vs is](~/samples/csharp/language-reference/operators/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Přetížení operátoru

Operátory, `as`anejsoupřetíženy. `is` `typeof`

Uživatelsky definovaný typ nemůže přetížit `()` operátor, ale může definovat vlastní převody typů, které mohou být provedeny výrazem přetypování. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Operátor is](~/_csharplang/spec/expressions.md#the-is-operator)
- [Operátor as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Výrazy cast](~/_csharplang/spec/expressions.md#cast-expressions)
- [Operátor typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Operátory jazyka C#](index.md)
- [Postupy: Bezpečné přetypování pomocí porovnávání vzorů a operátorů is a as](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
