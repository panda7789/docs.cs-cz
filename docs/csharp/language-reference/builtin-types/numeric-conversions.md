---
description: 'Přečtěte si o implicitních a explicitních převodech mezi vestavěnými číselnými typy v jazyce C. #'
title: Předdefinované číselné převody – reference jazyka C#
ms.date: 10/22/2019
helpviewer_keywords:
- implicit numeric conversions [C#]
- explicit numeric conversion [C#]
- numeric conversions [C#], implicit
- numeric conversions [C#], explicit
- conversions [C#], implicit numeric
- conversions [C#], explicit numeric
ms.openlocfilehash: ee5def3b5e0e067919a8c8335db701dbb6dd4d88
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89142242"
---
# <a name="built-in-numeric-conversions-c-reference"></a>Předdefinované číselné převody (Referenční dokumentace jazyka C#)

Jazyk C# poskytuje sadu číselných typů [integrálních](integral-numeric-types.md) a [plovoucích bodů](floating-point-numeric-types.md) . Existuje převod mezi dvěma číselnými typy, buď implicitně, nebo explicitní. K provedení explicitního převodu je nutné použít [výraz přetypování](../operators/type-testing-and-cast.md#cast-expression) .

## <a name="implicit-numeric-conversions"></a>Implicitní číselné převody

V následující tabulce jsou uvedeny předdefinované implicitní převody mezi vestavěnými číselnými typy:

|Z|Záměr|
|----------|--------|
|[SByte](integral-numeric-types.md)|`short`, `int` , `long` , `float` , `double` nebo `decimal`|
|[bytové](integral-numeric-types.md)|`short`, `ushort` , `int` , `uint` , `long` , `ulong` , `float` , `double` nebo `decimal`|
|[short](integral-numeric-types.md)|`int`, `long` , `float` , `double` nebo `decimal`|
|[ushort](integral-numeric-types.md)|`int`, `uint` , `long` , `ulong` , `float` , `double` nebo `decimal`|
|[int](integral-numeric-types.md)|`long`, `float` , `double` nebo `decimal`|
|[uint](integral-numeric-types.md)|`long`, `ulong` , `float` , `double` nebo `decimal`|
|[long](integral-numeric-types.md)|`float`, `double` nebo `decimal`|
|[ulong](integral-numeric-types.md)|`float`, `double` nebo `decimal`|
|[float](floating-point-numeric-types.md)|`double`|

> [!NOTE]
> Implicitní převody z `int` , `uint` , `long` nebo `ulong` na `float` a z `long` nebo `ulong` na `double` mohou způsobit ztrátu přesnosti, ale nikdy nezpůsobí ztrátu velikosti. Ostatní implicitní číselné převody nikdy neztratí žádné informace.

Všimněte si také, že

- Libovolný [celočíselný numerický typ](integral-numeric-types.md) je implicitně převoditelný na libovolný [číselný typ s plovoucí](floating-point-numeric-types.md)desetinnou čárkou.

- Neexistují žádné implicitní převody na `byte` typy a `sbyte` . Neexistují žádné implicitní převody z `double` typů a `decimal` .

- Mezi `decimal` typem a typy nebo nejsou žádné implicitní převody `float` `double` .

- Hodnota konstantního výrazu typu `int` (například hodnota reprezentovaná celočíselným literálem) může být implicitně převedena na `sbyte` , `byte` , `short` , `ushort` , `uint` nebo `ulong` , pokud je v rozsahu cílového typu:

  ```csharp
  byte a = 13;
  byte b = 300;  // CS0031: Constant value '300' cannot be converted to a 'byte'
  ```

  Jak ukazuje předchozí příklad, pokud hodnota konstanty není v rozsahu cílového typu, dojde k chybě kompilátoru [CS0031](../../misc/cs0031.md) .

## <a name="explicit-numeric-conversions"></a>Explicitní číselné převody

V následující tabulce jsou uvedeny předdefinované explicitní převody mezi vestavěnými číselnými typy, pro které neexistuje [implicitní převod](#implicit-numeric-conversions):

|Z|Záměr|
|----------|--------|
|[SByte](integral-numeric-types.md)|`byte`, `ushort` , `uint` nebo `ulong`|
|[bytové](integral-numeric-types.md)|`sbyte`|
|[short](integral-numeric-types.md)|`sbyte`, `byte` , `ushort` , `uint` nebo `ulong`|
|[ushort](integral-numeric-types.md)|`sbyte`, `byte` nebo `short`|
|[int](integral-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `uint` nebo `ulong`|
|[uint](integral-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` nebo `int`|
|[long](integral-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` nebo `ulong`|
|[ulong](integral-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` nebo `long`|
|[float](floating-point-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` nebo `decimal`|
|[double](floating-point-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `float` nebo `decimal`|
|[decimal](floating-point-numeric-types.md)|`sbyte`, `byte` , `short` , `ushort` , `int` , `uint` , `long` , `ulong` , `float` nebo `double`|

> [!NOTE]
> Explicitní číselný převod může způsobit ztrátu dat nebo vyvolat výjimku, obvykle <xref:System.OverflowException> .

Všimněte si také, že

- Pokud převedete hodnotu integrálního typu na jiný celočíselný typ, výsledek závisí na [kontextu kontroly](../keywords/checked-and-unchecked.md)přetečení. V kontrolovaném kontextu je převod úspěšný, pokud je zdrojová hodnota v rozsahu cílového typu. V opačném případě <xref:System.OverflowException> je vyvolána výjimka. V nekontrolovaném kontextu je převod vždy úspěšný a pokračuje následujícím způsobem:

  - Pokud je typ zdroje větší než cílový typ, je zdrojová hodnota zkrácena tím, že zahodí "extra" nejvýznamnější bity. Výsledek je pak zpracován jako hodnota cílového typu.

  - Pokud je typ zdroje menší než cílový typ, pak je zdrojová hodnota buď znaménko, nebo nula-rozšířená, aby měla stejnou velikost jako cílový typ. Podpisové rozšíření se používá, pokud je typ zdroje podepsaný; Pokud je zdrojový typ bez znaménka, je použita nulová přípona. Výsledek je pak zpracován jako hodnota cílového typu.

  - Pokud má typ zdroje stejnou velikost jako cílový typ, pak je zdrojová hodnota zpracována jako hodnota cílového typu.

- Při převodu `decimal` hodnoty na celočíselný typ je tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud výsledná celočíselná hodnota je mimo rozsah cílového typu, <xref:System.OverflowException> je vyvolána výjimka.

- Při převodu `double` `float` hodnoty nebo na celočíselný typ je tato hodnota zaokrouhlena směrem k nule na nejbližší celočíselnou hodnotu. Pokud výsledná celočíselná hodnota je mimo rozsah cílového typu, výsledek závisí na [kontextu kontroly](../keywords/checked-and-unchecked.md)přetečení. V kontrolovaném kontextu <xref:System.OverflowException> je vyvolána výjimka, zatímco v nekontrolovaném kontextu je výsledek nespecifikovanou hodnotou cílového typu.

- Při převodu `double` na `float` se `double` hodnota zaokrouhluje na nejbližší `float` hodnotu. Pokud `double` je hodnota příliš malá nebo příliš velká, aby se vešla do `float` typu, výsledek je nula nebo nekonečno.

- Když převedete `float` nebo `double` na `decimal` , zdrojová hodnota se převede na `decimal` reprezentaci a v případě potřeby se zaokrouhluje na nejbližší číslo za 28 desetinným místem. V závislosti na hodnotě zdrojové hodnoty může dojít k jednomu z následujících výsledků:

  - Pokud je zdrojová hodnota příliš malá, aby byla reprezentována jako `decimal` , výsledkem bude nula.

  - Je-li zdrojová hodnota NaN (není číslo), nekonečno nebo příliš velká, aby byla reprezentována jako `decimal` , <xref:System.OverflowException> je vyvolána.

- Když převedete `decimal` na `float` nebo `double` , zdrojová hodnota se zaokrouhlí na nejbližší `float` nebo `double` hodnotu v uvedeném pořadí.

## <a name="c-language-specification"></a>specifikace jazyka C#

Další informace naleznete v následujících oddílech [specifikace jazyka C#](~/_csharplang/spec/introduction.md):

- [Implicitní číselné převody](~/_csharplang/spec/conversions.md#implicit-numeric-conversions)
- [Explicitní číselné převody](~/_csharplang/spec/conversions.md#explicit-numeric-conversions)

## <a name="see-also"></a>Viz také

- [Referenční dokumentace k jazyku C#](../index.md)
- [Přetypování a převody typů](../../programming-guide/types/casting-and-type-conversions.md)
