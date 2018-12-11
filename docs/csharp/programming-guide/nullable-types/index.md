---
title: Typy s možnou hodnotou Null – C# Průvodce programováním pro službu
ms.custom: seodec18
description: Další informace o typech s povolenou hodnotou Null C# a jak se dají použít
ms.date: 07/30/2018
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: cd5ac40ca73f7c528a903d5863f3cf5880738f11
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245120"
---
# <a name="nullable-types-c-programming-guide"></a>Typy s možnou hodnotou Null (C# Programming Guide)

Typy s možnou hodnotou Null jsou instance <xref:System.Nullable%601?displayProperty=nameWithType> struktury. Typy připouštějící hodnotu Null, může představovat všechny hodnoty ze základního typu `T`a další [null](../../language-reference/keywords/null.md) hodnotu. Základní typ `T` může být libovolný neumožňující [typ hodnoty](../../language-reference/keywords/value-types.md). `T` nemůže být typ odkazu.

Například můžete přiřadit `null` nebo libovolnou celočíselnou hodnotu od <xref:System.Int32.MinValue?displayProperty=nameWithType> k <xref:System.Int32.MaxValue?displayProperty=nameWithType> k `Nullable<int>` a [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), nebo `null` k `Nullable<bool>`.

Použijete typ připouštějící hodnotu Null, když budete potřebovat k reprezentaci nedefinovaná hodnota základního typu. Proměnné typu Boolean může mít jenom dvě hodnoty: true a false. Neexistuje žádná hodnota "undefined". V mnoha programování aplikací zejména interakce databáze, hodnotu proměnné lze nedefinované nebo chybí. Například pole v databázi může obsahovat hodnoty true nebo false, nebo může obsahovat vůbec žádnou hodnotu. Můžete použít `Nullable<bool>` v takovém případě zadejte.

Typy připouštějící hodnotu Null, mají následující vlastnosti:
  
- Typy s možnou hodnotou Null představují proměnné typu hodnoty, které je možné přiřadit `null` hodnotu. Nelze vytvořit typ připouštějící hodnotu Null na základě typu odkazu. (Referenční typy již podporují `null` hodnota.)  
  
- Syntaxe `T?` představuje zkratku pro `Nullable<T>`. Dvě různými formami jsou zaměnitelné.  
  
- Přiřadí hodnotu typu s možnou hodnotou Null, stejně jako základní typ hodnoty: `int? x = 10;` nebo `double? d = 4.108;`. Také můžete přiřadit `null` hodnota: `int? x = null;`.  
  
- Použití <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> a <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> vlastnosti jen pro čtení pro testování pro hodnotu null a načtení hodnoty, jak je znázorněno v následujícím příkladu: `if (x.HasValue) y = x.Value;`  
  
  - <xref:System.Nullable%601.HasValue%2A> Vrátí vlastnost `true` Pokud proměnná obsahuje hodnotu, nebo `false` jde `null`.
  
  - <xref:System.Nullable%601.Value%2A> Vlastnost vrací hodnotu, pokud <xref:System.Nullable%601.HasValue%2A> vrátí `true`. V opačném případě <xref:System.InvalidOperationException> je vyvolána výjimka.  
  
- Můžete také použít `==` a `!=` operátory s povolenou hodnotou Null typu, jak je znázorněno v následujícím příkladu: `if (x != null) y = x.Value;`. Pokud `a` a `b` mají obě hodnotu null, `a == b` vyhodnotí jako `true`.  

- Od verze C# 7.0, můžete použít [porovnávání vzorů](../../pattern-matching.md#the-is-type-pattern-expression) jak prozkoumat a získat hodnotu typu s možnou hodnotou NULL: `if (x is int valueOfX) y = valueOfX;`.
  
- Výchozí hodnota `T?` je instance jehož <xref:System.Nullable%601.HasValue%2A> vrátí vlastnost `false`.  

- Použití <xref:System.Nullable%601.GetValueOrDefault> metoda vrátí buď přiřazenou hodnotu, nebo [výchozí](../../language-reference/keywords/default-values-table.md) hodnota základního typu hodnoty, pokud je hodnota typu s možnou hodnotou Null `null`.  

- Použití <xref:System.Nullable%601.GetValueOrDefault(%600)> metoda vrací hodnotu přiřazenou nebo zadaná výchozí hodnota, pokud je hodnota typu s možnou hodnotou Null `null`.
  
- Použití [operátoru nulového sjednocení](../../language-reference/operators/null-coalescing-operator.md), `??`, chcete-li přiřadit hodnotu nadřazeného typu na základě hodnoty typu s možnou hodnotou NULL: `int? x = null; int y = x ?? -1;`. V příkladu protože `x` je null, hodnota výsledku `y` je `-1`.

- Pokud je definována uživatelem definovaný převod mezi dvěma datovými typy, stejný převod lze také s verzemi tyto datové typy s možnou hodnotou Null.
  
- Vnořené typy s možnou hodnotou Null nejsou povoleny. Následující řádek nebude kompilace: `Nullable<Nullable<int>> n;`  

Další informace najdete v tématu [použití typů s povolenou hodnotou Null](using-nullable-types.md) a [jak: Identifikace typu s možnou hodnotou Null](how-to-identify-a-nullable-type.md) témata.
  
## <a name="see-also"></a>Viz také

- <xref:System.Nullable%601?displayProperty=nameWithType>  
- <xref:System.Nullable?displayProperty=nameWithType>  
- [?? – operátor](../../language-reference/operators/null-coalescing-operator.md)  
- [Průvodce programováním v jazyce C#](../index.md)  
- [Průvodce jazykem C#](../../index.md)  
- [Referenční dokumentace jazyka C#](../../language-reference/index.md)  
- [Typy s možnou hodnotou Null (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
