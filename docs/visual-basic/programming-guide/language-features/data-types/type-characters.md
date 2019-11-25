---
title: Znaky typu
ms.date: 01/31/2018
helpviewer_keywords:
- '&H prefix for hexadecimal values'
- hexadecimal literals [Visual Basic]
- F literal type character [Visual Basic]
- '& identifier type character'
- type characters [Visual Basic]
- octal literals [Visual Basic]
- literals [Visual Basic], hexadecimal
- '&O prefix for octal values'
- literals [Visual Basic], default types
- defaults, literal types
- C literal type character [Visual Basic]
- type characters [Visual Basic], literal
- $ identifier type character
- L literal type character [Visual Basic]
- UI literal type characters [Visual Basic]
- default literal types [Visual Basic]
- D literal type character [Visual Basic]
- literals [Visual Basic], octal
- S literal type character [Visual Basic]
- '! identifier type character'
- US literal type characters [Visual Basic]
- '% identifier type character'
- data types [Visual Basic], type characters
- characters [Visual Basic], identifier type
- type characters [Visual Basic], identifier
- '# identifier type character'
- identifier type characters [Visual Basic]
- literal type characters [Visual Basic]
- I literal type character [Visual Basic]
- R literal type character [Visual Basic]
- '@ identifier type character'
- UL literal type characters [Visual Basic]
- literal types [Visual Basic], default
ms.assetid: 6353cb9b-6ee4-4af6-a5a8-88ce39f90cc5
ms.openlocfilehash: 628461c8136946dd902c0a52048eee7c516c52cd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352927"
---
# <a name="type-characters-visual-basic"></a>Type characters (Visual Basic)

In addition to specifying a data type in a declaration statement, you can force the data type of some programming elements with a *type character*. The type character must immediately follow the element, with no intervening characters of any kind.

The type character is not part of the name of the element. An element defined with a type character can be referenced without the type character.

## <a name="identifier-type-characters"></a>Identifier type characters

Visual Basic supplies a set of *identifier type characters* that you can use in a declaration to specify the data type of a variable or constant. The following table shows the available identifier type characters with examples of usage.
  
|Identifier type character|Datový typ|Příklad|  
|-------------------------------|---------------|-------------|  
|`%`|`Integer`|`Dim L%`|  
|`&`|`Long`|`Dim M&`|  
|`@`|`Decimal`|`Const W@ = 37.5`|  
|`!`|`Single`|`Dim Q!`|  
|`#`|`Double`|`Dim X#`|  
|`$`|`String`|`Dim V$ = "Secret"`|  
  
 No identifier type characters exist for the `Boolean`, `Byte`, `Char`, `Date`, `Object`, `SByte`, `Short`, `UInteger`, `ULong`, or `UShort` data types, or for any composite data types such as arrays or structures.

In some cases, you can append the `$` character to a Visual Basic function, for example `Left$` instead of `Left`, to obtain a returned value of type `String`.

In all cases, the identifier type character must immediately follow the identifier name.

## <a name="literal-type-characters"></a>Literal type characters

A *literal* is a textual representation of a particular value of a data type.  

### <a name="default-literal-types"></a>Default literal types

The form of a literal as it appears in your code ordinarily determines its data type. The following table shows these default types.  
  
|Textual form of literal|Default data type|Příklad|  
|-----------------------------|-----------------------|-------------|  
|Numeric, no fractional part|`Integer`|`2147483647`|  
|Numeric, no fractional part, too large for `Integer`|`Long`|`2147483648`|  
|Numeric, fractional part|`Double`|`1.2`|  
|Enclosed in double quotation marks|`String`|`"A"`|  
|Enclosed within number signs|`Date`|`#5/17/1993 9:32 AM#`|  

### <a name="forced-literal-types"></a>Forced literal types

Visual Basic supplies a set of *literal type characters*, which you can use to force a literal to assume a data type other than the one its form indicates. You do this by appending the character to the end of the literal. The following table shows the available literal type characters with examples of usage.
  
|Literal type character|Datový typ|Příklad|  
|----------------------------|---------------|-------------|  
|`S`|`Short`|`I = 347S`|
|`I`|`Integer`|`J = 347I`|
|`L`|`Long`|`K = 347L`|
|`D`|`Decimal`|`X = 347D`|
|`F`|`Single`|`Y = 347F`|
|`R`|`Double`|`Z = 347R`|
|`US`|`UShort`|`L = 347US`|
|`UI`|`UInteger`|`M = 347UI`|
|`UL`|`ULong`|`N = 347UL`|
|`C`|`Char`|`Q = "."C`|

No literal type characters exist for the `Boolean`, `Byte`, `Date`, `Object`, `SByte`, or `String` data types, or for any composite data types such as arrays or structures.

Literals can also use the identifier type characters (`%`, `&`, `@`, `!`, `#`, `$`), as can variables, constants, and expressions. However, the literal type characters (`S`, `I`, `L`, `D`, `F`, `R`, `C`) can be used only with literals.

In all cases, the literal type character must immediately follow the literal value.

## <a name="hexadecimal-binary-and-octal-literals"></a>Hexadecimal, binary, and octal literals

The compiler normally interprets an integer literal to be in the decimal (base 10) number system. You can also define an integer literal as a hexadecimal (base 16) number with the `&H` prefix, as a binary (base 2) number with the `&B` prefix, and as an octal (base 8) number with the `&O` prefix. The digits that follow the prefix must be appropriate for the number system. The following table illustrates this.  
  
|Number base|Prefix|Valid digit values|Příklad|
|-----------------|------------|------------------------|-------------|
|Hexadecimal (base 16)|`&H`|0-9 and A-F|`&HFFFF`|
|Binary (base 2)|`&B`|0-1|`&B01111100`|
|Octal (base 8)|`&O`|0-7|`&O77`|

Starting in Visual Basic 2017, you can use the underscore character (`_`) as a group separator to enhance the readability of an integral literal. The following example uses the `_` character to group a binary literal into 8-bit groups:

```vb
Dim number As Integer = &B00100010_11000101_11001111_11001101
```

You can follow a prefixed literal with a literal type character. The following example shows this.

```vb
Dim counter As Short = &H8000S
Dim flags As UShort = &H8000US
```

In the previous example, `counter` has the decimal value of -32768, and `flags` has the decimal value of +32768.

Starting with Visual Basic 15.5, you can also use the underscore character (`_`) as a leading separator between the prefix and the hexadecimal, binary, or octal digits. Příklad:

```vb
Dim number As Integer = &H_C305_F860
```

[!INCLUDE [supporting-underscores](../../../../../includes/vb-separator-langversion.md)]

## <a name="see-also"></a>Viz také:

- [Datové typy](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
- [Type Conversions in Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)
