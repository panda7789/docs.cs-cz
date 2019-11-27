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
ms.openlocfilehash: 3867d433ea5f9a6effe70db0ff4162390fb50b5c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74331473"
---
# <a name="data-types-of-operator-results-visual-basic"></a>Datové typy výsledků operátoru (Visual Basic)
Visual Basic Určuje datový typ výsledku operace na základě datových typů operandů. V některých případech to může být datový typ s větším rozsahem než u obou operandů.  
  
## <a name="data-type-ranges"></a>Rozsahy datového typu  
 Rozsahy relevantních datových typů, od nejmenších po největší, jsou následující:  
  
- [Boolean](../../../visual-basic/language-reference/data-types/boolean-data-type.md) – dvě možné hodnoty  
  
- [SByte](../../../visual-basic/language-reference/data-types/sbyte-data-type.md), [Byte](../../../visual-basic/language-reference/data-types/byte-data-type.md) – 256 možných celočíselných hodnot  
  
- [Short](../../../visual-basic/language-reference/data-types/short-data-type.md), [UShort](../../../visual-basic/language-reference/data-types/ushort-data-type.md) – 65 536 (6,5... E + 4) možné celočíselné hodnoty  
  
- [Integer](../../../visual-basic/language-reference/data-types/integer-data-type.md), [UInteger –](../../../visual-basic/language-reference/data-types/uinteger-data-type.md) – 4 294 967 296 (4.2... E + 9) možné celočíselné hodnoty  
  
- [Long](../../../visual-basic/language-reference/data-types/long-data-type.md), [ulong](../../../visual-basic/language-reference/data-types/ulong-data-type.md) – 18446744073709551615 (1.8... E + 19) možné celočíselné hodnoty  
  
- [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) – 1,5... e + 29 možné celočíselné hodnoty, maximální rozsah 7.9... e + 28 (absolutní hodnota)  
  
- [Single](../../../visual-basic/language-reference/data-types/single-data-type.md) – maximální rozsah 3.4... E + 38 (absolutní hodnota)  
  
- [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) – maximální rozsah 1.7... E + 308 (absolutní hodnota)  
  
 Další informace o Visual Basic datových typů najdete v tématu [datové typy](../../../visual-basic/language-reference/data-types/index.md).  
  
 Pokud je operand vyhodnocen jako [Nothing](../../../visual-basic/language-reference/nothing.md), Visual Basic aritmetické operátory jsou považovány za nulu.  
  
## <a name="decimal-arithmetic"></a>Desítkové aritmetické operace  
 Všimněte si, že datový typ [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md) není plovoucí desetinná čárka ani celé číslo.  
  
 Pokud je jeden z operandů `+`, `–`, `*`, `/`nebo `Mod` operace `Decimal` a druhý není `Single` nebo `Double`, Visual Basic rozšíří druhý operand na `Decimal`. Provede operaci v `Decimal`a datový typ výsledku je `Decimal`.  
  
## <a name="floating-point-arithmetic"></a>Aritmetické operace s plovoucí desetinnou čárkou  
 Visual Basic provádí většinu aritmetických výpočtů s plovoucí desetinnou čárkou v [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), což je nejúčinnější datový typ pro tyto operace. Pokud je však jeden operand [jediný](../../../visual-basic/language-reference/data-types/single-data-type.md) a druhý není `Double`, Visual Basic provede operaci v `Single`. Rozšiřuje každý operand tak, jak je to nutné pro příslušný datový typ před operací a výsledek má tento datový typ.  
  
### <a name="-and--operators"></a>Operátory/a ^  
 Operátor `/` je definován pouze pro datové typy [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)a [Double](../../../visual-basic/language-reference/data-types/double-data-type.md) . Visual Basic rozšiřuje každý operand tak, jak je to nutné pro příslušný datový typ před operací a výsledek má tento datový typ.  
  
 V následující tabulce jsou uvedeny typy dat výsledků pro operátor `/`. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
