---
title: Výchozí hodnoty tabulka – C# odkaz
ms.custom: seodec18
description: Zjistěte, jaké jsou výchozí hodnoty C# typů.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 02f86ef8ee73ff31a6c5c9d17a44a443f72ef05e
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739278"
---
# <a name="default-values-table-c-reference"></a>Tabulka výchozích hodnot (C# Referenční dokumentace)

Následující tabulka ukazuje výchozí hodnoty C# typů:

|Typ|Výchozí hodnota|
|---------|------------------|
|Libovolný typ odkazu|`null`|
|Libovolný [vestavěný celočíselný numerický typ](../builtin-types/integral-numeric-types.md)|0 (nula)|
|Libovolný [vestavěný číselný typ s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou|0 (nula)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'` (U + 0000)|
|[enum](enum.md)|Hodnota vytvořená výrazem `(E)0`, kde `E` je identifikátor výčtu.|
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

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Výchozí hodnoty](~/_csharplang/spec/variables.md#default-values)
- [Výchozí konstruktory](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Klíčová slova jazyka C#](index.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
