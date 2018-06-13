---
title: Tabulka výchozích hodnot (referenční dokumentace jazyka C#)
description: Zjistěte, jaké jsou výchozí hodnoty typů hodnot vrácených výchozí konstruktory.
ms.date: 07/20/2015
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 634a55304534b4269487f29be1fbb4930f51d8ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33218787"
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
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0,0 D|
|[enum](enum.md)|Hodnota vyprodukované výraz (E) 0, kde E je identifikátor výčtu.|
|[float](float.md)|0,0 F|
|[int](int.md)|0|
|[long](long.md)|0L|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|Hodnota vytvořeného nastavením všechna pole typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkazu na `null`.|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="see-also"></a>Viz také
 [Referenční dokumentace jazyka C#](../index.md)  
 [Průvodce programováním v jazyce C#](../../programming-guide/index.md)  
 [Tabulka typů hodnot](value-types-table.md)  
 [Typy hodnot](value-types.md)  
 [Tabulka předdefinovaných typů](built-in-types-table.md)  
 [Referenční tabulky pro typy](reference-tables-for-types.md)