||||||  
|---|---|---|---|---|  
||`Decimal`|`Single`|`Double`|Libovolný celočíselný typ|  
|`Decimal`|Decimal|Single|Double|Decimal|  
|`Single`|Single|Single|Double|Single|  
|`Double`|Double|Double|Double|Double|  
|Libovolný celočíselný typ|Decimal|Single|Double|Double|  
  
 Operátor `^` je definován pouze pro datový typ `Double`. Visual Basic rozšiřuje každý operand tak, jak je to nutné pro `Double` před operací a výsledný datový typ je vždy `Double`.  
  
## <a name="integer-arithmetic"></a>Aritmetický typ Integer  
 Výsledný datový typ celočíselné operace závisí na datových typech operandů. Obecně platí, že Visual Basic k určení typu výsledných dat používá následující zásady:  
  
- Pokud mají oba operandy binárního operátoru stejný datový typ, výsledek má tento datový typ. Výjimka je `Boolean`, což je nuceně `Short`.  
  
- Pokud se operand bez znaménka účastní podepsaného operandu, má výsledek podepsaný typ s aspoň jako velký rozsah jako jeden operand.  
  
- V opačném případě má výsledek obvykle větší ze dvou datových typů operandů.  
  
 Všimněte si, že výsledný datový typ nemusí být stejný jako datový typ operandu.  
  
> [!NOTE]
> Výsledný datový typ není vždy dostatečně velký, aby mohl uchovávat všechny možné hodnoty, které jsou výsledkem operace. Výjimka <xref:System.OverflowException> může nastat, pokud je hodnota pro výsledný datový typ příliš velká.  
  
### <a name="unary--and--operators"></a>Unární operátory + a –  
 V následující tabulce jsou uvedeny typy dat výsledků pro dva unární operátory `+` a `–`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|Unární `+`|Krátké|SByte –|Bajt|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
|Unární `–`|Krátké|SByte –|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Decimal|  
  
### <a name="-and--operators"></a><operátory > \< a >  
 V následující tabulce jsou uvedeny typy dat výsledků pro dva operátory bitového posunutí `<<` a `>>`. Visual Basic zpracovává každý operátor bitového posunutí jako unární operátor na levém operandu (Bitová maska, která se má posunout).  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`<<``>>`|Krátké|SByte –|Bajt|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
  
 Pokud je levý operand `Decimal`, `Single`, `Double`nebo `String`, Visual Basic se pokusí ho převést na `Long` před operací a datový typ výsledku je `Long`. Pravý operand (počet bitových pozic k posunu) musí být `Integer` nebo typ, který se rozšíří na `Integer`.  
  
### <a name="binary----and-mod-operators"></a>Operátory Binary +,-, \*a mod  
 V následující tabulce jsou uvedeny typy dat výsledků pro binární `+` a operátory `–` a `*` a `Mod`. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krátké|SByte –|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Decimal|  
|`SByte`|SByte –|SByte –|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Decimal|  
|`Byte`|Krátké|Krátké|Bajt|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Decimal|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Decimal|  
|`UInteger`|Dlouhé|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Decimal|  
|`ULong`|Decimal|Decimal|ULong|Decimal|ULong|Decimal|ULong|Decimal|ULong|  
  
### <a name="-operator"></a>\\ – operátor  
 V následující tabulce jsou uvedeny typy dat výsledků pro operátor `\`. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Krátké|SByte –|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`SByte`|SByte –|SByte –|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`Byte`|Krátké|Krátké|Bajt|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UInteger`|Dlouhé|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|  
