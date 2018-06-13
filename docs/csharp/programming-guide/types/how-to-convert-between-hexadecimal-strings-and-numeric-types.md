---
title: 'Postupy: Převod mezi hexadecimálními řetězci a číselnými typy (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: 1a5bde0a9169a78e179a69c7a2f4080e5a465f54
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334698"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Postupy: Převod mezi hexadecimálními řetězci a číselnými typy (Průvodce programováním v C#)
Tyto příklady ukazují, jak provádět následující úlohy:  
  
-   Získat šestnáctkové hodnoty každý znak v [řetězec](../../../csharp/language-reference/keywords/string.md).  
  
-   Získat [char](../../../csharp/language-reference/keywords/char.md) odpovídající každé hodnotě v řetězec hexadecimálních znaků.  
  
-   Převést hexadecimální `string` k [int](../../../csharp/language-reference/keywords/int.md).  
  
-   Převést hexadecimální `string` k [float](../../../csharp/language-reference/keywords/float.md).  
  
-   Převést [bajtů](../../../csharp/language-reference/keywords/byte.md) pole pro hexadecimální `string`.  
  
## <a name="example"></a>Příklad  
 Výstupy šestnáctkové hodnoty každý znak v tomto příkladu `string`. Nejprve analyzuje `string` na pole znaků. Potom zavolá <xref:System.Convert.ToInt32%28System.Char%29> na každý znak získat jeho číselnou hodnotu. Nakonec formátuje číslo jako hexadecimální vyjádření v `string`.  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu analyzuje `string` z hexadecimální hodnoty a výstupy znak odpovídající každé šestnáctkové hodnoty. První volání [rozdělení (Char\[\])](xref:System.String.Split(System.Char[])) metoda získat každý šestnáctkové hodnoty jako samostatnou `string` v matici. Potom zavolá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> Převést šestnáctkové hodnoty hodnotu decimal vyjádřené [int](../../../csharp/language-reference/keywords/int.md). Zobrazuje dvěma různými způsoby získat znak odpovídající tento kód znaku. První způsob využívá <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, který vrátí znak odpovídající argument celého čísla jako `string`. Druhý způsob spočívá explicitně vrhá `int` k [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje další způsob, jak převést hexadecimální `string` na celé číslo, voláním <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metoda.  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést hexadecimální `string` k [float](../../../csharp/language-reference/keywords/float.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy a <xref:System.Int32.Parse%2A?displayProperty=nameWithType> metoda.  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést [bajtů](../../../csharp/language-reference/keywords/byte.md) pole pro řetězec hexadecimálních znaků pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy.  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a>Viz také  
 [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)  
 [Typy](../../../csharp/programming-guide/types/index.md)  
 [Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
