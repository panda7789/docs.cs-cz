---
title: Tabulka výchozích hodnot - C# odkaz
ms.custom: seodec18
description: Zjistěte, jaké jsou výchozí hodnoty jazyka C# hodnotové typy.
ms.date: 08/23/2018
helpviewer_keywords:
- constructors [C#], return values
- keywords [C#], new
- parameterless constructor [C#]
- defaults [C#]
- value types [C#], initializing
- variables [C#], value types
- constructors [C#], parameterless constructor
- types [C#], parameterless constructor return values
ms.openlocfilehash: 4fc9a35f69540e047a97c21788015ca8e54068a0
ms.sourcegitcommit: 10986410e59ff29f2ec55c6759bde3eb4d1a00cb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/31/2019
ms.locfileid: "66422028"
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

Jak ukazuje následující příklad vytvoří výchozí hodnota typu hodnoty, můžete použít také konstruktor bez parametrů nebo implicitní konstruktor bez parametrů. Další informace o konstruktorech naleznete v tématu [konstruktory](../../programming-guide/classes-and-structs/constructors.md) článku.

```csharp
int a = new int();
```

Zadejte výchozí hodnotu kterékoli [odkazovat na typ](reference-types.md) je `null`. Výchozí hodnota [typ připouštějící hodnotu Null](../../programming-guide/nullable-types/index.md) u kterého je instance <xref:System.Nullable%601.HasValue%2A> vlastnost `false` a <xref:System.Nullable%601.Value%2A> vlastnost není definována.

## <a name="see-also"></a>Viz také:

- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Typy hodnot](value-types.md)
- [Tabulka typů hodnot](value-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
