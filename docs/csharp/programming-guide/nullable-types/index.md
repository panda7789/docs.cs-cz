---
title: Typy hodnot s možnou hodnotou null – C# Průvodce programováním
ms.custom: seodec18
description: Další informace C# o typech hodnot s možnou hodnotou null a jejich použití
ms.date: 09/26/2019
helpviewer_keywords:
- nullable value types [C#]
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: b8b52e7fb34adf65d5c76d59811ea6dd0ab16a98
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/27/2019
ms.locfileid: "71396216"
---
# <a name="nullable-value-types-c-programming-guide"></a>Typy hodnot s možnou hodnotou null (C# Průvodce programováním)

Typy s možnou hodnotou null jsou instance struktury <xref:System.Nullable%601?displayProperty=nameWithType>. Typy hodnot s možnou hodnotou null mohou představovat všechny hodnoty základního typu `T` a další hodnotu [null](../../language-reference/keywords/null.md) . Podkladový typ `T` může být jakýkoli [typ hodnoty](../../language-reference/keywords/value-types.md), která není null. `T` nemůže být odkazový typ.

> [!NOTE]
> C#8,0 zavádí funkci typů odkazů s možnou hodnotou null. Další informace naleznete v tématu [typy odkazů s možnou hodnotou null](../../nullable-references.md). Typy s C# možnou hodnotou null jsou k dispozici od 2.

Můžete například přiřadit `null` nebo libovolné celočíselné hodnoty z <xref:System.Int32.MinValue?displayProperty=nameWithType> @no__t do `Nullable<int>` a [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md)nebo `null` do `Nullable<bool>`.

Použijete typ hodnoty s možnou hodnotou null, pokud potřebujete reprezentovat nedefinovanou hodnotu základního typu. Logická proměnná může mít pouze dvě hodnoty: `true` a `false`. Není k dispozici žádná Nedefinovaná hodnota. V mnoha programovacích aplikacích, zejména interakci s databází, může být hodnota proměnné nedefinovaná nebo chybí. Například pole v databázi může obsahovat hodnoty true nebo false, případně nesmí vůbec obsahovat žádnou hodnotu. V takovém případě použijete typ `Nullable<bool>`.

Typy s možnou hodnotou null mají následující vlastnosti:

- Typy s možnou hodnotou null reprezentují proměnné hodnotového typu, které mohou mít přiřazenou hodnotu `null`.

- Syntaxe `T?` je zkrácený pro `Nullable<T>`. Tyto dva formuláře jsou zaměnitelné.

- Přiřaďte hodnotu typu hodnoty s možnou hodnotou null stejně jako u základního typu hodnoty: `int? x = 10;` nebo `double? d = 4.108;`. Můžete také přiřadit hodnotu `null`: `int? x = null;`.

- Použijte vlastnosti <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> a <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> jen pro čtení k otestování hodnoty null a načtení hodnoty, jak je znázorněno v následujícím příkladu: `if (x.HasValue) y = x.Value;`

  - Vlastnost <xref:System.Nullable%601.HasValue%2A> vrátí `true`, pokud proměnná obsahuje hodnotu, nebo `false`, pokud je `null`.

  - Vlastnost <xref:System.Nullable%601.Value%2A> vrací hodnotu, pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`. V opačném případě je vyvolána <xref:System.InvalidOperationException>.

- Můžete také použít operátory `==` a `!=` s typem hodnoty s možnou hodnotou null, jak je znázorněno v následujícím příkladu: `if (x != null) y = x.Value;`. Pokud `a` a `b` jsou obě hodnoty null, `a == b` se vyhodnotí jako `true`.

- Počínaje C# 7,0 můžete použít [porovnávání vzorů](../../pattern-matching.md#the-is-type-pattern-expression) pro kontrolu a získání hodnoty typu s možnou hodnotou null: `if (x is int valueOfX) y = valueOfX;`.

- Výchozí hodnota `T?` je instance, jejíž vlastnost <xref:System.Nullable%601.HasValue%2A> vrátí `false`.

- Použijte metodu <xref:System.Nullable%601.GetValueOrDefault> a vraťte buď přiřazenou hodnotu, nebo [výchozí](../../language-reference/keywords/default-values-table.md) hodnotu základního typu hodnoty, pokud je hodnota typu Nullable `null`.

- Použijte metodu <xref:System.Nullable%601.GetValueOrDefault(%600)> a vraťte buď přiřazenou hodnotu, nebo zadanou výchozí hodnotu, pokud je hodnota typu s možnou hodnotou null `null`.

- Pomocí [operátoru nulového](../../language-reference/operators/null-coalescing-operator.md)sjednocení `??` můžete přiřadit hodnotu k proměnné základního typu hodnoty na základě hodnoty s možnou hodnotou null: `int? x = null; int y = x ?? -1;`. V příkladu, protože `x` je `null`, je výsledkem hodnota `y` `-1`.

- Pokud je uživatelsky definovaný převod definován mezi dvěma typy hodnot, stejný převod lze také použít s odpovídajícími typy s možnou hodnotou null.

- Vnořené typy hodnot s možnou hodnotou null nejsou povoleny. Následující řádek není zkompilován: `Nullable<Nullable<int>> n;`

Další informace naleznete v tématu [použití typů hodnot s možnou hodnotou null](using-nullable-types.md) a [Postupy: určení typů hodnot s možnou hodnotou null](how-to-identify-a-nullable-type.md) .

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
- [?? – operátor](../../language-reference/operators/null-coalescing-operator.md)
- [Typy hodnot s možnou hodnotou null (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- <xref:System.Nullable%601?displayProperty=nameWithType>
- <xref:System.Nullable?displayProperty=nameWithType>
