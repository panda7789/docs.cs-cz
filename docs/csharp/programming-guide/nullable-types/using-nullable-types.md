---
title: Použití typů s povolenou hodnotou Null – C# Průvodce programováním pro službu
ms.custom: seodec18
description: Zjistěte, jak pracovat s typy s možnou hodnotou Null C#
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: ef7c9c18d303131b5a1c0156be820e1d475e7ec1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61709936"
---
# <a name="using-nullable-types-c-programming-guide"></a>Použití typů s povolenou hodnotou Null (C# Programming Guide)

Typy s možnou hodnotou Null jsou typy, které představují všechny hodnoty základního typu hodnoty `T`a další [null](../../language-reference/keywords/null.md) hodnotu. Další informace najdete v tématu [typy připouštějící hodnotu Null](index.md) tématu.

Můžete odkazovat na typ připouštějící hodnotu Null v některém z následujících forem: `Nullable<T>` nebo `T?`. Tyto dvě formy jsou zaměnitelné.  
  
## <a name="declaration-and-assignment"></a>Deklaraci a přiřazení

Jako typ hodnoty lze implicitně převést na odpovídající typ s možnou hodnotou Null, přiřadíte hodnotu na typ připouštějící hodnotu null jako jeho základní typ hodnoty. Také můžete přiřadit `null` hodnotu.  Příklad:
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Zkoumání hodnotu typu s možnou hodnotou Null

Použijte následující vlastnosti jen pro čtení sloužící ke zkoumání instanci typu s možnou hodnotou Null pro hodnotu null a načíst hodnotu podkladového typu:  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Označuje, zda obsahuje instanci typu s možnou hodnotou Null hodnotu jeho nadřízeného typu.
  
- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> Získá hodnotu základního typu, pokud <xref:System.Nullable%601.HasValue%2A> je `true`. Pokud <xref:System.Nullable%601.HasValue%2A> je `false`, <xref:System.Nullable%601.Value%2A> vlastnost vyvolá <xref:System.InvalidOperationException>.
  
Kód v následujícím příkladu používá `HasValue` vlastnost k ověření, zda proměnná obsahuje hodnotu před zobrazením jej:
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
Typ s možnou hodnotou Null proměnné se taky můžete porovnat `null` namísto použití `HasValue` vlastnosti, jako v následujícím příkladu:  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

Od verze C# 7.0, můžete použít [porovnávání vzorů](../../pattern-matching.md) jak prozkoumat a získat hodnotu typu s možnou hodnotou NULL:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>Převod z typu s možnou hodnotou Null na základní typ.

Pokud je potřeba přiřadit typ připouštějící hodnotu Null hodnotu typu Null, použijte [operátoru nulového sjednocení `??` ](../../language-reference/operators/null-coalescing-operator.md) zadat hodnotu pro přiřazení, pokud je typ připouštějící hodnotu Null hodnota null (můžete také použít <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> metodu který):
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Použití <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metody, pokud hodnota má být použit při hodnota s možnou hodnotou Null typu má hodnotu null musí být výchozí hodnota základního typu hodnoty.
  
Můžete explicitně přetypován typ připouštějící hodnotu NULL do typu Null. Příklad:  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

V době běhu, pokud hodnota s možnou hodnotou Null typu má hodnotu null, vyvolá explicitní přetypování <xref:System.InvalidOperationException>.

Typ hodnotu null je implicitně převést na odpovídající typ s možnou hodnotou Null.
  
## <a name="operators"></a>Operátory

Předdefinované jednočlenné a binární operátory a operátory definované uživatelem, které existují pro typy hodnot může také sloužit typy s možnou hodnotou Null. Tyto operátory vytvořit hodnotu null, pokud jeden nebo oba operandy jsou null. v opačném případě operátor, který se používá omezením hodnoty k výpočtu výsledku. Příklad:  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]

> [!NOTE]
> Pro `bool?` zadejte předdefinované `&` a `|` operátory není postupujte z pravidel popsaných v této části: výsledek vyhodnocení operátor může být jiná než null, i v případě, že jeden z operandů má hodnotu null. Další informace najdete v tématu [logické operátory s povolenou hodnotou Null logická](../../language-reference/operators/boolean-logical-operators.md#nullable-boolean-logical-operators) část [logické logické operátory](../../language-reference/operators/boolean-logical-operators.md) článku.
  
Pro relační operátory (`<`, `>`, `<=`, `>=`), pokud jeden nebo oba operandy hodnotu null, je výsledkem `false`. Nepředpokládejte, protože konkrétní porovnání (například `<=`) vrátí `false`, opačný porovnání (`>`) vrátí `true`. Následující příklad ukazuje, že je 10

- ani větší než nebo rovna hodnotě null,
- ani nižší než null.
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
Výše uvedený příklad také ukazuje, že porovnání rovnosti dvou typů s povolenou hodnotou Null, které jsou obě hodnotu null je vyhodnocen jako `true`.

Další informace najdete v tématu [zrušeno vs. operátory](~/_csharplang/spec/expressions.md#lifted-operators) část [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).

## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení

Typ s možnou hodnotou null je [boxed](../types/boxing-and-unboxing.md) následujícími pravidly:

- Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `false`, je vytvořen nulový odkaz.  
- Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`, hodnota základního typu hodnoty `T` je zabalená, není instancí <xref:System.Nullable%601>.

Hodnotový typ, který má odpovídající typ s možnou hodnotou Null, může unbox jako v následujícím příkladu:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="see-also"></a>Viz také:

- [Typy s možnou hodnotou Null](index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Co přesně pojem "zrušeno" znamená?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
