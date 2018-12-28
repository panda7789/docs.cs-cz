---
title: ushort – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
ms.openlocfilehash: 934e25576a8a24c176a54ec6af984459b513fe5a
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/19/2018
ms.locfileid: "53614453"
---
# <a name="ushort-c-reference"></a>ushort (Referenční dokumentace jazyka C#)

`ushort` – Klíčové slovo určuje celočíselný datový typ, který uchovává hodnoty podle velikosti a oblasti, které jsou uvedeny v následující tabulce.

|Typ|Rozsah|Velikost|Typ formátu .NET|
|----------|-----------|----------|-------------------------|
|`ushort`|0 až 65 535|Celé číslo bez znaménka 16 bitů|<xref:System.UInt16?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Můžete deklarovat a inicializovat `ushort` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu. Pokud celočíselný literál je mimo rozsah `ushort` (tj. Pokud je menší než <xref:System.UInt16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 65,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](int.md) k `ushort` hodnoty.

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]

> [!NOTE]
> Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál. Desítkové literály mají žádná předpona.

Počínaje C# 7.0, několik funkce byly přidány za účelem zlepšení čitelnosti:

- C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.
- C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu. Desítkový literál není povoleno mít vedoucího podtržítka.

Níže je uvedeno několik příkladů.

[!code-csharp[UShort](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]

## <a name="compiler-overload-resolution"></a>Řešení přetížení kompilátoru

Přetypování musí být použito při volání přetížené metody. Zvažte například následující přetížené metody, které používají `ushort` a [int](int.md) parametry:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ushort s) {}
```

Použití `ushort` přetypování zaručuje, že správný typ název, například:

```csharp
// Calls the method with the int parameter:
SampleMethod(5);
// Calls the method with the ushort parameter:
SampleMethod((ushort)5);
```

## <a name="conversions"></a>Převody

Není předdefinovanou implicitní převod z `ushort` k [int](int.md), [uint](uint.md), [dlouhé](long.md), [ulong](ulong.md), [plovoucí desetinnou čárkou ](float.md), [double](double.md), nebo [desítkové](decimal.md).

Není předdefinovanou implicitní převod z [bajtů](byte.md) nebo [char](char.md) k `ushort`. V opačném případě musí být použito k provedení explicitního převodu přetypování. Zvažte například následující dva `ushort` proměnné `x` a `y`:

```csharp
ushort x = 5, y = 12;
```

Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako `int` ve výchozím nastavení.

```csharp
ushort z = x + y;   // Error: conversion from int to ushort
```

Pokud chcete tento problém vyřešit, použijte přetypování:

```csharp
ushort z = (ushort)(x + y);   // OK: explicit conversion
```

Je ale možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:

```csharp
int m = x + y;
long n = x + y;
```

Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `ushort`. Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:

```csharp
// Error -- no implicit conversion from double:
ushort x = 3.0;
// OK -- explicit conversion:
ushort y = (ushort)3.0;
```

Informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).

Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.UInt16>
- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Tabulka celočíselných typů](integral-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
