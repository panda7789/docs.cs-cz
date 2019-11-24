---
title: 'How to: Convert Between Hexadecimal Strings and Numeric Types - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 8b72734f9b617fed2ff65977c9a0e60f46424ae8
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/23/2019
ms.locfileid: "74429437"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Postupy: Převod mezi hexadecimálními řetězci a číselnými typy (Průvodce programováním v C#)
These examples show you how to perform the following tasks:  
  
- Obtain the hexadecimal value of each character in a [string](../../language-reference/builtin-types/reference-types.md).  
  
- Obtain the [char](../../language-reference/builtin-types/char.md) that corresponds to each value in a hexadecimal string.  
  
- Convert a hexadecimal `string` to an [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
- Convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal `string`.  
  
## <a name="example"></a>Příklad  
 This example outputs the hexadecimal value of each character in a `string`. First it parses the `string` to an array of characters. Then it calls <xref:System.Convert.ToInt32%28System.Char%29> on each character to obtain its numeric value. Finally, it formats the number as its hexadecimal representation in a `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Příklad  
 This example parses a `string` of hexadecimal values and outputs the character corresponding to each hexadecimal value. First it calls the [Split(Char\[\])](xref:System.String.Split(System.Char[])) method to obtain each hexadecimal value as an individual `string` in an array. Then it calls <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> to convert the hexadecimal value to a decimal value represented as an [int](../../language-reference/builtin-types/integral-numeric-types.md). It shows two different ways to obtain the character corresponding to that character code. The first technique uses <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, which returns the character corresponding to the integer argument as a `string`. The second technique explicitly casts the `int` to a [char](../../language-reference/builtin-types/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Příklad  
 This example shows another way to convert a hexadecimal `string` to an integer, by calling the <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> method.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Příklad  
 The following example shows how to convert a hexadecimal `string` to a [float](../../language-reference/builtin-types/floating-point-numeric-types.md) by using the <xref:System.BitConverter?displayProperty=nameWithType> class and the <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> method.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Příklad  
 The following example shows how to convert a [byte](../../language-reference/builtin-types/integral-numeric-types.md) array to a hexadecimal string by using the <xref:System.BitConverter?displayProperty=nameWithType> class.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](./index.md)
- [Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