|`ULong`|Dlouhé|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|  
  
 Pokud je Operand operátoru `\` [Decimal](../../../visual-basic/language-reference/data-types/decimal-data-type.md), [Single](../../../visual-basic/language-reference/data-types/single-data-type.md)nebo [Double](../../../visual-basic/language-reference/data-types/double-data-type.md), Visual Basic se pokusí ho převést na [dlouhou dobu](../../../visual-basic/language-reference/data-types/long-data-type.md) před operací a výsledný datový typ je `Long`.  
  
## <a name="relational-and-bitwise-comparisons"></a>Relační a bitové porovnání  
 Typ dat výsledku relační operace (`=`, `<>`, `<`, `>`, `<=`, `>=`) je vždycky `Boolean`[logický datový typ](../../../visual-basic/language-reference/data-types/boolean-data-type.md). Totéž platí pro logické operace (`And`, `AndAlso`, `Not`, `Or`, `OrElse`, `Xor`) na `Boolean` operandy.  
  
 Výsledný datový typ bitové logické operace závisí na datových typech operandů. Všimněte si, že `AndAlso` a `OrElse` jsou definovány pouze pro `Boolean`a Visual Basic před provedením operace převede každý operand podle potřeby na `Boolean`.  
  
### <a name="-----and--operators"></a>=, < >, \<, >, \<= a > = operátory  
 Pokud jsou oba operandy `Boolean`, Visual Basic považuje `True` za méně než `False`. Pokud číselný typ je porovnán s `String`, Visual Basic se pokusí převést `String` na `Double` před operací. Operand `Char` nebo `Date` lze porovnat pouze s jiným operandem stejného datového typu. Výsledný datový typ je vždycky `Boolean`.  
  
### <a name="bitwise-not-operator"></a>Bitový operátor NOT  
 V následující tabulce jsou uvedeny typy dat výsledků pro bitový operátor `Not`.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Not`|Logická hodnota|SByte –|Bajt|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
  
 Pokud je operand `Decimal`, `Single`, `Double`nebo `String`, Visual Basic se pokusí ho převést na `Long` před operací a datový typ výsledku je `Long`.  
  
### <a name="bitwise-and-or-and-xor-operators"></a>Bitové operátory and, or a XOR  
 V následující tabulce jsou uvedeny typy dat výsledků pro bitové `And`, `Or`a operátory `Xor`. Všimněte si, že je tato tabulka symetrická; pro danou kombinaci datových typů operand je výsledný datový typ stejný bez ohledu na pořadí operandů.  
  
|||||||||||  
|---|---|---|---|---|---|---|---|---|---|  
||`Boolean`|`SByte`|`Byte`|`Short`|`UShort`|`Integer`|`UInteger`|`Long`|`ULong`|  
|`Boolean`|Logická hodnota|SByte –|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`SByte`|SByte –|SByte –|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`Byte`|Krátké|Krátké|Bajt|Krátké|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Short`|Krátké|Krátké|Krátké|Krátké|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UShort`|Integer|Integer|UShort|Integer|UShort|Integer|UInteger –|Dlouhé|ULong|  
|`Integer`|Integer|Integer|Integer|Integer|Integer|Integer|Dlouhé|Dlouhé|Dlouhé|  
|`UInteger`|Dlouhé|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|UInteger –|Dlouhé|ULong|  
|`Long`|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|Dlouhé|  
|`ULong`|Dlouhé|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|Dlouhé|ULong|  
  
 Pokud je operand `Decimal`, `Single`, `Double`nebo `String`, Visual Basic se pokusí ho převést na `Long` před operací a výsledný datový typ je stejný, jako kdyby byl tento operand již `Long`.  
  
## <a name="miscellaneous-operators"></a>Různé operátory  
 Operátor `&` je definován pouze pro zřetězení operandů `String`. Visual Basic převede každý operand tak, jak je to nutné, aby `String` před operací a výsledný datový typ je vždy `String`. Pro účely operátoru `&` se všechny převody na `String` považují za rozšiřující, i když je `On``Option Strict`.  
  
 Operátory `Is` a `IsNot` vyžadují, aby oba operandy byly typu odkazu. Výraz `TypeOf`...`Is` vyžaduje, aby první operand byl typu odkazu a druhý operand byl názvem datového typu. Ve všech těchto případech je datový typ výsledku `Boolean`.  
  
 Operátor `Like` je definován pouze pro porovnávání vzorů operandů `String`. Visual Basic se pokusí převést každý operand, jak je to nutné pro `String` před operací. Výsledný datový typ je vždycky `Boolean`.  
  
## <a name="see-also"></a>Viz také:

- [Datové typy](../../../visual-basic/language-reference/data-types/index.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Aritmetické operátory v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/arithmetic-operators.md)
- [Operátory porovnávání v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operátory](../../../visual-basic/language-reference/operators/index.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
