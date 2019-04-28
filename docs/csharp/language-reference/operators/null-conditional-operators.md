---
title: Podmíněné operátory s Null - C# odkaz
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 9cbf8a0f860f0bc0328cd98e558b20b5e8e1bf8f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688875"
---
# <a name="-and--null-conditional-operators-c-reference"></a>?. a? [] podmíněné operátory s null (C# odkaz)

Testuje hodnotu levý operand pro hodnotu null, před provedením přístup ke členu (`?.`) nebo indexu (`?[]`) časový limit operace; vrátí `null` pokud levý operand je vyhodnocen jako `null`.

Tyto operátory usnadňuje psaní méně kód pro zpracování null kontrol, zejména pro sestupné řazení do datové struktury.

```csharp
int? length = customers?.Length; // null if customers is null
Customer first = customers?[0];  // null if customers is null
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null
```

Podmíněné operátory s null jsou short-circuiting.  Pokud jedna operace v řetězci Podmíněný člen přístup a index operace vrátí hodnotu null, zastaví se zbytek spuštění do řetězce.  V následujícím příkladu `E` neprovede, pokud `A`, `B`, nebo `C` vyhodnotí na hodnotu null.

```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

Další možností použití pro přístup ke členům podmíněných null je vyvoláním delegátů způsobem bezpečným pro vlákno s mnohem menším množstvím kódu.  Starý způsob vyžaduje kód podobný tomuto:

```csharp
var handler = this.PropertyChanged;
if (handler != null)
    handler(…);
```

Nový způsob je mnohem jednodušší:

```csharp
PropertyChanged?.Invoke(…)
```

Nový způsob je bezpečná pro vlákno, protože kompilátor generuje kód do vyhodnocení `PropertyChanged` pouze jednou, uchovávání výsledek v dočasné proměnné. Je třeba explicitně volat `Invoke` metoda vzhledem k tomu, že neexistuje žádná syntaxe vyvolání delegáta null podmíněných `PropertyChanged?(e)`.

## <a name="language-specifications"></a>Specifikace jazyka

Další informace najdete v tématu [Null podmíněného operátoru](~/_csharplang/spec/expressions.md#null-conditional-operator) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- [?? (operátoru nulového sjednocení)](null-coalescing-operator.md)
- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)