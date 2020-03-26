---
title: Výchozí hodnoty typů jazyka C# – odkaz jazyka C#
description: Naučte se výchozí hodnoty c# typy jako bool, char, int, float, double a další.
ms.date: 12/18/2019
helpviewer_keywords:
- default [C#]
- parameterless constructor [C#]
ms.openlocfilehash: 5e34d291ec15c738f3bc9409df321ede454b6710
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507253"
---
# <a name="default-values-of-c-types-c-reference"></a>Výchozí hodnoty typů jazyka C# (odkaz jazyka C#)

V následující tabulce jsou uvedeny výchozí hodnoty typů jazyka C#:

|Typ|Výchozí hodnota|
|---------|------------------|
|Jakýkoli typ odkazu|`null`|
|Jakýkoli [vestavěný integrální číselný typ](integral-numeric-types.md)|0 (nula)|
|Jakýkoli [vestavěný číselný typ s plovoucí desetinnou desetinnou desetinnou stoužek](floating-point-numeric-types.md)|0 (nula)|
|[bool](bool.md)|`false`|
|[char](char.md)|`'\0'`(U+0000)|
|[Výčtu](enum.md)|Hodnota vytvořená výrazem `(E)0` `E` , kde je identifikátor výčtu.|
|[Struct](struct.md)|Hodnota vytvořená nastavením všech polí typu hodnoty na jejich výchozí `null`hodnoty a všechna pole typu odkazu na .|
|Jakýkoli [typ hodnoty s možnou hodnotou null](nullable-value-types.md)|Instance, pro <xref:System.Nullable%601.HasValue%2A> kterou `false` je <xref:System.Nullable%601.Value%2A> vlastnost a vlastnost není definována. Tato výchozí hodnota je také známá jako *hodnota null* typu hodnoty s možnou hodnotou, kterou lze hodnotit.|

Pomocí [ `default` operátoru](../operators/default.md#default-operator) můžete vytvořit výchozí hodnotu typu, jak ukazuje následující příklad:

```csharp
int a = default(int);
```

Počínaje C# 7.1, můžete použít [ `default` literál](../operators/default.md#default-literal) k inicializaci proměnné s výchozí hodnotou jejího typu:

```csharp
int a = default;
```

Pro typ hodnoty implicitní konstruktor bez parametrů také vytvoří výchozí hodnotu typu, jak ukazuje následující příklad:

```csharp-interactive
var n = new System.Numerics.Complex();
Console.WriteLine(n);  // output: (0, 0)
```

Za běhu, pokud <xref:System.Type?displayProperty=nameWithType> instance představuje typ hodnoty, <xref:System.Activator.CreateInstance(System.Type)?displayProperty=nameWithType> můžete použít metodu k vyvolání konstruktoru bez parametrů k získání výchozí hodnoty typu.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících částech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Výchozí hodnoty](~/_csharplang/spec/variables.md#default-values)
- [Výchozí konstruktory](~/_csharplang/spec/types.md#default-constructors)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Konstruktory](../../programming-guide/classes-and-structs/constructors.md)
