---
title: 'Postupy: Převod mezi hexadecimálními řetězci a číselnými C# typy – Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a7109945192fe1577cd1b96c8b4d6c05270d54e8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69588382"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Postupy: Převod mezi hexadecimálními řetězci a číselnýmiC# typy (Průvodce programováním)
Tyto příklady vám ukážou, jak provádět následující úlohy:  
  
- Získá hexadecimální hodnotu každého znaku v [řetězci](../../language-reference/keywords/string.md).  
  
- Získejte [znak](../../language-reference/keywords/char.md) , který odpovídá každé hodnotě v šestnáctkovém řetězci.  
  
- Převod šestnáctkového `string` čísla na [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
- Převod šestnáctkové `string` hodnoty na [float](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Převeďte pole [bajtů](../../language-reference/builtin-types/integral-numeric-types.md) na hexadecimální `string`hodnotu.  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří výstup hexadecimální hodnoty každého znaku v `string`. Nejprve analyzuje `string` pole znaků. Pak volá <xref:System.Convert.ToInt32%28System.Char%29> každý znak a získá tak číselnou hodnotu. Nakonec formátuje číslo jako šestnáctkové vyjádření v `string`.  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Příklad  
 Tento příklad analyzuje `string` šestnáctkové hodnoty a vypíše znak odpovídající každé hexadecimální hodnotě. Nejprve zavolá metodu [Split (Char\[\])](xref:System.String.Split(System.Char[])) pro získání každé hexadecimální hodnoty jako jednotlivce `string` v poli. Poté volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> k převedení hexadecimální hodnoty na desítkovou hodnotu reprezentovanou jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Zobrazuje dva různé způsoby získání znaku odpovídajícího kódu znaku. První technika používá <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, která vrací znak odpovídající celočíselnému argumentu `string`jako. Druhá technika je explicitně přetypování `int` na typ [char](../../language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje jiný způsob, jak převést šestnáctkové `string` hodnoty na celé číslo, <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> voláním metody.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `string` , jak převést šestnáctkovou hodnotu na [float](../../language-reference/builtin-types/floating-point-numeric-types.md) <xref:System.BitConverter?displayProperty=nameWithType> pomocí třídy a <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést pole [bajtů](../../language-reference/builtin-types/integral-numeric-types.md) na šestnáctkový řetězec pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](./index.md)
- [Postupy: Určení, zda řetězec představuje číselnou hodnotu](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
