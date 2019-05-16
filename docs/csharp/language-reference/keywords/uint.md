---
title: uint – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- uint
- uint_CSharpKeyword
helpviewer_keywords:
- uint keyword [C#]
ms.openlocfilehash: 9a60460f67f9b6cf0b57d40ebf2789536e870d75
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633149"
---
# <a name="uint-c-reference"></a>uint (Referenční dokumentace jazyka C#)

`uint` – Klíčové slovo označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.

|Type|Rozsah|Velikost|Typ formátu .NET|
|----------|-----------|----------|-------------------------|
|`uint`|0 do 4 294 967 295|Nepodepsané 32bitové celé číslo|<xref:System.UInt32?displayProperty=nameWithType>|

**Poznámka:** `uint` typ není kompatibilní se Specifikací CLS. Použití `int` kdykoli je to možné.

## <a name="literals"></a>Literály

Můžete deklarovat a inicializovat `uint` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu. Pokud celočíselný literál je mimo rozsah `uint` (tj. Pokud je menší než <xref:System.UInt32.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 3,000,000,000, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `uint` hodnoty.

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UInt)]

> [!NOTE]
> Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál. Desítkové literály mají žádná předpona.

Počínaje C# 7.0, několik funkce byly přidány za účelem zlepšení čitelnosti:

- C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.
- C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu. Desítkový literál není povoleno mít vedoucího podtržítka.

Níže je uvedeno několik příkladů.

[!code-csharp[uint](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UIntS)]

Literály celých čísel může také obsahovat příponu, která označuje typ. Přípona `U` nebo "u" označuje buď `uint` nebo `ulong`, v závislosti na číselnou hodnotu literálu. V následujícím příkladu `u` příponu k označení celé číslo bez znaménka obou typů. Všimněte si, že je první literál `uint` vzhledem k tomu, že její hodnota je menší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>, zatímco druhá je `ulong` vzhledem k tomu, že její hodnota je větší než <xref:System.UInt32.MaxValue?displayProperty=nameWithType>.

[!code-csharp[usuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#1)]

Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:

1. [int](int.md)
2. `uint`
3. [long](long.md)
4. [ulong](ulong.md)

## <a name="conversions"></a>Převody

Není předdefinovanou implicitní převod z `uint` k [dlouhé](long.md), [ulong](ulong.md), [float](float.md), [double](double.md), nebo [ desetinné](decimal.md). Příklad:

```csharp
float myFloat = 4294967290;   // OK: implicit conversion to float
```

Není předdefinovanou implicitní převod z [bajtů](byte.md), [ushort](ushort.md), nebo [char](char.md) k `uint`. V opačném případě je nutné použít přetypování. Přiřazovací příkaz například způsobí chybu kompilace bez přetypování:

```csharp
long aLong = 22;
// Error -- no implicit conversion from long:
uint uInt1 = aLong;
// OK -- explicit conversion:
uint uInt2 = (uint)aLong;
```

Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `uint`. Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:

```csharp
// Error -- no implicit conversion from double:
uint x = 3.0;
// OK -- explicit conversion:
uint y = (uint)3.0;
```

Informace o aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).

Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.UInt32>
- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Tabulka celočíselných typů](integral-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
