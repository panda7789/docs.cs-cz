---
title: Použití typů hodnot s možnou hodnotou null – C# Průvodce programováním
ms.custom: seodec18
description: Naučte se pracovat s C# typy hodnot s možnou hodnotou null.
ms.date: 09/26/2019
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 65fc3b0ca94f9a41c9375e96000449b52cb7db26
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396172"
---
# <a name="using-nullable-value-types-c-programming-guide"></a>Použití typů hodnot s možnou hodnotou null (C# Průvodce programováním)

Typy s možnou hodnotou null jsou typy, které představují všechny hodnoty základního typu hodnoty `T` a další hodnotu [null](../../language-reference/keywords/null.md) . Další informace naleznete v tématu [typy hodnot s možnou hodnotou null](index.md) .

> [!NOTE]
> C#8,0 zavádí funkci typů odkazů s možnou hodnotou null. Další informace naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md). Typy s C# možnou hodnotou null jsou k dispozici od 2.

Můžete odkazovat na typ hodnoty s možnou hodnotou null v některém z následujících formulářů, které lze měnit: `Nullable<T>` nebo `T?`. `T` musí být typ hodnoty.

## <a name="declaration-and-assignment"></a>Deklarace a přiřazení

Typ hodnoty lze implicitně převést na odpovídající typ hodnoty s možnou hodnotou null. přiřadíte hodnotu typu s možnou hodnotou null, jako byste to měli pro svůj základní typ hodnoty. Můžete také přiřadit hodnotu `null`. Příklad:

[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Prověření hodnoty typu s možnou hodnotou null

Pomocí následujících vlastností ReadOnly prověřte instanci typu hodnoty s možnou hodnotou null a načtěte hodnotu základního typu:

- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> označuje, zda instance typu s možnou hodnotou null má hodnotu svého nadřízeného typu.

- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> Získá hodnotu základního typu, pokud je <xref:System.Nullable%601.HasValue%2A> `true`. Pokud je <xref:System.Nullable%601.HasValue%2A> `false`, vlastnost <xref:System.Nullable%601.Value%2A> vyvolá <xref:System.InvalidOperationException>.

Kód v následujícím příkladu používá vlastnost `HasValue` k otestování, zda proměnná obsahuje hodnotu před jejich zobrazením:

[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]

Můžete také porovnat proměnnou typu hodnoty s možnou hodnotou null s `null` namísto použití vlastnosti `HasValue`, jak ukazuje následující příklad:

[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

Počínaje C# 7,0 můžete použít [porovnávání vzorů](../../pattern-matching.md) pro kontrolu a získání hodnoty typu s možnou hodnotou null:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-value-type-to-an-underlying-type"></a>Převod z typu hodnoty s možnou hodnotou null na nadřízený typ

Pokud potřebujete přiřadit hodnotu typu hodnoty s možnou hodnotou null k typu, který neumožňuje hodnotu null, použijte [operátor sloučení s hodnotou null `??`](../../language-reference/operators/null-coalescing-operator.md) k určení hodnoty, která má být přiřazena, pokud hodnota typu s možnou hodnotou null má hodnotu null (můžete také použít metodu <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> k tomu). :

[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Použijte metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType>, pokud je hodnota, která se má použít, pokud je hodnota typu s možnou hodnotou null `null` výchozí hodnotou základního typu hodnoty.

Typ hodnoty s možnou hodnotou null můžete explicitně přetypovat na typ, který není null. Příklad:

[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

V době běhu, pokud je hodnota typu s možnou hodnotou null `null`, explicitní přetypování vyvolá <xref:System.InvalidOperationException>.

Typ hodnoty, která není null, je implicitně převeden na odpovídající typ s možnou hodnotou null.

## <a name="operators"></a>Operátory

Předdefinované unární a binární operátory a jakékoli uživatelsky definované operátory, které existují pro typy hodnot, mohou být použity také odpovídajícími typy s možnou hodnotou null. Tyto operátory vytváří `null`, pokud jsou jeden nebo oba operandy `null`; v opačném případě operátor používá k výpočtu výsledku obsažené hodnoty. Příklad:

[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> U typu `bool?` se předdefinované operátory `&` a `|` nepoužijí pravidla popsaná v této části: výsledek vyhodnocení operátoru nemůže být null, i když je jeden z operandů `null`. Další informace naleznete v části s [možnou hodnotou null logických operátorů](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) v článku [Boolean Logical Operators](../../language-reference/operators/boolean-logical-operators.md) .
  
V případě relačních operátorů (`<`, `>`, `<=`, `>=`) platí, že pokud je jeden nebo oba operandy `null`, výsledek je `false`. Nepředpokládáme, že vzhledem k tomu, že konkrétní porovnání (například `<=`) vrátí `false`, opačné porovnání (`>`) vrátí `true`. Následující příklad ukazuje, že 10

- ani větší než nebo rovno `null`,
- ani menší než `null`.

[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]

Výše uvedený příklad také ukazuje, že porovnání rovnosti dvou typů hodnot s možnou hodnotou null, které jsou obě hodnoty null, jsou vyhodnoceny jako `true`.

Další informace naleznete v části předané [operátory](~/_csharplang/spec/expressions.md#lifted-operators) v tématu [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení

Typ hodnoty s možnou hodnotou null je [zabalený](../types/boxing-and-unboxing.md) podle následujících pravidel:

- Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `false`, bude vytvořen odkaz s hodnotou null.
- Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`, hodnota základního typu hodnoty `T` je zabalena, nikoli instance <xref:System.Nullable%601>.

Můžete unbox typ zabalené hodnoty na odpovídající typ s povolenou hodnotou null, jak ukazuje následující příklad:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Viz také:

- [Typy hodnot s možnou hodnotou null](index.md)
- [Co přesně znamená "vyvoláno"?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
