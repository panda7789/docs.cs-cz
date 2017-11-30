---
title: "Tabulka výchozích hodnot (referenční dokumentace jazyka C#)"
descripton: Learn what are the default values of value types returned by the default constructors.
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.assetid: 4af2c1df-9e3a-48c1-83ac-b192986fc5bc
caps.latest.revision: "12"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7f692ee1242af88dc6bd3938f7a00f3d11ed8ca7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-values-table-c-reference"></a>Tabulka výchozích hodnot (referenční dokumentace jazyka C#)
V následující tabulce jsou uvedeny výchozí hodnoty typů hodnot vrácených výchozí konstruktory. Výchozí konstruktory jsou vyvolány pomocí `new` operátor následujícím způsobem:

```csharp
int myInt = new int();
```

Předchozí příkaz má stejný účinek jako následující příkaz:

```csharp
int myInt = 0;
```

Mějte na paměti, že není povolené použití neinicializovaného proměnných v jazyce C#.

|Typ hodnoty|Výchozí hodnota|
|----------------|-------------------|
|[BOOL](../../../csharp/language-reference/keywords/bool.md)|`false`|
|[bajtů](../../../csharp/language-reference/keywords/byte.md)|0|
|[Char](../../../csharp/language-reference/keywords/char.md)|'\0'|
|[Decimal](../../../csharp/language-reference/keywords/decimal.md)|0,0 M|
|[Double](../../../csharp/language-reference/keywords/double.md)|0,0 D|
|[výčet](../../../csharp/language-reference/keywords/enum.md)|Hodnota vyprodukované výraz (E) 0, kde E je identifikátor výčtu.|
|[plovoucí desetinná čárka](../../../csharp/language-reference/keywords/float.md)|0,0 F|
|[celá čísla](../../../csharp/language-reference/keywords/int.md)|0|
|[dlouhá](../../../csharp/language-reference/keywords/long.md)|0L|
|[SByte –](../../../csharp/language-reference/keywords/sbyte.md)|0|
|[krátký](../../../csharp/language-reference/keywords/short.md)|0|
|[Struktura](../../../csharp/language-reference/keywords/struct.md)|Hodnota vytvořeného nastavením všechna pole typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkazu na `null`.|
|[uint](../../../csharp/language-reference/keywords/uint.md)|0|
|[ulong –](../../../csharp/language-reference/keywords/ulong.md)|0|
|[ushort –](../../../csharp/language-reference/keywords/ushort.md)|0|

## <a name="see-also"></a>Viz také
 [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Tabulka typů hodnot](../../../csharp/language-reference/keywords/value-types-table.md)  
 [Typy hodnot](../../../csharp/language-reference/keywords/value-types.md)  
 [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [Referenční tabulky pro typy](../../../csharp/language-reference/keywords/reference-tables-for-types.md)
