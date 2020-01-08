---
title: Výchozí hodnoty tabulka – C# odkaz
ms.custom: seodec18
description: Zjistěte, jaké jsou výchozí hodnoty C# typů.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 3604316b75bb3a6a4de39991899a837f64e547d2
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345490"
---
# <a name="default-values-table-c-reference"></a>Tabulka výchozích hodnot (C# Referenční dokumentace)

Následující tabulka ukazuje výchozí hodnoty C# typů:

|Type|Výchozí hodnota|
|---------|------------------|
|Libovolný typ odkazu|`null`|
|Libovolný [vestavěný celočíselný numerický typ](../builtin-types/integral-numeric-types.md)|0 (nula)|
|Libovolný [vestavěný číselný typ s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou|0 (nula)|
|[bool](../builtin-types/bool.md)|`false`|
|[char](../builtin-types/char.md)|`'\0'` (U + 0000)|
|[enum](../builtin-types/enum.md)|Hodnota vytvořená výrazem `(E)0`, kde `E` je identifikátor výčtu.|
|[struct](struct.md)|Hodnota vytvořená nastavením všech polí typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkaz na `null`.|
|Libovolný [typ hodnoty s možnou hodnotou null](../builtin-types/nullable-value-types.md)|Instance, pro kterou je vlastnost <xref:System.Nullable%601.HasValue%2A> `false` a vlastnost <xref:System.Nullable%601.Value%2A> není definována. Tato výchozí hodnota je také známá jako hodnota *null* typu hodnoty s možnou hodnotou null.|

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
- [Klíčová slova jazyka C#](index.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
