---
title: Použití typů s povolenou hodnotou Null (C# Programming Guide)
description: Zjistěte, jak pracovat s typy s možnou hodnotou Null C#
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: 8ef875aee8c40f60472df52c19d1c1f2c73e95e8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43515434"
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
  
Pro relační operátory (`<`, `>`, `<=`, `>=`), pokud jeden nebo oba operandy hodnotu null, je výsledkem `false`. Nepředpokládejte, protože konkrétní porovnání (například `<=`) vrátí `false`, opačný porovnání (`>`) vrátí `true`. Následující příklad ukazuje, že je 10

- ani větší než nebo rovna hodnotě null,
- ani nižší než null.
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
Výše uvedený příklad také ukazuje, že porovnání rovnosti dvou typů s povolenou hodnotou Null, které jsou obě hodnotu null je vyhodnocen jako `true`.

## <a name="boxing-and-unboxing"></a>Zabalení a rozbalení

Typ s možnou hodnotou null je [boxed](../types/boxing-and-unboxing.md) následujícími pravidly:

- Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `false`, je vytvořen nulový odkaz.  
- Pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`, hodnota základního typu hodnoty `T` je zabalená, není instancí <xref:System.Nullable%601>.

Hodnotový typ, který má odpovídající typ s možnou hodnotou Null, může unbox jako v následujícím příkladu:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="the-bool-type"></a>Logická hodnota? Typ

`bool?` Typ připouštějící hodnotu Null, může obsahovat tři různé hodnoty: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md) a [null](../../language-reference/keywords/null.md). `bool?` Typ je jako logická typ proměnné, který se používá v SQL. Chcete-li zajistit výsledky vytvořené metodou `&` a `|` operátory jsou konzistentní s typem Boolean s hodnotou tři v SQL, jsou k dispozici následující předdefinované operátory:

- `bool? operator &(bool? x, bool? y)`  
- `bool? operator |(bool? x, bool? y)`  
  
Sémantika těchto operátorů je definována v následující tabulce:  
  
|x|y|x & y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  

Všimněte si, že tyto dva operátory neodpovídají pravidel popsaných v [operátory](#operators) oddílu: výsledek vyhodnocení operátor může být jiná než null, i v případě, že jeden z operandů má hodnotu null.
  
## <a name="see-also"></a>Viz také

- [Typy s možnou hodnotou Null](index.md)  
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
- [Co přesně pojem "zrušeno" znamená?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)  
