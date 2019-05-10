---
title: Datové typy výsledků operátoru (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- data types [Visual Basic], operator result data types
- result data types [Visual Basic]
- operator result data types [Visual Basic]
- operators [Visual Basic], data types
- data types [Visual Basic], ranges
- operators [Visual Basic], result data types
ms.assetid: 9d524533-e1a1-4aa8-b1b8-622068173d06
ms.openlocfilehash: 1169a30f25db6084b8d232c0696991b040e7ea59
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662538"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Datové typy výsledků operátoru (Visual Basic)
Visual Basic určuje datový typ výsledku operace na základě typu dat z operandů. V některých případech to může být datový typ s větší rozsah než jeden z operandů.  
  
## <a name="data-type-ranges"></a>Rozsahy datového typu  
 Rozsahy typů relevantní data v pořadí od nejmenšího po největší, jsou následující:  
  
- [Logická](../../../visual-basic/language-reference/data-types/boolean-data-type.md) – dvě možné hodnoty  
  
- [SByte –](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md) – 256 možné celočíselné hodnoty  
  
- [Krátký](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) – 65 536 (6.5... E + 4) možné celočíselné hodnoty  
  
- [Celé číslo](../../../visual-basic/language-reference/data-types/integer-data-type.md), [uinteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) – 4 294 967 296 (4.2... E + 9) možné celočíselné hodnoty  
  
- [Dlouhé](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) – 18,446,744,073,709,551,615 (1.8... E + 19) možné celočíselné hodnoty  
  
- [Desetinné](../../../visual-basic/language-reference/data-types/decimal-data-type.md) – 1.5... E + 29 možné celočíselné hodnoty, maximální rozsah 7.9... E + 28 (absolutní hodnota)  
  
- [Jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) – maximální rozsah 3.4... E + 38 (absolutní hodnota)  
  
- [Dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md) – maximální rozsah 1.7... E + 308 (absolutní hodnota)  
  
 Další informace o jazyce Visual Basic datové typy naleznete v tématu [datové typy](../../../visual-basic/language-reference/data-types/index.md).  
  
 Pokud je operand vyhodnocen jako [nic](../../../visual-basic/language-reference/nothing.md), aritmetické operátory jazyka Visual Basic ji považovat za nulu.  
  
## <a name="decimal-arithmetic"></a>Desetinné aritmetické operace  
 Všimněte si, že [desítkové](../../../visual-basic/language-reference/data-types/decimal-data-type.md) datový typ není ani s plovoucí desetinnou čárkou ani celé číslo.  
  
 Pokud každý operand `+`, `–`, `*`, `/`, nebo `Mod` operace `Decimal` a druhá ne `Single` nebo `Double`, Visual Basic rozšiřuje je druhý operand `Decimal`. Provede operaci v `Decimal`, a datový typ výsledku je `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Aritmetické operace s plovoucí desetinnou čárkou  
 Visual Basic provádí většinu aritmetické operace s plovoucí desetinnou čárkou v [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), což je nejúčinnější datový typ pro tyto operace. Ale pokud jeden operand je [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) a druhá ne `Double`, Visual Basic provádí operaci v `Single`. Rozšiřuje operandem tak, aby odpovídající typ dat před provedením operace a výsledek je datového typu.  
  
### <a name="-and--operators"></a>/ a ^ operátory  
 `/` Operátor je určená jenom pro [desítkové](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md), a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) datové typy. Visual Basic rozšiřuje operandem tak, aby odpovídající typ dat před provedením operace a výsledek obsahuje tento typ data.  
  
 V následující tabulce jsou uvedeny výsledek datové typy pro `/` operátor. Všimněte si, že tato tabulka je symetrický; pro danou kombinaci operand datové typy datový typ výsledku je stejný bez ohledu na pořadí z operandů.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Jakýkoli typ celé číslo|  
|`Decimal`|Desetinné číslo|Single|Double|Desetinné číslo|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Jakýkoli typ celé číslo|Desetinné číslo|Single|Double|Double|  
  
 `^` Operátor je určená jenom pro `Double` datového typu. Visual Basic rozšiřuje operandem tak, aby `Double` před operace a výsledek datový typ je vždy `Double`.  
  
## <a name="integer-arithmetic"></a>Celočíselné aritmetiky  
 Datový typ výsledek celočíselné operace závisí na datové typy operandů. Obecně platí Visual Basic používá následující zásady pro stanovení výsledku datový typ:  
  
- Pokud mají oba operandy binárního operátoru stejný datový typ, výsledek je datového typu. Výjimkou je `Boolean`, který bude muset `Short`.  
  
- Je-li operand bez znaménka se účastní se znaménkem operandem, výsledek má typ se znaménkem s alespoň tak velké rozsah jako jeden z operandů.  
  
- V opačném případě výsledek obvykle má větší ze dvou typů dat operand.  
  
 Všimněte si, že datový typ výsledek nemusí být stejný jako buď datový typ operandu.  
  
> [!NOTE]
>  Datový typ výsledku vždy není dostatečně velký pro uložení všech možných hodnot plynoucí z operace. <xref:System.OverflowException> Výjimce může dojít, pokud hodnota je příliš velká pro datový typ výsledku.  
  
### <a name="unary--and--operators"></a>Unární + a – operátory  
 Následující tabulka ukazuje výsledek datové typy pro dva unární operátory, `+` a `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unární `+`|Krátké|SByte|Byte|Krátké|UShort|Integer|UInteger|Dlouhé|ULong|  
|Unární `–`|Krátké|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
  
### <a name="-and--operators"></a><\< a >> operátory  
 Následující tabulka ukazuje výsledek datových typů pro dvě bitové posunutí – operátory `<<` a `>>`. Visual Basic zpracovává každý bitové posunutí – operátor jako unární operátor na levý operand (bitový vzor posunutí).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|Krátké|SByte|Byte|Krátké|UShort|Integer|UInteger|Dlouhé|ULong|  
  
 Pokud levý operand `Decimal`, `Single`, `Double`, nebo `String`, Visual Basic se pokusí převést na `Long` před operace a výsledek je datový typ `Long`. Pravý operand (počet bitové pozice posunout) musí být `Integer` nebo typ, který rozšiřuje na `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Binární +, -, * a Mod operátory  
 V následující tabulce jsou uvedeny výsledek datové typy pro binární soubor `+` a `–` operátory a `*` a `Mod` operátory. Všimněte si, že tato tabulka je symetrický; pro danou kombinaci operand datové typy datový typ výsledku je stejný bez ohledu na pořadí z operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krátké|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
|`SByte`|SByte|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
|`Byte`|Krátké|Krátké|Byte|Krátké|UShort|Integer|UInteger|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Desetinné číslo|  
|`UInteger`|Dlouhé|Dlouhé|UInteger|Dlouhé|UInteger|Dlouhé|UInteger|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Desetinné číslo|  
|`ULong`|Desetinné číslo|Desetinné číslo|ULong|Desetinné číslo|ULong|Desetinné číslo|ULong|Desetinné číslo|ULong|  
  
### <a name="-operator"></a>\ – operátor  
 V následující tabulce jsou uvedeny výsledek datové typy pro `\` operátor. Všimněte si, že tato tabulka je symetrický; pro danou kombinaci operand datové typy datový typ výsledku je stejný bez ohledu na pořadí z operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krátké|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`SByte`|SByte|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`Byte`|Krátké|Krátké|Byte|Krátké|UShort|Integer|UInteger|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UInteger`|Dlouhé|Dlouhé|UInteger|Dlouhé|UInteger|Dlouhé|UInteger|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|  
|`ULong`|Dlouhé|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|  
  
 Pokud každý operand `\` operátor je [desítkové](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md), nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic se pokusí převést na [dlouho](../../../visual-basic/language-reference/data-types/long-data-type.md)před operace a výsledek je datový typ `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Relační a bitové porovnání  
 Datový typ výsledku operace, která relační (`=`, `<>`, `<`, `>`, `<=`, `>=`) je vždy `Boolean` [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Totéž platí pro logické operace (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) na `Boolean` operandy.  
  
 Datový typ výsledku bitové logické operace závisí na datové typy operandů. Všimněte si, že `AndAlso` a `OrElse` jsou určená jenom pro `Boolean`, a Visual Basic převede operandem tak, aby `Boolean` před provedením operace.  
  
### <a name="-----and--operators"></a>= <>, \<, >, \<= a > = operátory  
 Pokud jsou oba operandy `Boolean`, Visual Basic bere v úvahu `True` být menší než `False`. Pokud číselného typu se porovná se `String`, Visual Basic se pokusí převést `String` k `Double` před provedením operace. A `Char` nebo `Date` operand jde porovnat jenom s jiný operand stejného datového typu. Datový typ výsledku je vždy `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bitový operátor Not  
 V následující tabulce jsou uvedeny výsledek datové typy pro bitový `Not` operátor.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte –|Byte|Krátké|UShort|Integer|UInteger|Dlouhé|ULong|  
  
 Pokud je operand `Decimal`, `Single`, `Double`, nebo `String`, Visual Basic se pokusí převést na `Long` před operace a výsledek je datový typ `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bitový operátor a, nebo, operátory a operátory Xor  
 V následující tabulce jsou uvedeny výsledek datové typy pro bitový `And`, `Or`, a `Xor` operátory. Všimněte si, že tato tabulka je symetrický; pro danou kombinaci operand datové typy datový typ výsledku je stejný bez ohledu na pořadí z operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`SByte`|SByte|SByte|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`Byte`|Krátké|Krátké|Byte|Krátké|UShort|Integer|UInteger|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UInteger`|Dlouhé|Dlouhé|UInteger|Dlouhé|UInteger|Dlouhé|UInteger|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|  
|`ULong`|Dlouhé|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|  
  
 Pokud je operand `Decimal`, `Single`, `Double`, nebo `String`, Visual Basic se pokusí převést na `Long` před operaci a výsledná data typ je stejný jako kdyby byla již operandu `Long`.  
  
## <a name="miscellaneous-operators"></a>Různé operátory  
 `&` Operátor je určená jenom pro zřetězení `String` operandy. Visual Basic převede operandem tak, aby `String` před operace a výsledek datový typ je vždy `String`. Pro účely `&` operátora, všechny převody na `String` jsou považovány za rozšíření, i když `Option Strict` je `On`.  
  
 `Is` a `IsNot` operátory vyžadují oba operandy typu odkaz. `TypeOf`... `Is` výraz vyžaduje první operand typu odkaz a druhý operand, aby název datového typu. Ve všech těchto případech výsledných dat je typu `Boolean`.  
  
 `Like` Operátor je určená jenom pro porovnávání vzorů z `String` operandy. Visual Basic se pokusí převést každý operand tak, aby `String` před provedením operace. Datový typ výsledku je vždy `Boolean`.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátory](../../../visual-basic/language-reference/operators/index.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
