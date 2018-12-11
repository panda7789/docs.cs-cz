---
title: 'Postupy: Převod mezi hexadecimálními řetězci a číselnými typy - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- hexadecimal strings [C#], converting to numeric type
- conversions [C#], hexidecimal strings
- strings [C#], converting hexadecimal strings
- hexadecimal strings [C#]
ms.assetid: 7115c49f-7d1d-40c3-8bd9-aae0cc1d46b6
ms.openlocfilehash: d61d48ca05e93743ef3afa894ad0cbc98d6d2ab0
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237165"
---
# <a name="how-to-convert-between-hexadecimal-strings-and-numeric-types-c-programming-guide"></a>Postupy: Převod mezi hexadecimálními řetězci a číselnými typy (C# Průvodce programováním v)
Tyto příklady ukazují, jak provádět následující úlohy:  
  
-   Získat šestnáctkovou hodnotu každého znaku v [řetězec](../../../csharp/language-reference/keywords/string.md).  
  
-   Získat [char](../../../csharp/language-reference/keywords/char.md) odpovídající každé hodnotě v je možné šestnáctkový řetězec.  
  
-   Převést šestnáctkové `string` do [int](../../../csharp/language-reference/keywords/int.md).  
  
-   Převést šestnáctkové `string` k [float](../../../csharp/language-reference/keywords/float.md).  
  
-   Převést [bajtů](../../../csharp/language-reference/keywords/byte.md) pole, které chcete hexadecimální `string`.  
  
## <a name="example"></a>Příklad  
 Šestnáctková hodnota každý znak v tomto příkladu je výstupem `string`. Nejprve analyzuje `string` na pole znaků. Potom volá <xref:System.Convert.ToInt32%28System.Char%29> na jednotlivé znaky získat číselnou hodnotu. A konečně, formátuje číslo jako její šestnáctkové vyjádření v `string`.  
  
 [!code-csharp[csProgGuideTypes#30](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_1.cs)]  
  
## <a name="example"></a>Příklad  
 V tomto příkladu analyzuje `string` z šestnáctkové hodnoty a uloží znak, který odpovídá každé šestnáctková hodnota. Nejprve se volá [rozdělit (Char\[\])](xref:System.String.Split(System.Char[])) metodu k získání jednotlivých šestnáctkové hodnoty jako individuální uživatel `string` v poli. Potom volá <xref:System.Convert.ToInt32%28System.String%2CSystem.Int32%29> převést na šestnáctkovou hodnotu Desítková hodnota reprezentovaná jako [int](../../../csharp/language-reference/keywords/int.md). Ukazuje dva různé způsoby, získat znak, který odpovídá této kód znaku. První způsob využívá <xref:System.Char.ConvertFromUtf32%28System.Int32%29>, která vrací odpovídající argument typu celé číslo jako znak `string`. Druhý způsob spočívá explicitní přetypování `int` k [char](../../../csharp/language-reference/keywords/char.md).  
  
 [!code-csharp[csProgGuideTypes#31](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_2.cs)]  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje další způsob, jak převést šestnáctkové `string` na celé číslo, voláním <xref:System.Int32.Parse%28System.String%2CSystem.Globalization.NumberStyles%29> metody.  
  
 [!code-csharp[csProgGuideTypes#32](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_3.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést šestnáctkové `string` k [float](../../../csharp/language-reference/keywords/float.md) pomocí <xref:System.BitConverter?displayProperty=nameWithType> třídy a <xref:System.UInt32.Parse%2A?displayProperty=nameWithType> metoda.  
  
 [!code-csharp[csProgGuideTypes#39](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_4.cs)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak převést [bajtů](../../../csharp/language-reference/keywords/byte.md) pole je možné šestnáctkový řetězec s použitím <xref:System.BitConverter?displayProperty=nameWithType> třídy.  
  
 [!code-csharp[csProgGuideTypes#38](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-between-hexadecimal-strings-and-numeric-types_5.cs)]  
  
## <a name="see-also"></a>Viz také

- [Standardní řetězce číselného formátu](../../../standard/base-types/standard-numeric-format-strings.md)  
- [Typy](../../../csharp/programming-guide/types/index.md)  
- [Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
