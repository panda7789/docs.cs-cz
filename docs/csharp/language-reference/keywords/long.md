---
title: Long - C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: 997ce7399dc9742076932b213811abd1f847e60b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661216"
---
# <a name="long-c-reference"></a>long (Referenční dokumentace jazyka C#)

`long` označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.

|Type|Rozsah|Velikost|Typ formátu .NET|
|----------|-----------|----------|-------------------------|
|`long`|-9,223,372,036,854,775,808 k 9,223,372,036,854,775,807|64bitové celé číslo se znaménkem|<xref:System.Int64?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Můžete deklarovat a inicializovat `long` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.

V následujícím příkladu celých čísel rovnat do 4 294 967 296 jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `long` hodnoty.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]

> [!NOTE]
> Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál. Desítkové literály mají žádná předpona.

Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.
- C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.
- C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu. Desítkový literál není povoleno mít vedoucího podtržítka.

Níže je uvedeno několik příkladů.

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

Literály celých čísel může také obsahovat příponu, která označuje typ. Přípona `L` označuje `long`. V následujícím příkladu `L` příponu k označení dlouhé celé číslo:

```csharp
long value = 4294967296L;
```

> [!NOTE]
> Malé písmeno "l" můžete také použít jako příponu. Nicméně tím se vygeneruje upozornění kompilátoru protože písmeno "l" je snadno zaměnitelná s číslicí "1". Pro přehlednost použijte "L".

Pokud použijete tuto příponu `L`, vyhodnotí typu literál celého čísla buď `long` nebo [ulong](../../../csharp/language-reference/keywords/ulong.md), v závislosti na jeho velikost. V takovém případě je `long` vzhledem k tomu je méně než rozsah [ulong](../../../csharp/language-reference/keywords/ulong.md).

Běžné použití přípona je volání přetížené metody. Například následující přetížené metody mít parametry typu `long` a [int](../../../csharp/language-reference/keywords/int.md):

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(long l) {}
```

`L` Přípona zaručuje, že je volána správné přetížení:

```csharp
SampleMethod(5);    // Calls the method with the int parameter
SampleMethod(5L);   // Calls the method with the long parameter
```

Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md)

Typ je literál 4294967296 v předchozích příkladech `long`, protože překračuje rozsah [uint](../../../csharp/language-reference/keywords/uint.md) (naleznete v tématu [integrální typy tabulky](../../../csharp/language-reference/keywords/integral-types-table.md) pro velikosti úložiště celočíselných typů).

Pokud používáte `long` typ s jiné typy celých čísel ve stejném výrazu, výrazu je vyhodnoceno jako `long` (nebo [bool](../../../csharp/language-reference/keywords/bool.md) v případě relační nebo logické výrazy). Například následující výraz se vyhodnocuje jako `long`:

```csharp
898L + 88
```

Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](../../../csharp/language-reference/keywords/float.md) a [double](../../../csharp/language-reference/keywords/double.md).

## <a name="conversions"></a>Převody

Není předdefinovanou implicitní převod z `long` k [float](../../../csharp/language-reference/keywords/float.md), [double](../../../csharp/language-reference/keywords/double.md), nebo [desítkové](../../../csharp/language-reference/keywords/decimal.md). V opačném případě se musí použít přetypování. Například následující příkaz vytvoří chybu kompilace bez explicitního přetypování:

```csharp
int x = 8L;        // Error: no implicit conversion from long to int
int y = (int)8L;   // OK: explicit conversion to int
```

Není předdefinovanou implicitní převod z [sbyte](../../../csharp/language-reference/keywords/sbyte.md), [bajtů](../../../csharp/language-reference/keywords/byte.md), [krátký](../../../csharp/language-reference/keywords/short.md), [ushort](../../../csharp/language-reference/keywords/ushort.md), [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), nebo [char](../../../csharp/language-reference/keywords/char.md) k `long`.

Všimněte si také, že neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `long`. Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:

```csharp
long x = 3.0;         // Error: no implicit conversion from double
long y = (long)3.0;   // OK: explicit conversion
```

## <a name="c-language-specification"></a>Specifikace jazyka C#

Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.Int64>
- [Referenční dokumentace jazyka C#](../../../csharp/language-reference/index.md)
- [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)
- [Klíčová slova jazyka C#](../../../csharp/language-reference/keywords/index.md)
- [Tabulka celočíselných typů](../../../csharp/language-reference/keywords/integral-types-table.md)
- [Tabulka předdefinovaných typů](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [Tabulka implicitních číselných převodů](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
