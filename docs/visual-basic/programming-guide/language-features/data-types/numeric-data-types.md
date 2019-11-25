---
title: Numerické datové typy
ms.date: 07/20/2015
helpviewer_keywords:
- integral types [Visual Basic], Visual Basic
- Short data type [Visual Basic], numeric data types
- Double data type [Visual Basic], numeric data types
- Long data type [Visual Basic], Visual Basic numeric data types
- numbers [Visual Basic], whole
- fractions
- numbers
- whole numbers
- integer numbers
- numbers [Visual Basic], integer
- fractional data types [Visual Basic]
- mantissas, of fractional numbers
- mantissas
- data types [Visual Basic], numeric
- Integer data type [Visual Basic], numeric data types
- exponent, of fractional numbers
- integers [Visual Basic]
- numeric data types [Visual Basic], Visual Basic
- Single data type [Visual Basic], numeric types
- Decimal data type [Visual Basic], numeric data types
ms.assetid: a27bd4d0-7e14-43eb-9cc4-b42eaab323c9
ms.openlocfilehash: dc8b630eebc48e5733344a00664b453360769c0b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346314"
---
# <a name="numeric-data-types-visual-basic"></a>Numerické datové typy (Visual Basic)
Visual Basic supplies several *numeric data types* for handling numbers in various representations. *Integral* types represent only whole numbers (positive, negative, and zero), and *nonintegral* types represent numbers with both integer and fractional parts.  
  
 For a table showing a side-by-side comparison of the Visual Basic data types, see [Data Types](../../../../visual-basic/language-reference/data-types/index.md).  
  
## <a name="integral-numeric-types"></a>Integral Numeric Types  
 *Integral data types* are those that represent only numbers without fractional parts.  
  
 The *signed* integral data types are [SByte Data Type](../../../../visual-basic/language-reference/data-types/sbyte-data-type.md) (8-bit), [Short Data Type](../../../../visual-basic/language-reference/data-types/short-data-type.md) (16-bit), [Integer Data Type](../../../../visual-basic/language-reference/data-types/integer-data-type.md) (32-bit), and [Long Data Type](../../../../visual-basic/language-reference/data-types/long-data-type.md) (64-bit). If a variable always stores integers rather than fractional numbers, declare it as one of these types.  
  
 The *unsigned* integral types are [Byte Data Type](../../../../visual-basic/language-reference/data-types/byte-data-type.md) (8-bit), [UShort Data Type](../../../../visual-basic/language-reference/data-types/ushort-data-type.md) (16-bit), [UInteger Data Type](../../../../visual-basic/language-reference/data-types/uinteger-data-type.md) (32-bit), and [ULong Data Type](../../../../visual-basic/language-reference/data-types/ulong-data-type.md) (64-bit). If a variable contains binary data, or data of unknown nature, declare it as one of these types.  
  
### <a name="performance"></a>Výkon  
 Arithmetic operations are faster with integral types than with other data types. They are fastest with the `Integer` and `UInteger` types in Visual Basic.  
  
### <a name="large-integers"></a>Large Integers  
 If you need to hold an integer larger than the `Integer` data type can hold, you can use the `Long` data type instead. `Long` variables can hold numbers from -9,223,372,036,854,775,808 through 9,223,372,036,854,775,807. Operations with `Long` are slightly slower than with `Integer`.  
  
 If you need even larger values, you can use the [Decimal Data Type](../../../../visual-basic/language-reference/data-types/decimal-data-type.md). You can hold numbers from -79,228,162,514,264,337,593,543,950,335 through 79,228,162,514,264,337,593,543,950,335 in a `Decimal` variable if you do not use any decimal places. However, operations with `Decimal` numbers are considerably slower than with any other numeric data type.  
  
### <a name="small-integers"></a>Small Integers  
 If you do not need the full range of the `Integer` data type, you can use the `Short` data type, which can hold integers from -32,768 through 32,767. For the smallest integer range, the `SByte` data type holds integers from -128 through 127. If you have a very large number of variables that hold small integers, the common language runtime can sometimes store your `Short` and `SByte` variables more efficiently and save memory consumption. However, operations with `Short` and `SByte` are somewhat slower than with `Integer`.  
  
### <a name="unsigned-integers"></a>Unsigned Integers  
 If you know that your variable never needs to hold a negative number, you can use the *unsigned types*`Byte`, `UShort`, `UInteger`, and `ULong`. Each of these data types can hold a positive integer twice as large as its corresponding signed type (`SByte`, `Short`, `Integer`, and `Long`). In terms of performance, each unsigned type is exactly as efficient as its corresponding signed type. In particular, `UInteger` shares with `Integer` the distinction of being the most efficient of all the elementary numeric data types.  
  
## <a name="nonintegral-numeric-types"></a>Nonintegral Numeric Types  
 *Nonintegral data types* are those that represent numbers with both integer and fractional parts.  
  
 The nonintegral numeric data types are `Decimal` (128-bit fixed point), [Single Data Type](../../../../visual-basic/language-reference/data-types/single-data-type.md) (32-bit floating point), and [Double Data Type](../../../../visual-basic/language-reference/data-types/double-data-type.md) (64-bit floating point). They are all signed types. If a variable can contain a fraction, declare it as one of these types.  
  
 `Decimal` is not a floating-point data type. `Decimal` numbers have a binary integer value and an integer scaling factor that specifies what portion of the value is a decimal fraction.  
  
 You can use `Decimal` variables for money values. The advantage is the precision of the values. The `Double` data type is faster and requires less memory, but it is subject to rounding errors. The `Decimal` data type retains complete accuracy to 28 decimal places.  
  
 Floating-point (`Single` and `Double`) numbers have larger ranges than `Decimal` numbers but can be subject to rounding errors. Floating-point types support fewer significant digits than `Decimal` but can represent values of greater magnitude.  
  
 Nonintegral number values can be expressed as mmmEeee, in which mmm is the *mantissa* (the significant digits) and eee is the *exponent* (a power of 10). The highest positive values of the nonintegral types are 7.9228162514264337593543950335E+28 for `Decimal`, 3.4028235E+38 for `Single`, and 1.79769313486231570E+308 for `Double`.  
  
### <a name="performance"></a>Výkon  
 `Double` is the most efficient of the fractional data types, because the processors on current platforms perform floating-point operations in double precision. However, operations with `Double` are not as fast as with the integral types such as `Integer`.  
  
### <a name="small-magnitudes"></a>Small Magnitudes  
 For numbers with the smallest possible magnitude (closest to 0), `Double` variables can hold numbers as small as -4.94065645841246544E-324 for negative values and 4.94065645841246544E-324 for positive values.  
  
### <a name="small-fractional-numbers"></a>Small Fractional Numbers  
 If you do not need the full range of the `Double` data type, you can use the `Single` data type, which can hold floating-point numbers from -3.4028235E+38 through 3.4028235E+38. The smallest magnitudes for `Single` variables are -1.401298E-45 for negative values and 1.401298E-45 for positive values. If you have a very large number of variables that hold small floating-point numbers, the common language runtime can sometimes store your `Single` variables more efficiently and save memory consumption.  
  
## <a name="see-also"></a>Viz také:

- [Základní datové typy](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)
- [Znakové datové typy](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)
- [Různé datové typy](../../../../visual-basic/programming-guide/language-features/data-types/miscellaneous-data-types.md)
- [Řešení potíží s datovými typy](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [Postupy: Volání funkce systému Windows, která přebírá nepřiřazené typy](../../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
