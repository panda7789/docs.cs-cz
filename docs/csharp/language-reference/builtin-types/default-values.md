---
title: Výchozí hodnoty C# typů – C# referenční informace
description: Seznamte se s výchozími hodnotami C# typů, jako jsou bool, char, int, float, Double a more.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 2447db25e837cdcd6d67847b8677d7d44da551a9
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/15/2020
ms.locfileid: "75964942"
---
# <a name="default-values-of-c-types-c-reference"></a>Výchozí hodnoty C# typů (C# Referenční dokumentace)

Následující tabulka ukazuje výchozí hodnoty C# typů:

|Type|Výchozí hodnota|
|---------|------------------|
|Libovolný typ odkazu|`null`|
|Libovolný [vestavěný celočíselný numerický typ](integral-numeric-types.md)|0 (nula)|
|Libovolný [vestavěný číselný typ s plovoucí desetinnou](floating-point-numeric-types.md) čárkou|0 (nula)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U + 0000)|
|[enum](enum.md)|Hodnota vytvořená výrazem `(E)0`, kde `E` je identifikátor výčtu.|
|[struct](../keywords/struct.md)|Hodnota vytvořená nastavením všech polí typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkaz na `null`.|
|Libovolný [typ hodnoty s možnou hodnotou null](nullable-value-types.md)|Instance, pro kterou je vlastnost <xref:System.Nullable%601.HasValue%2A> `false` a vlastnost <xref:System.Nullable%601.Value%2A> není definována. Tato výchozí hodnota je také známá jako hodnota *null* typu hodnoty s možnou hodnotou null.|

Použijte [výchozí operátor](../operators/default.md) k vytvoření výchozí hodnoty typu, jak ukazuje následující příklad:

```csharp
int a = default(int);
```

Počínaje C# 7,1 můžete použít [literál`default`](../operators/default.md#default-literal) k inicializaci proměnné s výchozí hodnotou svého typu:

```csharp
int a = default;
```

Pro typ hodnoty, implicitní konstruktor bez parametrů vytvoří také výchozí hodnotu typu, jak ukazuje následující příklad:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

V době běhu, pokud <xref:System.Type?displayProperty=nameWithType> instance představuje typ hodnoty, lze použít metodu <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> k vyvolání konstruktoru bez parametrů k získání výchozí hodnoty typu.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Výchozí hodnoty](~/_csharplang/spec/variables.md#default-values)
- [Výchozí konstruktory](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
