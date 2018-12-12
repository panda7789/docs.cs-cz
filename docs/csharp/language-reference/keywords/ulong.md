---
title: ulong – klíčové slovo - C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- ulong_CSharpKeyword
- ulong
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
ms.openlocfilehash: 97db22612e900658746f40cd117ff941135027a1
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235017"
---
# <a name="ulong-c-reference"></a>ulong (Referenční dokumentace jazyka C#)

`ulong` – Klíčové slovo označuje integrální typ, který uchovává hodnoty podle toho, velikost a rozsah je znázorněno v následující tabulce.

|Typ|Rozsah|Velikost|Typ formátu .NET|
|----------|-----------|----------|-------------------------|
|`ulong`|0 na 18,446,744,073,709,551,615|64-bit znaménka.|<xref:System.UInt64?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Můžete deklarovat a inicializovat `ulong` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.  Pokud celočíselný literál je mimo rozsah `ulong` (tj. Pokud je menší než <xref:System.UInt64.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.UInt64.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 7,934,076,125, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou přiřazeny k `ulong` hodnoty.

[!code-csharp[ulong](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]

> [!NOTE]
> Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál. Desítkové literály mají žádná předpona.

Počínaje C# 7.0, několik funkce byly přidány za účelem zlepšení čitelnosti:

- C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.
- C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu. Desítkový literál není povoleno mít vedoucího podtržítka.

Níže je uvedeno několik příkladů.

[!code-csharp[long](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]

Literály celých čísel může také obsahovat příponu, která označuje typ. Přípona `UL` nebo `ul` jednoznačně identifikuje jako číselný literál `ulong` hodnotu. `L` Označuje příponu `ulong` pokud překročí hodnotu literálu <xref:System.Int64.MaxValue?displayProperty=nameWithType>. A `U` nebo `u` označuje příponu `ulong` pokud překročí hodnotu literálu <xref:System.UInt32.MaxValue?displayProperty=nameWithType>. V následujícím příkladu `ul` příponu k označení dlouhé celé číslo:

[!code-csharp[ulsuffix](~/samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

Pokud celočíselného literálu bez přípony, jeho typ je první z těchto typů, ve kterých může být reprezentována jeho hodnotu:

1. [int](int.md)
2. [uint](uint.md)
3. [long](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a>Řešení přetížení kompilátoru

Je běžné použití přípony s voláním přetížené metody. Zvažte například následující přetížené metody, které používají `ulong` a [int](int.md) parametry:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(ulong l) {}
```

Pomocí přípony s `ulong` parametr zaručuje, že správný typ název, například:

```csharp
SampleMethod(5);    // Calling the method with the int parameter
SampleMethod(5UL);  // Calling the method with the ulong parameter
```

## <a name="conversions"></a>Převody

Není předdefinovanou implicitní převod z `ulong` k [float](float.md), [double](double.md), nebo [desítkové](decimal.md).

Neexistuje žádný implicitní převod z `ulong` na libovolný integrální typ. Například následující příkaz vytvoří chybu kompilace bez explicitního přetypování:

```csharp
long long1 = 8UL;   // Error: no implicit conversion from ulong
```

Není předdefinovanou implicitní převod z [bajtů](byte.md), [ushort](ushort.md), [uint](uint.md), nebo [char](char.md) k `ulong`.

Také, neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `ulong`. Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:

```csharp
// Error -- no implicit conversion from double:
ulong x = 3.0;
// OK -- explicit conversion:
ulong y = (ulong)3.0;
```

Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).

Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.UInt64>
- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Tabulka celočíselných typů](integral-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
