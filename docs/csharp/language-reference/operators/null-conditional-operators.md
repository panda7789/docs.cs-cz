---
title: Podmíněné operátory s Null - C# odkaz
ms.custom: seodec18
ms.date: 04/03/2015
helpviewer_keywords:
- null-conditional operators [C#]
- ?. operator [C#]
- ?[] operator [C#]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: 38298cded904cbfedeaf3c6b66c74d610d714902
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333236"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a>?. a? [] podmíněné operátory s null (C# a Visual Basic)

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