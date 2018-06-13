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
ms.openlocfilehash: c2e94a80e83becf25bf47ef7837362f0ebf441a9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33605430"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Datové typy výsledků operátoru (Visual Basic)
Visual Basic určuje datový typ výsledku operace založené na datové typy operandy. V některých případech to může být datový typ s větší rozsah než buď operand.  
  
## <a name="data-type-ranges"></a>Rozsahy datového typu  
 Rozsahy typů relevantních dat, v pořadí od nejmenšího po největší, jsou následující:  
  
-   [Logická hodnota](../../../visual-basic/language-reference/data-types/boolean-data-type.md) – dvě možné hodnoty  
  
-   [SByte –](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [bajtů](../../../visual-basic/language-reference/data-types/byte-data-type.md) – 256 možné celočíselné hodnoty  
  
-   [Krátký](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) – 65 536 (6.5 … E + 4) možné celočíselné hodnoty  
  
-   [Celé číslo](../../../visual-basic/language-reference/data-types/integer-data-type.md), [uinteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) – 4 294 967 296 (4.2 … E + 9) možné celočíselné hodnoty  
  
-   [Dlouhé](../../../visual-basic/language-reference/data-types/long-data-type.md), [ULong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) – 18,446,744,073,709,551,615 (1.8 … E + 19) možné celočíselné hodnoty  
  
-   [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) – 1.5 … E + 29 možné celočíselné hodnoty, maximální rozsah 7.9 … E + 28 (absolutní hodnota)  
  
-   [Jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) – maximální rozsah 3.4 … E + 38 (absolutní hodnota)  
  
-   [Dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md) – maximální rozsah 1.7 … E + 308 (absolutní hodnota)  
  
 Další informace v jazyce Visual Basic – datové typy najdete v tématu [datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md).  
  
 Pokud je výsledkem operand [nic](../../../visual-basic/language-reference/nothing.md), aritmetické operátory jazyka Visual Basic s nimi zacházet jako nula.  
  
## <a name="decimal-arithmetic"></a>Decimal aritmetické operace  
 Všimněte si, že [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) je datový typ, ani s plovoucí desetinnou čárkou ani celé číslo.  
  
 Pokud buď operand `+`, `–`, `*`, `/`, nebo `Mod` operace je `Decimal` a dalších není `Single` nebo `Double`, Visual Basic rozšiřuje jiných operand pro `Decimal`. Provede operaci v `Decimal`, a výsledný typ dat je `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Aritmetické operace s plovoucí desetinnou čárkou  
 Visual Basic provádí většinu aritmetické s plovoucí desetinnou čárkou v [dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md), což je nejúčinnější data zadejte pro tyto operace. Ale pokud je jeden operand [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md) a dalších není `Double`, provede operaci v jazyce Visual Basic `Single`. Ji rozšiřuje každý operand v případě potřeby na odpovídající datový typ před provedením operace a výsledek obsahuje datového typu.  
  
### <a name="-and--operators"></a>/ a ^ operátory  
 `/` Operátor je určená jenom pro [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md), a [dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md) datové typy. Visual Basic rozšiřuje každý operand v případě potřeby na odpovídající datový typ před provedením operace a výsledek obsahuje tento typ dat.  
  
 V následující tabulce jsou uvedeny výsledek datové typy pro `/` operátor. Upozorňujeme, že je tato tabulka symetrický; datový typ výsledku pro dané kombinace operand datové typy, je stejný bez ohledu na pořadí operandy.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Žádný typ celé číslo|  
|`Decimal`|Desetinné číslo|Single|Double|Desetinné číslo|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Žádný typ celé číslo|Desetinné číslo|Single|Double|Double|  
  
 `^` Operátor je určená jenom pro `Double` datového typu. Visual Basic rozšiřuje každý operand podle potřeby k `Double` před operace a výsledek datový typ je vždy `Double`.  
  
## <a name="integer-arithmetic"></a>Celočíselné aritmetiky  
 Datový typ výsledku operace celé číslo závisí na typech dat operandy. Obecně platí jazyka Visual Basic používá následující zásady pro zjištění výsledku datový typ:  
  
-   Pokud oba operandy binárního operátoru mít stejný datový typ, výsledek obsahuje datového typu. Výjimkou je `Boolean`, který je nucen se `Short`.  
  
-   Pokud se nepodepsané operand účastní s podepsaný operandem, výsledek obsahuje typ se znaménkem s alespoň tak velké rozsah jako buď operand.  
  
-   Jinak výsledek obvykle obsahuje větší z těchto dvou typů dat operand.  
  
 Všimněte si, výsledný typ dat nemusí být stejný jako buď datový typ operandu.  
  
> [!NOTE]
>  Datový typ výsledku vždy není dostatečně velký pro uložení všech možných hodnot plynoucí z operace. <xref:System.OverflowException> Výjimce může dojít, pokud hodnota je příliš velká pro datový typ výsledku.  
  
### <a name="unary--and--operators"></a>Unární + a – operátory  
 Následující tabulka uvádí výsledek datové typy pro dva unární operátory, `+` a `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unární `+`|krátký|SByte|Byte|krátký|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
|Unární `–`|krátký|SByte|krátký|krátký|Integer|Integer|dlouhá|dlouhá|Desetinné číslo|  
  
### <a name="-and--operators"></a><\< a >> operátory  
 Následující tabulka uvádí výsledek datové typy pro dvě bitové posunutí – operátory `<<` a `>>`. Visual Basic zpracovává jednotlivé bitové posunutí – operátory jako unární operátor na jeho levý operand (vzoru bitové posunutí).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<`, `>>`|krátký|SByte|Byte|krátký|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
  
 Pokud je levý operand `Decimal`, `Single`, `Double`, nebo `String`, Visual Basic pokusí převeďte ho na `Long` před operace a výsledek je datový typ `Long`. Pravý operand (počet pozic bit se posunou) musí být `Integer` nebo typ, který rozšiřuje na `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Binární +, -, * a Mod operátory  
 V následující tabulce jsou uvedeny výsledek datové typy pro binárního souboru `+` a `–` operátory a `*` a `Mod` operátory. Upozorňujeme, že je tato tabulka symetrický; datový typ výsledku pro dané kombinace operand datové typy, je stejný bez ohledu na pořadí operandy.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|krátký|SByte|krátký|krátký|Integer|Integer|dlouhá|dlouhá|Desetinné číslo|  
|`SByte`|SByte|SByte|krátký|krátký|Integer|Integer|dlouhá|dlouhá|Desetinné číslo|  
|`Byte`|krátký|krátký|Byte|krátký|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
|`Short`|krátký|krátký|krátký|krátký|Integer|Integer|dlouhá|dlouhá|Desetinné číslo|  
|`UShort`|Integer|Integer|Ushort –|Integer|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|dlouhá|dlouhá|Desetinné číslo|  
|`UInteger`|dlouhá|dlouhá|Uinteger –|dlouhá|Uinteger –|dlouhá|Uinteger –|dlouhá|Ulong –|  
|`Long`|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|Desetinné číslo|  
|`ULong`|Desetinné číslo|Desetinné číslo|Ulong –|Desetinné číslo|Ulong –|Desetinné číslo|Ulong –|Desetinné číslo|Ulong –|  
  
### <a name="-operator"></a>\ – operátor  
 V následující tabulce jsou uvedeny výsledek datové typy pro `\` operátor. Upozorňujeme, že je tato tabulka symetrický; datový typ výsledku pro dané kombinace operand datové typy, je stejný bez ohledu na pořadí operandy.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|krátký|SByte|krátký|krátký|Integer|Integer|dlouhá|dlouhá|dlouhá|  
|`SByte`|SByte|SByte|krátký|krátký|Integer|Integer|dlouhá|dlouhá|dlouhá|  
|`Byte`|krátký|krátký|Byte|krátký|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
|`Short`|krátký|krátký|krátký|krátký|Integer|Integer|dlouhá|dlouhá|dlouhá|  
|`UShort`|Integer|Integer|Ushort –|Integer|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|dlouhá|dlouhá|dlouhá|  
|`UInteger`|dlouhá|dlouhá|Uinteger –|dlouhá|Uinteger –|dlouhá|Uinteger –|dlouhá|Ulong –|  
|`Long`|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|  
|`ULong`|dlouhá|dlouhá|Ulong –|dlouhá|Ulong –|dlouhá|Ulong –|dlouhá|Ulong –|  
  
 Pokud buď operand `\` operátor je [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [jeden](../../../visual-basic/language-reference/data-types/single-data-type.md), nebo [dvojité](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic pokusí převeďte ho na [dlouho](../../../visual-basic/language-reference/data-types/long-data-type.md)před operace a výsledek je datový typ `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Relační a bitové porovnání  
 Datový typ výsledku relační operace (`=`, `<>`, `<`, `>`, `<=`, `>=`) je vždy `Boolean` [datový typ Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Totéž platí pro logické operace (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) na `Boolean` operandy.  
  
 Výsledný typ dat bitová logické operace závisí na datové typy operandy. Všimněte si, že `AndAlso` a `OrElse` jsou definovány pouze pro `Boolean`, a Visual Basic převede každý operand podle potřeby k `Boolean` před provedením operace.  
  
### <a name="-----and--operators"></a>= <>, \<, >, \<=, a > = operátory  
 Pokud jsou oba operandy `Boolean`, Visual Basic zvažuje `True` být menší než `False`. Pokud číselného typu se porovná se `String`, Visual Basic pokusí převést `String` k `Double` před provedením operace. A `Char` nebo `Date` operand lze porovnat pouze s jinou operand stejného datového typu. Datový typ výsledek je vždy `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bitový operátor Not  
 V následující tabulce jsou uvedeny výsledek datové typy pro bitové hodnotě `Not` operátor.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Boolean|SByte|Byte|krátký|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
  
 Pokud je operand `Decimal`, `Single`, `Double`, nebo `String`, Visual Basic pokusí převeďte ho na `Long` před operace a výsledek je datový typ `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bitový a, nebo a Xor operátory  
 V následující tabulce jsou uvedeny výsledek datové typy pro bitové hodnotě `And`, `Or`, a `Xor` operátory. Upozorňujeme, že je tato tabulka symetrický; datový typ výsledku pro dané kombinace operand datové typy, je stejný bez ohledu na pořadí operandy.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Boolean|SByte|krátký|krátký|Integer|Integer|dlouhá|dlouhá|dlouhá|  
|`SByte`|SByte|SByte|krátký|krátký|Integer|Integer|dlouhá|dlouhá|dlouhá|  
|`Byte`|krátký|krátký|Byte|krátký|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
|`Short`|krátký|krátký|krátký|krátký|Integer|Integer|dlouhá|dlouhá|dlouhá|  
|`UShort`|Integer|Integer|Ushort –|Integer|Ushort –|Integer|Uinteger –|dlouhá|Ulong –|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|dlouhá|dlouhá|dlouhá|  
|`UInteger`|dlouhá|dlouhá|Uinteger –|dlouhá|Uinteger –|dlouhá|Uinteger –|dlouhá|Ulong –|  
|`Long`|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|dlouhá|  
|`ULong`|dlouhá|dlouhá|Ulong –|dlouhá|Ulong –|dlouhá|Ulong –|dlouhá|Ulong –|  
  
 Pokud je operand `Decimal`, `Single`, `Double`, nebo `String`, Visual Basic pokusí převeďte ho na `Long` před operaci a výsledná data typu je stejný jako v případě, že operand byla již `Long`.  
  
## <a name="miscellaneous-operators"></a>Různé operátory  
 `&` Operátor je určená jenom pro zřetězení `String` operandy. Visual Basic převede každý operand podle potřeby k `String` před operace a výsledek datový typ je vždy `String`. Pro účely `&` operátor, všechny převody k `String` jsou považovány za být rozšíření, i v případě `Option Strict` je `On`.  
  
 `Is` a `IsNot` operátory vyžadují obě operandy být odkazového typu. `TypeOf`... `Is` výraz vyžaduje první operand být odkazového typu a druhý operand jako název datového typu. Ve všech těchto případech výsledných dat je typu `Boolean`.  
  
 `Like` Operátor je určená jenom pro vzor shody `String` operandy. Visual Basic pokusí převést každý operand podle potřeby k `String` před provedením operace. Datový typ výsledek je vždy `Boolean`.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Aritmetické operátory v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Operátory](../../../visual-basic/language-reference/operators/index.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
