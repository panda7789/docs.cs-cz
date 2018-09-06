---
title: Tabulka výchozích hodnot (referenční dokumentace jazyka C#)
description: Zjistěte, jaké jsou výchozí hodnoty jazyka C# hodnotové typy.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- default constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], default constructor
- types [C#], default constructor return values
ms.openlocfilehash: 184a9f42ddd3654a81aef0b7ce35e404de2d4bb9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43737980"
---
# <a name="default-values-table-c-reference"></a>Tabulka výchozích hodnot (referenční dokumentace jazyka C#)

V následující tabulce jsou uvedeny výchozí hodnoty [typů hodnot](value-types.md).

|Typ hodnoty|Výchozí hodnota|
|----------------|-------------------|
|[bool](bool.md)|`false`|
|[byte](byte.md)|0|
|[char](char.md)|'\0'|
|[decimal](decimal.md)|0M|
|[double](double.md)|0.0 D|
|[enum](enum.md)|Hodnota vytvořený podle výrazu `(E)0`, kde `E` je identifikátor výčtu.|
|[float](float.md)|0,0 F|
|[int](int.md)|0|
|[long](long.md)|0L|
|[sbyte](sbyte.md)|0|
|[short](short.md)|0|
|[struct](struct.md)|Hodnota vytvořen nastavením všechna pole typu hodnoty na jejich výchozí hodnoty a všechna pole typu odkazu k `null`.|
|[uint](uint.md)|0|
|[ulong](ulong.md)|0|
|[ushort](ushort.md)|0|

## <a name="remarks"></a>Poznámky

Neinicializované proměnné nelze použít v jazyce C#. Můžete inicializovat proměnné s výchozí hodnotou jeho typu. Také vám pomůže výchozí hodnota typu zadat výchozí hodnotu z metody [nepovinný argument](../../programming-guide/classes-and-structs/named-and-optional-arguments.md#optional-arguments).

Použití [výchozí hodnota výrazu](../../programming-guide/statements-expressions-operators/default-value-expressions.md) vytvoří výchozí hodnota typu, jako v následujícím příkladu:

```csharp
int a = default(int);
```

Od verze C# 7.1, můžete použít [ `default` literálu](../../programming-guide/statements-expressions-operators/default-value-expressions.md#default-literal-and-type-inference) inicializace proměnné s výchozí hodnotou typu:

```csharp
int a = default;
```

Jak ukazuje následující příklad vytvoří výchozí hodnota typu hodnoty, můžete použít také výchozí konstruktor nebo implicitní výchozí konstruktor. Další informace o konstruktorech naleznete v tématu [konstruktory](../../programming-guide/classes-and-structs/constructors.md) článku.

```csharp
int a = new int();
```

Zadejte výchozí hodnotu kterékoli [odkazovat na typ](reference-types.md) je `null`. Výchozí hodnota [typ připouštějící hodnotu Null](../../programming-guide/nullable-types/index.md) u kterého je instance <xref:System.Nullable%601.HasValue%2A> vlastnost `false` a <xref:System.Nullable%601.Value%2A> vlastnost není definována.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Referenční tabulky pro typy](reference-tables-for-types.md)
- [Typy hodnot](value-types.md)
- [Tabulka typů hodnot](value-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
