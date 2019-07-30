---
title: Výchozí hodnoty tabulka – C# odkaz
ms.custom: seodec18
description: Zjistěte, jaké jsou výchozí hodnoty C# typů.
ms.date: 07/29/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 23fba8269670156000cb68b3aa07ae7c770eada1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68627738"
---
# <a name="default-values-table-c-reference"></a>Tabulka výchozích hodnot (C# Referenční dokumentace)

Následující tabulka ukazuje výchozí hodnoty C# typů:

|type|Výchozí hodnota|
|---------|------------------|
|Libovolný typ odkazu|`null`|
|Libovolný [vestavěný celočíselný numerický typ](../builtin-types/integral-numeric-types.md)|0 (nula)|
|Libovolný [vestavěný číselný typ s plovoucí desetinnou](../builtin-types/floating-point-numeric-types.md) čárkou|0 (nula)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'`(U + 0000)|
|[enum](enum.md)|Hodnota vytvořená výrazem `(E)0`, kde `E` je identifikátor výčtu.|
|[struct](struct.md)|Hodnota vytvořená nastavením všech polí typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkaz na `null`.|
|Libovolný [typ hodnoty s možnou hodnotou null](../../programming-guide/nullable-types/index.md)|Instance, pro kterou <xref:System.Nullable%601.HasValue%2A> je `false` vlastnost a <xref:System.Nullable%601.Value%2A> vlastnost není definována. Tato výchozí hodnota je také známá jako hodnota *null* typu hodnoty s možnou hodnotou null.|

Použijte [výchozí hodnotu Expression](../../programming-guide/statements-expressions-operators/default-value-expressions.md) pro vytvoření výchozí hodnoty typu, jak ukazuje následující příklad:

```csharp
int a = default(int);
```

Počínaje C# 7,1 můžete použít [ `default` literál](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) k inicializaci proměnné s výchozí hodnotou jeho typu:

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
