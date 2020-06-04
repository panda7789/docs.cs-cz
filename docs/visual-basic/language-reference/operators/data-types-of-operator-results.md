---
title: Datové typy výsledků operátoru
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: b80508c5619770da0c7dc78003ff9d4847dd94d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371424"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Datové typy výsledků operátoru (Visual Basic)
Visual Basic Určuje datový typ výsledku operace na základě datových typů operandů. V některých případech to může být datový typ s větším rozsahem než u obou operandů.  
  
## <a name="data-type-ranges"></a>Rozsahy datového typu  
 Rozsahy relevantních datových typů, od nejmenších po největší, jsou následující:  
  
- [Boolean](../data-types/boolean-data-type.md) – dvě možné hodnoty  
  
- [SByte](../data-types/sbyte-data-type.md), [Byte](../data-types/byte-data-type.md) – 256 možných celočíselných hodnot  
  
- [Short](../data-types/short-data-type.md), [UShort](../data-types/ushort-data-type.md) – 65 536 (6,5... E + 4) možné celočíselné hodnoty  
  
- [Integer](../data-types/integer-data-type.md), [UInteger –](../data-types/uinteger-data-type.md) – 4 294 967 296 (4.2... E + 9) možné celočíselné hodnoty  
  
- [Long](../data-types/long-data-type.md), [ulong](../data-types/ulong-data-type.md) – 18446744073709551615 (1.8... E + 19) možné celočíselné hodnoty  
  
- [Decimal](../data-types/decimal-data-type.md) – 1,5... e + 29 možné celočíselné hodnoty, maximální rozsah 7.9... e + 28 (absolutní hodnota)  
  
- [Single](../data-types/single-data-type.md) – maximální rozsah 3.4... E + 38 (absolutní hodnota)  
  
- [Double](../data-types/double-data-type.md) – maximální rozsah 1.7... E + 308 (absolutní hodnota)  
  
 Další informace o Visual Basic datových typů najdete v tématu [datové typy](../data-types/index.md).  
  
 Pokud je operand vyhodnocen jako [Nothing](../nothing.md), Visual Basic aritmetické operátory jsou považovány za nulu.  
  
## <a name="decimal-arithmetic"></a>Desítkové aritmetické operace  
 Všimněte si, že datový typ [Decimal](../data-types/decimal-data-type.md) není plovoucí desetinná čárka ani celé číslo.  
  
 Pokud je jeden z operandů `+` , `–` ,, `*` `/` nebo `Mod` operace, `Decimal` a druhý není `Single` nebo `Double` , Visual Basic rozšiřuje druhý operand na `Decimal` . Provede operaci v `Decimal` a výsledný datový typ je `Decimal` .  
  
## <a name="floating-point-arithmetic"></a>Aritmetické operace s plovoucí desetinnou čárkou  
 Visual Basic provádí většinu aritmetických výpočtů s plovoucí desetinnou čárkou v [Double](../data-types/double-data-type.md), což je nejúčinnější datový typ pro tyto operace. Pokud je však jeden operand [jediný](../data-types/single-data-type.md) a druhý není `Double` , Visual Basic provede operaci v `Single` . Rozšiřuje každý operand tak, jak je to nutné pro příslušný datový typ před operací a výsledek má tento datový typ.  
  
### <a name="-and--operators"></a>Operátory/a ^  
 `/`Operátor je definován pouze pro datové typy [Decimal](../data-types/decimal-data-type.md), [Single](../data-types/single-data-type.md)a [Double](../data-types/double-data-type.md) . Visual Basic rozšiřuje každý operand tak, jak je to nutné pro příslušný datový typ před operací a výsledek má tento datový typ.  
  
 V následující tabulce jsou uvedeny typy dat výsledků pro `/` operátor. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Libovolný celočíselný typ|  
|`Decimal`|Desetinné číslo|Single|Double|Desetinné číslo|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Libovolný celočíselný typ|Desetinné číslo|Single|Double|Double|  
  
 `^`Operátor je definován pouze pro `Double` datový typ. Visual Basic rozšiřuje každý operand tak, jak je potřeba `Double` před operací, a výsledný datový typ je vždycky `Double` .  
  
