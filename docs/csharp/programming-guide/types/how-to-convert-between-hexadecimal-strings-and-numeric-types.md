---
title: Jak převádět mezi hexadecimálními řetězci a číselnými typy – Průvodce programováním v C#
description: Naučte se převádět mezi hexadecimálními řetězci a číselnými typy. Podívejte se na příklady kódu a zobrazte další dostupné prostředky.
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: a49c4a9ee1fc19134d434d42b1eae59376c89fa4
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381798"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Jak převádět mezi hexadecimálními řetězci a číselnými typy (Průvodce programováním v C#)
Tyto příklady vám ukážou, jak provádět následující úlohy:  
  
- Získá hexadecimální hodnotu každého znaku v [řetězci](../../language-reference/builtin-types/reference-types.md).  
  
- Získejte [znak](../../language-reference/builtin-types/char.md) , který odpovídá každé hodnotě v šestnáctkovém řetězci.  
  
- Převod šestnáctkového čísla `string` na [int](../../language-reference/builtin-types/integral-numeric-types.md).  
  
- Převod šestnáctkové hodnoty `string` na [float](../../language-reference/builtin-types/floating-point-numeric-types.md).  
  
- Převeďte pole [bajtů](../../language-reference/builtin-types/integral-numeric-types.md) na hexadecimální hodnotu `string` .  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří výstup hexadecimální hodnoty každého znaku v `string` . Nejprve analyzuje `string` pole znaků. Pak volá <xref:System.Convert.ToInt32%28System.Char%29> každý znak a získá tak číselnou hodnotu. Nakonec formátuje číslo jako šestnáctkové vyjádření v `string` .  
  
 [!code-csharp[csProgGuideTypes#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#30)]  
  
## <a name="example"></a>Příklad  
 Tento příklad analyzuje `string` šestnáctkové hodnoty a vypíše znak odpovídající každé hexadecimální hodnotě. Nejprve zavolá metodu [Split (Char \[ \] )](xref:System.String.Split(System.Char[])) pro získání každé hexadecimální hodnoty jako jednotlivce `string` v poli. Poté volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> k převedení hexadecimální hodnoty na desítkovou hodnotu reprezentovanou jako [int](../../language-reference/builtin-types/integral-numeric-types.md). Zobrazuje dva různé způsoby získání znaku odpovídajícího kódu znaku. První technika používá <xref:System.Char.ConvertFromUtf32%28System.Int32%29> , která vrací znak odpovídající celočíselnému argumentu jako `string` . Druhá technika je explicitně přetypování `int` na typ [char](../../language-reference/builtin-types/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#31)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje jiný způsob, jak převést šestnáctkové `string` hodnoty na celé číslo, voláním <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metody.  
  
 [!code-csharp[csProgGuideTypes#32](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#32)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést šestnáctkovou hodnotu `string` na [float](../../language-reference/builtin-types/floating-point-numeric-types.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy a <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metody.  
  
 [!code-csharp[csProgGuideTypes#39](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#39)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést pole [bajtů](../../language-reference/builtin-types/integral-numeric-types.md) na šestnáctkový řetězec pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy.  
  
 [!code-csharp[csProgGuideTypes#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsProgGuideTypes/CS/Class1.cs#38)]  
  
## <a name="see-also"></a>Viz také:

- [Standardní řetězce pro formátování čísel](../../../standard/base-types/standard-numeric-format-strings.md)
- [Typy](./index.md)
- [Jak určit, jestli řetězec představuje číselnou hodnotu](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
