---
title: Použití typů s možnou hodnotou null – C# Průvodce programováním
ms.custom: seodec18
description: Naučte se pracovat s C# typy s možnou hodnotou null.
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 75b8889f5f1f1b0dab4aa365daa34ef5ae226b02
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588830"
---
# <a name="using-nullable-types-c-programming-guide"></a>Použití typů s možnou hodnotou null (C# Průvodce programováním)

Typy s možnou hodnotou null jsou typy, které představují všechny hodnoty základního `T`typu hodnoty, a další hodnotu [null](../../language-reference/keywords/null.md) . Další informace najdete v tématu [typy s možnou hodnotou null](index.md) .

Na typ s možnou hodnotou null můžete odkazovat v některé z následujících forem `Nullable<T>` : `T?`nebo. Tyto dva formuláře jsou zaměnitelné.  
  
## <a name="declaration-and-assignment"></a>Deklarace a přiřazení

Typ hodnoty lze implicitně převést na odpovídající typ s povolenou hodnotou null. přiřadíte hodnotu typu s možnou hodnotou null, jako byste to měli pro svůj základní typ hodnoty. Můžete také přiřadit `null` hodnotu.  Příklad:
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Prověření hodnoty typu s možnou hodnotou null

Pomocí následujících vlastností ReadOnly prověřte instanci typu s možnou hodnotou null a načtěte hodnotu základního typu:  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType>Určuje, zda instance typu s možnou hodnotou null má hodnotu svého nadřízeného typu.
  
- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType>Získá hodnotu základního typu, pokud <xref:System.Nullable%601.HasValue%2A> je. `true` Pokud <xref:System.Nullable%601.HasValue%2A> je `false` ,<xref:System.Nullable%601.Value%2A>vlastnost vyvolá .<xref:System.InvalidOperationException>
  
Kód v následujícím příkladu používá `HasValue` vlastnost k otestování, zda proměnná obsahuje hodnotu před jejich zobrazením:
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
Můžete také porovnat proměnnou typu s možnou hodnotou `null` null s namísto `HasValue` použití vlastnosti, jak ukazuje následující příklad:  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

Počínaje C# 7,0 můžete použít [porovnávání vzorů](../../pattern-matching.md) pro kontrolu a získání hodnoty typu s možnou hodnotou null:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>Převod z typu s možnou hodnotou null na nadřízený typ

Pokud potřebujete přiřadit hodnotu typu s možnou hodnotou null k typu bez hodnoty null, použijte [operátor `??` ](../../language-reference/operators/null-coalescing-operator.md) pro sjednocení null k určení hodnoty, která má být přiřazena, pokud je hodnota typu s povolenou hodnotou null nulová ( <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> můžete také použít metodu k tomu):
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Použijte metodu <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> , pokud hodnota, která se má použít, když má hodnota typu Nullable hodnotu null, by měla být výchozí hodnotou základního typu hodnoty.
  
Typ s možnou hodnotou null můžete explicitně přetypovat na typ, který není null. Příklad:  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

V době běhu, pokud je hodnota typu s možnou hodnotou null null, vyvolá <xref:System.InvalidOperationException>explicitní přetypování.

Typ hodnoty, která není null, je implicitně převeden na odpovídající typ s možnou hodnotou null.
  
## <a name="operators"></a>Operátory

Předdefinované unární a binární operátory a jakékoli uživatelsky definované operátory, které existují pro typy hodnot, mohou být použity i pro typy s možnou hodnotou null. Tyto operátory vytvoří hodnotu null, pokud má jeden nebo oba operandy hodnotu null. v opačném případě operátor používá k výpočtu výsledku obsažené hodnoty. Příklad:  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> Pro typ se předdefinované `&` a `|` operátory nevztahují na pravidla popsaná v této části: výsledek vyhodnocení operátoru nemůže mít hodnotu null, i když jeden z operandů je null. `bool?` Další informace naleznete v části s [možnou hodnotou null](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) logických operátorů v článku [Boolean Logical Operators](../../language-reference/operators/boolean-logical-operators.md) .
  
V případě relačních operátorů `>`( `<=``<`, `>=`,,), pokud je jeden nebo oba operandy NULL, je `false`výsledek. Nepředpokládáme, že vzhledem k tomu, že konkrétní porovnání `<=`(například `false`) vrátí, vrátí `true`opačné porovnání (`>`). Následující příklad ukazuje, že 10

- ani větší nebo rovno hodnotě null,
- ani menší než null.
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
Výše uvedený příklad také ukazuje, že porovnání rovnosti dvou typů s možnou hodnotou null, na `true`které jsou obě hodnoty null, jsou vyhodnoceny.

Další informace naleznete v části předané [operátory](~/_csharplang/spec/expressions.md#lifted-operators) v tématu [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení

Typ hodnoty s možnou [](../types/boxing-and-unboxing.md) hodnotou null je zabalený podle následujících pravidel:

- Pokud <xref:System.Nullable%601.HasValue%2A> se `false`vrátí, je vytvořen odkaz s hodnotou null.  
- Pokud <xref:System.Nullable%601.HasValue%2A> se `true`vrátí, hodnota základního typu `T` hodnoty je zabalená, nikoli instance <xref:System.Nullable%601>.

Můžete unbox typ zabalené hodnoty na odpovídající typ s povolenou hodnotou null, jak ukazuje následující příklad:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Viz také:

- [Typy s možnou hodnotou null](index.md)
- [Průvodce programováním v jazyce C#](../index.md)
- [Co přesně znamená "vyvoláno"?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
