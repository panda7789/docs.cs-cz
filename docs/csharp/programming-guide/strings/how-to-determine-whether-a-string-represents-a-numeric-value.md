---
title: 'Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu (Průvodce programováním v C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: f1e5efca7fb3088064b3f252675b8cae965717f0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336583"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a>Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu (Průvodce programováním v C#)
K určení, zda řetězec je platný reprezentace zadané číselného typu, použijte statickou `TryParse` metodu, která je implementována všechny primitivní číselnými typy a také typy, jako <xref:System.DateTime> a <xref:System.Net.IPAddress>. Následující příklad ukazuje, jak určit, zda "108" je platná [int](../../../csharp/language-reference/keywords/int.md).  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 Pokud řetězec obsahuje číselného typu znaky nebo číselná hodnota je příliš velký či příliš malý pro konkrétní typ, který jste zadali, `TryParse` vrací hodnotu false a nastaví výstupní parametr na hodnotu nula. Jinak vrátí hodnotu true a nastaví parametr mimo na číselnou hodnotu řetězce.  
  
> [!NOTE]
>  Řetězec může obsahovat pouze znaky a stále není platné pro typ jehož `TryParse` metoda, která používáte. Například "256" není platná hodnota pro `byte` , ale je platná pro `int`. "98.6" není platná hodnota pro `int` , ale je platná `decimal`.  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak používat `TryParse` s řetězcové vyjádření `long`, `byte`, a `decimal` hodnoty.  
  
 [!code-csharp[csProgGuideStrings#14](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-determine-whether-a-string-represents-a-numeric-value_1.cs)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Číselný primitivní typy také implementace `Parse` statickou metodu, která vyvolá výjimku, pokud řetězec není platné číslo. `TryParse` je obecně efektivnější, protože ji právě vrací hodnotu false, pokud číslo není platné.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Vždy nutné použít `TryParse` nebo `Parse` metody k ověření uživatelského vstupu z ovládací prvky například textová pole a pole se seznamem.  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Převedení pole bajtů na typ int](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)  
 [Postupy: Převedení řetězce na číslo](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)  
 [Postupy: Převod mezi hexadecimálními řetězci a číselnými typy](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)  
 [Analýza číselných řetězců](../../../standard/base-types/parsing-numeric.md)  
 [Typy formátování](../../../standard/base-types/formatting-types.md)
