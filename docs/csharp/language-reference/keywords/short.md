---
title: short – C# odkaz
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- short
- short_CSharpKeyword
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
ms.openlocfilehash: 0b02e72e0588f1c1a0343a391430b5878b96b5f5
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633995"
---
# <a name="short-c-reference"></a>short (Referenční dokumentace jazyka C#)

`short` označuje integrální datový typ, který uchovává hodnoty podle velikosti a oblasti, které jsou uvedeny v následující tabulce.

|Type|Rozsah|Velikost|Typ formátu .NET|
|----------|-----------|----------|-------------------------|
|`short`|-32 768 do 32 767|16bitové celé číslo se znaménkem|<xref:System.Int16?displayProperty=nameWithType>|

## <a name="literals"></a>Literály

Můžete deklarovat a inicializovat `short` proměnné přiřazením literál desítkové, hexadecimální literál, nebo (od verze C# 7.0) binární literál k němu.  Pokud celočíselný literál je mimo rozsah `short` (tj. Pokud je menší než <xref:System.Int16.MinValue?displayProperty=nameWithType> nebo větší než <xref:System.Int16.MaxValue?displayProperty=nameWithType>), dojde k chybě kompilace.

V následujícím příkladu celých čísel je rovno 1,034, které jsou reprezentovány jako desítkové, hexadecimální, a binární literály jsou implicitně převeden z [int](int.md) k `short` hodnoty.

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]

> [!NOTE]
> Použijte předponu `0x` nebo `0X` k označení šestnáctkové literal a předponu `0b` nebo `0B` k označení binární literál. Desítkové literály mají žádná předpona.

Od verze C# 7.0, přidali několik funkcí za účelem zlepšení čitelnosti.

- C# 7.0 umožňuje použití znaku podtržítka `_`, jako oddělovač číslic.
- C# 7.2 umožňuje `_` má být použit jako oddělovač číslici šestnáctkové nebo binární literál po předponu. Desítkový literál není povoleno mít vedoucího podtržítka.

Níže je uvedeno několik příkladů.

[!code-csharp[Short](~/samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]

## <a name="compiler-overload-resolution"></a>Řešení přetížení kompilátoru

Přetypování musí být použito při volání přetížené metody. Zvažte například následující přetížené metody, které používají `short` a [int](int.md) parametry:

```csharp
public static void SampleMethod(int i) {}
public static void SampleMethod(short s) {}
```

Použití `short` přetypování zaručuje, že správný typ název, například:

```csharp
SampleMethod(5);         // Calling the method with the int parameter
SampleMethod((short)5);  // Calling the method with the short parameter
```

## <a name="conversions"></a>Převody

Není předdefinovanou implicitní převod z `short` k [int](int.md), [dlouhé](long.md), [float](float.md), [double](double.md), nebo [ desetinné](decimal.md).

Nelze implicitně převést neliterální číselné typy větší velikosti úložiště `short` (naleznete v tématu [integrální typy tabulky](integral-types-table.md) pro velikosti úložiště celočíselných typů). Zvažte například následující dva `short` proměnné `x` a `y`:

```csharp
short x = 5, y = 12;
```

Přiřazovací příkaz způsobí chybu kompilace, protože aritmetický výraz na pravé straně operátoru přiřazení vyhodnotí jako [int](int.md) ve výchozím nastavení.

```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

Pokud chcete tento problém vyřešit, použijte přetypování:

```csharp
short z  = (short)(x + y);   // Explicit conversion
```

Je také možné použít následující příkazy, kde Cílová proměnná se stejnou velikostí úložiště nebo větší velikost úložiště:

```csharp
int m = x + y;
long n = x + y;
```

Neexistuje žádný implicitní převod z typů s plovoucí desetinnou čárkou `short`. Například následující příkaz vygeneruje chybu kompilátoru, pokud používá explicitní přetypování:

```csharp
short x = 3.0;          // Error: no implicit conversion from double
short y = (short)3.0;   // OK: explicit conversion
```

Informace v aritmetických výrazech s smíšené typy s plovoucí desetinnou čárkou a celočíselných typů naleznete v tématu [float](float.md) a [double](double.md).

Další informace o pravidlech implicitní převod čísla, najdete v článku [Implicit Numeric Conversions Table](implicit-numeric-conversions-table.md).

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v tématu [integrální typy](~/_csharplang/spec/types.md#integral-types) v [ C# specifikace jazyka](../language-specification/index.md). Specifikace jazyka je úplným a rozhodujícím zdrojem pro syntaxi a použití jazyka C#.

## <a name="see-also"></a>Viz také:

- <xref:System.Int16>
- [Referenční dokumentace jazyka C#](../index.md)
- [Průvodce programováním v jazyce C#](../../programming-guide/index.md)
- [Klíčová slova jazyka C#](index.md)
- [Tabulka celočíselných typů](integral-types-table.md)
- [Tabulka předdefinovaných typů](built-in-types-table.md)
- [Tabulka implicitních číselných převodů](implicit-numeric-conversions-table.md)
- [Tabulka explicitních číselných převodů](explicit-numeric-conversions-table.md)