## <a name="integer-arithmetic"></a>Aritmetický typ Integer  
 Výsledný datový typ celočíselné operace závisí na datových typech operandů. Obecně platí, že Visual Basic k určení typu výsledných dat používá následující zásady:  
  
- Pokud mají oba operandy binárního operátoru stejný datový typ, výsledek má tento datový typ. Výjimka je `Boolean` , což je vynuceno `Short` .  
  
- Pokud se operand bez znaménka účastní podepsaného operandu, má výsledek podepsaný typ s aspoň jako velký rozsah jako jeden operand.  
  
- V opačném případě má výsledek obvykle větší ze dvou datových typů operandů.  
  
 Všimněte si, že výsledný datový typ nemusí být stejný jako datový typ operandu.  
  
> [!NOTE]
> Výsledný datový typ není vždy dostatečně velký, aby mohl uchovávat všechny možné hodnoty, které jsou výsledkem operace. <xref:System.OverflowException>Výjimka může nastat, pokud je hodnota pro výsledný datový typ příliš velká.  
  
### <a name="unary--and--operators"></a>Unární operátory + a –  
 V následující tabulce jsou uvedeny typy dat výsledků pro dva unární operátory `+` a `–` .  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unární`+`|Dostatečná|SByte|Byte|Dostatečná|UShort|Integer|UInteger –|Dlouhou|ULong|  
|Unární`–`|Dostatečná|SByte|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Desetinné číslo|  
  
### <a name="-and--operators"></a><\< and >> operátory  
 V následující tabulce jsou uvedeny typy dat výsledků pro dva operátory bitového posunutí `<<` a `>>` . Visual Basic zpracovává každý operátor bitového posunutí jako unární operátor na levém operandu (Bitová maska, která se má posunout).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Dostatečná|SByte|Byte|Dostatečná|UShort|Integer|UInteger –|Dlouhou|ULong|  
  
 Pokud je levý operand `Decimal` , `Single` , `Double` nebo `String` , Visual Basic se pokusí ho převést na `Long` před operací a výsledný datový typ je `Long` . Pravý operand (počet bitových pozic k posunu) musí být `Integer` nebo typ, který se rozšíří na `Integer` .  
  
### <a name="binary----and-mod-operators"></a>Operátory Binary +, –, \* a mod  
 V následující tabulce jsou uvedeny typy dat výsledků pro binární `+` a `–` operátory a `*` `Mod` operátory a. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Dostatečná|SByte|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Desetinné číslo|  
|`SByte`|SByte|SByte|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Desetinné číslo|  
|`Byte`|Dostatečná|Dostatečná|Byte|Dostatečná|UShort|Integer|UInteger –|Dlouhou|ULong|  
|`Short`|Dostatečná|Dostatečná|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Desetinné číslo|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhou|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhou|Dlouhou|Desetinné číslo|  
|`UInteger`|Dlouhou|Dlouhou|UInteger –|Dlouhou|UInteger –|Dlouhou|UInteger –|Dlouhou|ULong|  
|`Long`|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Desetinné číslo|  
|`ULong`|Desetinné číslo|Desetinné číslo|ULong|Desetinné číslo|ULong|Desetinné číslo|ULong|Desetinné číslo|ULong|  
  
