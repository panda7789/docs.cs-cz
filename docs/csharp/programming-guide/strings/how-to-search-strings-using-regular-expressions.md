---
title: "Postupy: Vyhledávání řetězců pomocí regulárních výrazů (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- searching strings [C#]
- strings [C#], searching with RegEx
ms.assetid: dcab2150-a4a2-4fe4-87e3-83b83b58d84a
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c851c57b44f1343816b905db002e530121fb6c0a
ms.sourcegitcommit: 3a96c706e4dbb4667bf3bf37edac9e1666646f93
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2018
---
# <a name="how-to-search-strings-using-regular-expressions-c-programming-guide"></a>Postupy: Vyhledávání řetězců pomocí regulárních výrazů (Průvodce programováním v C#)
<xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType> Třídu lze použít k vyhledání řetězců. Tato hledání mohou být v rozsahu v složitosti od velmi jednoduché provedení úplné použití regulárních výrazů. Následují dva příklady vyhledávání pomocí řetězce <xref:System.Text.RegularExpressions.Regex> třídy. Další informace najdete v tématu [regulární výrazy rozhraní .NET Framework](https://msdn.microsoft.com/library/hs600312).  
  
## <a name="example"></a>Příklad  
 Následující kód je konzolovou aplikaci, která provede jednoduché hledání bez rozlišování velikosti písmen řetězců v matici. Statickou metodu <xref:System.Text.RegularExpressions.Regex.IsMatch%2A?displayProperty=nameWithType> provede vyhledávání zadaný hledaný řetězec a řetězec, který obsahuje vzor hledání. V takovém případě třetí argument slouží k označení, že by měl být ignoruje velikost písmen. Další informace naleznete v tématu <xref:System.Text.RegularExpressions.RegexOptions?displayProperty=nameWithType>.  
  
 [!code-csharp[csProgGuideStrings#17](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_1.cs)]  
  
## <a name="example"></a>Příklad  
 Následující kód je konzolovou aplikaci, která používá regulární výrazy k ověření formát každý řetězce v matici. Ověření vyžaduje, aby každý řetězec mít formu telefonní číslo, ve kterém jsou tři skupiny číslic odděleny pomlčkami, první dvě skupiny obsahují tři znaky a třetí skupina obsahuje čtyři číslice. To se provádí pomocí regulárního výrazu `^\\d{3}-\\d{3}-\\d{4}$`. Další informace najdete v tématu [jazyk regulárních výrazů – Stručná referenční příručka](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c).  
  
 [!code-csharp[csProgGuideStrings#18](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-search-strings-using-regular-expressions_2.cs)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Text.RegularExpressions.Regex?displayProperty=nameWithType>  
 [Průvodce programováním v jazyce C#](../../../csharp/programming-guide/index.md)  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)  
 [Regulární výrazy rozhraní .NET framework](https://msdn.microsoft.com/library/hs600312)  
 [Jazyk regulárních výrazů – stručná referenční dokumentace](http://msdn.microsoft.com/library/930653a6-95d2-4697-9d5a-52d11bb6fd4c)
