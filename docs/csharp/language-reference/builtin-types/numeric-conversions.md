---
title: Předdefinované číselné převody – C# referenční informace
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: 5380e8480c39d1940df13b2ecb50a0f394367388
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72776031"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Předdefinované číselné převody (C# Referenční dokumentace)

C#poskytuje sadu číselných typů [integrálních](integral-numeric-types.md) a [plovoucích bodů](floating-point-numeric-types.md) . Existuje převod mezi dvěma číselnými typy, buď implicitně, nebo explicitní. K vyvolání explicitního převodu je nutné použít [operátor přetypování `()`](../operators/type-testing-and-cast.md#cast-operator-) .

## <a name="implicit-numeric-conversions"></a>Implicitní číselné převody

V následující tabulce jsou uvedeny předdefinované implicitní převody mezi vestavěnými číselnými typy:

|From|Chcete-li|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`short`, `int`, `long`, `float`, `double` nebo `decimal`|
|[byte](integral-numeric-types.md)|`short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float`, `double` nebo `decimal`|
|[short](integral-numeric-types.md)|`int`, `long`, `float`, `double` nebo `decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint`, `long`, `ulong`, `float`, `double` nebo `decimal`|
|[int](integral-numeric-types.md)|`long`, `float`, `double` nebo `decimal`|
|[uint](integral-numeric-types.md)|`long`, `ulong`, `float`, `double` nebo `decimal`|
|[long](integral-numeric-types.md)|`float`, `double` nebo `decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double` nebo `decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> Implicitní převody z `int`, `uint`, `long` nebo `ulong` na `float` a z `long` nebo `ulong` na `double` mohou způsobit ztrátu přesnosti, ale nikdy nezpůsobí ztrátu velikosti. Ostatní implicitní číselné převody nikdy neztratí žádné informace.

Všimněte si také, že

- Libovolný [celočíselný numerický typ](integral-numeric-types.md) je implicitně převoditelný na libovolný [číselný typ s plovoucí](floating-point-numeric-types.md)desetinnou čárkou.

- Neexistují žádné implicitní převody na `byte` a `sbyte` typy. Neexistují žádné implicitní převody z `double` a `decimal` typů.

- Mezi typem `decimal` a typy `float` nebo `double` nejsou žádné implicitní převody.

- Hodnota konstantního výrazu typu `int` (například hodnota reprezentovaná celočíselným literálem) se dá implicitně převést na `sbyte`, `byte`, `short`, `ushort`, `uint` nebo `ulong`, pokud je v rozsahu cílového typu. :

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Jak ukazuje předchozí příklad, pokud hodnota konstanty není v rozsahu cílového typu, dojde k chybě kompilátoru [CS0031](../../misc/cs0031.md) .

## <a name="explicit-numeric-conversions"></a>Explicitní číselné převody

V následující tabulce jsou uvedeny předdefinované explicitní převody mezi vestavěnými číselnými typy, pro které neexistuje [implicitní převod](#implicit-numeric-conversions):

|From|Chcete-li|
|----------|--------|
|[sbyte](integral-numeric-types.md)|`byte`, `ushort`, `uint` nebo `ulong`|
|[byte](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte`, `ushort`, `uint` nebo `ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte` nebo `short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `uint` nebo `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort` nebo `int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` nebo `ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint` nebo `long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong` nebo `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float` nebo `decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `float` nebo `double`|

> [!NOTE]
> Explicitní číselný převod může způsobit ztrátu dat nebo vyvolat výjimku, obvykle <xref:System.OverflowException>.

Všimněte si také, že

- Pokud převedete hodnotu integrálního typu na jiný celočíselný typ, výsledek závisí na [kontextu kontroly](../keywords/checked-and-unchecked.md)přetečení. V kontrolovaném kontextu je převod úspěšný, pokud je zdrojová hodnota v rozsahu cílového typu. V opačném případě je vyvolána <xref:System.OverflowException>. V nekontrolovaném kontextu je převod vždy úspěšný a pokračuje následujícím způsobem:

  - Pokud je typ zdroje větší než cílový typ, je zdrojová hodnota zkrácena tím, že zahodí "extra" nejvýznamnější bity. Výsledek je pak zpracován jako hodnota cílového typu.

  - Pokud je typ zdroje menší než cílový typ, pak je zdrojová hodnota buď znaménko, nebo nula-rozšířená, aby měla stejnou velikost jako cílový typ. Podpisové rozšíření se používá, pokud je typ zdroje podepsaný; Pokud je zdrojový typ bez znaménka, je použita nulová přípona. Výsledek je pak zpracován jako hodnota cílového typu.

  - Pokud má typ zdroje stejnou velikost jako cílový typ, pak je zdrojová hodnota zpracována jako hodnota cílového typu.

- Při převodu `decimal` hodnoty na celočíselný typ je tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud výsledná celočíselná hodnota je mimo rozsah cílového typu, je vyvolána <xref:System.OverflowException>.

- Při převodu `double` nebo `float` hodnoty na celočíselný typ je tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud výsledná celočíselná hodnota je mimo rozsah cílového typu, výsledek závisí na [kontextu kontroly](../keywords/checked-and-unchecked.md)přetečení. V kontextu zaškrtnutí je vyvolána <xref:System.OverflowException>, zatímco v nekontrolovaném kontextu je výsledek nespecifikovanou hodnotou cílového typu.

- Když převedete `double` na `float`, hodnota `double` se zaokrouhlí na nejbližší `float` hodnotu. Pokud je hodnota `double` příliš malá nebo příliš velká, aby se vešla do `float` typu, výsledek je nula nebo nekonečno.

- Když převedete `float` nebo `double` na `decimal`, zdrojová hodnota se převede na `decimal` reprezentaci a v případě potřeby se zaokrouhluje na nejbližší číslo za 28 desetinným místem. V závislosti na hodnotě zdrojové hodnoty může dojít k jednomu z následujících výsledků:

  - Pokud je zdrojová hodnota příliš malá, aby byla reprezentována jako `decimal`, výsledkem bude nula.

  - Pokud je zdrojová hodnota NaN (není číslo), nekonečno nebo příliš velká, aby byla reprezentována jako `decimal`, je vyvolána <xref:System.OverflowException>.

- Když převedete `decimal` na `float` nebo `double`, zdrojová hodnota se zaokrouhlí na nejbližší `float` nebo `double` hodnotu v uvedeném pořadí.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace najdete v následujících oddílech [ C# specifikace jazyka](~/_csharplang/spec/introduction.md):

- [Implicitní číselné převody](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Explicitní číselné převody](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Viz také:

- [C#odkaz](../index.md)
- [Přetypování a převody typů](../../programming-guide/types/casting-and-type-conversions.md)