### <a name="-operator"></a>\\ – operátor  
 V následující tabulce jsou uvedeny typy dat výsledků pro `\` operátor. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Dostatečná|SByte|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Dlouhou|  
|`SByte`|SByte|SByte|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Dlouhou|  
|`Byte`|Dostatečná|Dostatečná|Byte|Dostatečná|UShort|Integer|UInteger –|Dlouhou|ULong|  
|`Short`|Dostatečná|Dostatečná|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Dlouhou|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhou|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhou|Dlouhou|Dlouhou|  
|`UInteger`|Dlouhou|Dlouhou|UInteger –|Dlouhou|UInteger –|Dlouhou|UInteger –|Dlouhou|ULong|  
|`Long`|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|  
|`ULong`|Dlouhou|Dlouhou|ULong|Dlouhou|ULong|Dlouhou|ULong|Dlouhou|ULong|  
  
 Pokud je jeden operand `\` operátoru [Decimal](../data-types/decimal-data-type.md), [Single](../data-types/single-data-type.md)nebo [Double](../data-types/double-data-type.md), Visual Basic se pokusí ho převést na [dlouhou dobu](../data-types/long-data-type.md) před operací a výsledný datový typ je `Long` .  
  
## <a name="relational-and-bitwise-comparisons"></a>Relační a bitové porovnání  
 Datový typ výsledku relační operace ( `=` , `<>` ,, `<` `>` , `<=` , `>=` ) je vždy `Boolean` [logický datový typ](../data-types/boolean-data-type.md). Totéž platí pro logické operace ( `And` , `AndAlso` , `Not` , `Or` , `OrElse` , `Xor` ) na `Boolean` operandech.  
  
 Výsledný datový typ bitové logické operace závisí na datových typech operandů. Všimněte si, že `AndAlso` a `OrElse` jsou definovány pouze pro `Boolean` a Visual Basic `Boolean` před provedením operace převede každý operand podle potřeby.  
  
### <a name="-----and--operators"></a>=,  <>, \<, > , \<=, and > = – operátory  
 Jsou-li oba operandy `Boolean` , Visual Basic považuje `True` být menší než `False` . Pokud číselný typ je porovnán s `String` , Visual Basic se pokusí převést na `String` na `Double` před operací. `Char`Operand nebo `Date` lze porovnat pouze s jiným operandem stejného datového typu. Výsledný datový typ je vždycky `Boolean` .  
  
### <a name="bitwise-not-operator"></a>Bitový operátor NOT  
 V následující tabulce jsou uvedeny typy dat výsledků pro bitový `Not` operátor.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Logická hodnota|SByte|Byte|Dostatečná|UShort|Integer|UInteger –|Dlouhou|ULong|  
  
 Pokud je operand `Decimal` , `Single` , `Double` , nebo `String` , Visual Basic se pokusí ho převést na `Long` před operací a výsledný datový typ je `Long` .  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bitové operátory and, or a XOR  
 V následující tabulce jsou uvedeny typy dat výsledků pro bitové `And` operátory, `Or` a `Xor` . Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Logická hodnota|SByte|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Dlouhou|  
|`SByte`|SByte|SByte|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Dlouhou|  
|`Byte`|Dostatečná|Dostatečná|Byte|Dostatečná|UShort|Integer|UInteger –|Dlouhou|ULong|  
|`Short`|Dostatečná|Dostatečná|Dostatečná|Dostatečná|Integer|Integer|Dlouhou|Dlouhou|Dlouhou|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhou|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhou|Dlouhou|Dlouhou|  
|`UInteger`|Dlouhou|Dlouhou|UInteger –|Dlouhou|UInteger –|Dlouhou|UInteger –|Dlouhou|ULong|  
|`Long`|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|Dlouhou|  
|`ULong`|Dlouhou|Dlouhou|ULong|Dlouhou|ULong|Dlouhou|ULong|Dlouhou|ULong|  
  
 Pokud je operand `Decimal` , `Single` , `Double` , nebo `String` , Visual Basic se pokusí ho převést na `Long` před operací a výsledný datový typ je stejný, jako by tento operand již byl `Long` .  
  
## <a name="miscellaneous-operators"></a>Různé operátory  
 `&`Operátor je definován pouze pro zřetězení `String` operandů. Visual Basic každou hodnotu operandu `String` před operací převede tak, jak je potřeba, a výsledný datový typ je vždycky `String` . Pro účely `&` operátoru jsou všechny převody na `String` jsou považovány za rozšiřující, a to i v případě, že `Option Strict` je `On` .  
  
 `Is`Operátory a `IsNot` vyžadují, aby oba operandy byly typu odkazu. `TypeOf`Výraz... `Is` vyžaduje, aby první operand byl typu odkazu a druhý operand byl názvem datového typu. Ve všech těchto případech je výsledný datový typ `Boolean` .  
  
 `Like`Operátor je definován pouze pro porovnávání vzorů `String` operandů. Visual Basic se pokusí převést každý operand podle potřeby `String` před operací. Výsledný datový typ je vždycky `Boolean` .  
  
## <a name="see-also"></a>Viz také

- [Datové typy](../data-types/index.md)
- [Operátory a výrazy](../../programming-guide/language-features/operators-and-expressions/index.md)
- [Aritmetické operátory v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnání v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátory](index.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Operátory porovnání](comparison-operators.md)
- [Option Strict – příkaz](../statements/option-strict-statement.md)
