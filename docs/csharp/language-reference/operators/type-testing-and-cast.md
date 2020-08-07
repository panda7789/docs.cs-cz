---
title: Operátory testování typů a přetypování – reference jazyka C#
description: Seznamte se s operátory jazyka C#, které lze použít ke kontrole typu výsledku výrazu a v případě potřeby jej převést na jiný typ.
ms.date: 06/21/2019
author: pkulikov
f1_keywords:
- is_CSharpKeyword
- as_CSharpKeyword
- ()_CSharpKeyword
- typeof_CSharpKeyword
- as
- typeof
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
ms.openlocfilehash: 328a40f0213cbb55f86e16625507c1a5a5d775fb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855826"
---
# <a name="type-testing-operators-and-cast-expression-c-reference"></a>Operátory testování typů a výraz přetypování (Referenční dokumentace jazyka C#)

Pomocí následujících operátorů a výrazů můžete provést kontrolu typu nebo převod typu:

- [is – operátor](#is-operator): Pokud chcete zjistit, jestli je běhový typ výrazu kompatibilní s daným typem
- [as – operátor](#as-operator)pro explicitní převod výrazu na daný typ, pokud je jeho typ modulu runtime kompatibilní s daným typem
- [výraz cast](#cast-expression): k provedení explicitního převodu
- [typeof – operátor](#typeof-operator): pro získání <xref:System.Type?displayProperty=nameWithType> instance pro typ

## <a name="is-operator"></a>is – operátor

`is`Operátor zkontroluje, zda je typ modulu runtime výsledku výrazu kompatibilní s daným typem. Počínaje jazykem C# 7,0 `is` operátor také testuje výsledek výrazu proti vzorci.

Výraz s `is` operátorem testování typu má následující formu.

```csharp
E is T
```

kde `E` je výraz, který vrací hodnotu a `T` je názvem typu nebo parametrem typu. `E`nemůže být anonymní metoda nebo výraz lambda.

`E is T`Výraz vrátí `true` , pokud výsledek `E` není null a lze jej převést na typ `T` pomocí převodu odkazu, převodu zabalení nebo převodu rozbalení. v opačném případě vrátí `false` . `is`Operátor nebere v úvahu uživatelsky definované převody.

Následující příklad ukazuje, že `is` operátor vrátí, `true` Pokud typ modulu runtime výsledku výrazu je odvozen z daného typu, to znamená, že existuje převod odkazu mezi typy:

[!code-csharp[is with reference conversion](snippets/TypeTestingAndConversionOperators.cs#IsWithReferenceConversion)]

Následující příklad ukazuje, že `is` operátor vezme v úvahu převody zabalení a rozbalení, ale nebere v úvahu [číselné převody](../builtin-types/numeric-conversions.md):

[!code-csharp-interactive[is with int](snippets/TypeTestingAndConversionOperators.cs#IsWithInt)]

Informace o převodech jazyka C# naleznete v kapitole [převody](~/_csharplang/spec/conversions.md) [specifikace jazyka c#](~/_csharplang/spec/introduction.md).

### <a name="type-testing-with-pattern-matching"></a>Testování typu s porovnáváním vzorů

Počínaje jazykem C# 7,0 `is` operátor také testuje výsledek výrazu proti vzorci. Konkrétně podporuje vzor typu v následujícím tvaru:

```csharp
E is T v
```

kde `E` je výraz, který vrací hodnotu, `T` je název typu nebo parametr typu a `v` je nová lokální proměnná typu `T` . Pokud výsledek `E` je jiný než null a lze jej převést na `T` odkaz, zabalení nebo rozbalení, `E is T v` výraz se vrátí `true` a převedená hodnota výsledku `E` je přiřazena proměnné `v` .

Následující příklad ukazuje použití `is` operátoru se vzorem typu:

[!code-csharp-interactive[is with type pattern](snippets/TypeTestingAndConversionOperators.cs#IsTypePattern)]

Další informace o vzoru typu a dalších podporovaných vzorech naleznete v tématu [porovnávání vzorů s](../keywords/is.md#pattern-matching-with-is)parametrem is.

## <a name="as-operator"></a>Operátor as

`as`Operátor explicitně převede výsledek výrazu na daný odkaz nebo typ hodnoty s možnou hodnotou null. Pokud převod není možný, `as` vrátí operátor `null` . Na rozdíl od [výrazu přetypování](#cast-expression) `as` operátor nikdy nevyvolá výjimku.

Výraz formuláře

```csharp
E as T
```

kde `E` je výraz, který vrací hodnotu a `T` je názvem typu nebo parametrem typu, vytvoří stejný výsledek jako

```csharp
E is T ? (T)(E) : (T)null
```

s výjimkou, že `E` je vyhodnocena pouze jednou.

`as`Operátor zohledňuje pouze odkazy, převody s možnou hodnotou null, zabalení a rozbalení. Operátor nelze použít `as` k provedení převodu definovaného uživatelem. K tomu použijte [výraz cast](#cast-expression).

Následující příklad ukazuje použití `as` operátoru:

[!code-csharp-interactive[as operator](snippets/TypeTestingAndConversionOperators.cs#AsOperator)]

> [!NOTE]
> Jak ukazuje předchozí příklad, je nutné porovnat výsledek `as` výrazu s `null` a zjistit, zda převod proběhl úspěšně. Počínaje jazykem C# 7,0 můžete použít [operátor is](#type-testing-with-pattern-matching) pro testování, zda je převod úspěšný, a pokud je úspěšný, přiřaďte výsledek k nové proměnné.

## <a name="cast-expression"></a>Výraz cast

Výraz přetypování formuláře `(T)E` provádí explicitní převod výsledku výrazu `E` na typ `T` . Pokud neexistuje žádný explicitní převod z typu `E` na typ `T` , dojde k chybě při kompilaci. V době spuštění explicitní převod nemusí být úspěšný a výraz přetypování může vyvolat výjimku.

Následující příklad ukazuje explicitní číselné a referenční převody:

[!code-csharp-interactive[cast expression](snippets/TypeTestingAndConversionOperators.cs#Cast)]

Informace o podporovaných explicitních převodech naleznete v části [explicitní převody](~/_csharplang/spec/conversions.md#explicit-conversions) [specifikace jazyka C#](~/_csharplang/spec/introduction.md). Informace o tom, jak definovat vlastní explicitní nebo implicitní převod typu, naleznete v části [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

### <a name="other-usages-of-"></a>Další použití pro ()

K [volání metody nebo vyvolání delegáta](member-access-operators.md#invocation-expression-)můžete také použít kulaté závorky.

Jiné použití závorek je upravit pořadí, ve kterém se mají vyhodnocovat operace ve výrazu. Další informace naleznete v tématu [operátory jazyka C#](index.md).

## <a name="typeof-operator"></a>typeof – operátor

`typeof`Operátor získá <xref:System.Type?displayProperty=nameWithType> instanci pro typ. Argument `typeof` operátoru musí být název typu nebo parametr typu, jak ukazuje následující příklad:

[!code-csharp-interactive[typeof operator](snippets/TypeTestingAndConversionOperators.cs#TypeOf)]

Operátor můžete také použít `typeof` s nevázanými obecnými typy. Název nevázaného obecného typu musí obsahovat odpovídající počet čárek, což je jedna hodnota, která je menší než počet parametrů typu. Následující příklad ukazuje použití `typeof` operátoru s nevázaným obecným typem:

[!code-csharp-interactive[typeof unbound generic](snippets/TypeTestingAndConversionOperators.cs#TypeOfUnboundGeneric)]

Výraz nemůže být argumentem `typeof` operátoru. Chcete-li získat <xref:System.Type?displayProperty=nameWithType> instanci pro běhový typ výsledku výrazu, použijte <xref:System.Object.GetType%2A?displayProperty=nameWithType> metodu.

### <a name="type-testing-with-the-typeof-operator"></a>Testování typu pomocí `typeof` operátoru

Použijte `typeof` operátor ke kontrole, zda typ modulu runtime výsledku výrazu přesně odpovídá danému typu. Následující příklad ukazuje rozdíl mezi kontrolou typu provedenými s `typeof` operátorem a [operátorem is](#is-operator):

[!code-csharp[typeof vs is](snippets/TypeTestingAndConversionOperators.cs#TypeCheckWithTypeOf)]

## <a name="operator-overloadability"></a>Přetížení operátoru

`is`Operátory, `as` a `typeof` nemohou být přetíženy.

Uživatelsky definovaný typ nemůže přetížit `()` operátor, ale může definovat vlastní převody typů, které mohou být provedeny výrazem přetypování. Další informace naleznete v tématu [uživatelsky definované operátory převodu](user-defined-conversion-operators.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Operátor is](~/_csharplang/spec/expressions.md#the-is-operator)
- [Operátor as](~/_csharplang/spec/expressions.md#the-as-operator)
- [Výrazy cast](~/_csharplang/spec/expressions.md#cast-expressions)
- [Operátor typeof](~/_csharplang/spec/expressions.md#the-typeof-operator)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Operátory a výrazy v C#](index.md)
- [Jak bezpečně přetypovat pomocí porovnávání vzorů a operátorů is a as](../../how-to/safely-cast-using-pattern-matching-is-and-as-operators.md)
- [Obecné typy v .NET](../../../standard/generics/index.md)
