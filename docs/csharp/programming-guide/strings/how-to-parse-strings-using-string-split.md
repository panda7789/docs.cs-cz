---
title: "Postupy: Analýza řetězců využívajících String.Split (programování průvodce v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b97d1d89a4c74a4c759d1ed41a0bc2476b3b07a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-parse-strings-using-stringsplit-c-programming-guide"></a>Postupy: Analýza řetězců využívajících String.Split (programování průvodce v C#)
Následující příklad kódu ukazuje, jak může být řetězec analyzovat pomocí <xref:System.String.Split%2A?displayProperty=nameWithType> metoda. Jako vstup <xref:System.String.Split%2A> přijímá pole znaků, které označují, které znaky oddělení zajímavé řetězců dílčí řetězce cíl.  Funkce vrátí hodnotu pole řetězců sub.  
  
 Tento příklad používá mezery, čárky, tečky, dvojtečky a karty, všechny předané pole obsahující tyto oddělení znaků, který má <xref:System.String.Split%2A>.  Jednotlivých slov ve větě cílový řetězec zobrazí samostatně z výsledné pole řetězců.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[csProgGuideStrings#16](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-parse-strings-using-string-split_1.cs)]  
  
## <a name="example"></a>Příklad  
 Ve výchozím nastavení vrátí String.Split prázdné řetězce, pokud dva znaky dělicí zobrazí souvisle v cílový řetězec.  Můžete předat volitelný parametr StringSplitOptions.RemoveEmptyEntries vyloučit všechny prázdné řetězce ve výstupu.  
  
 String.Split může trvat pole řetězců (sekvence znaků, které se chovají jako oddělovače pro potřeby analýzy cíl řetězce, místo jedné znaků).  
  
```csharp  
class TestStringSplit  
{  
    static void Main()  
    {  
        string[] separatingChars = { "<<", "..." };  
  
        string text = "one<<two......three<four";  
        System.Console.WriteLine("Original text: '{0}'", text);  
  
        string[] words = text.Split(separatingChars, System.StringSplitOptions.RemoveEmptyEntries );  
        System.Console.WriteLine("{0} substrings in text:", words.Length);  
  
        foreach (string s in words)  
        {  
            System.Console.WriteLine(s);  
        }  
  
        // Keep the console window open in debug mode.  
        System.Console.WriteLine("Press any key to exit.");  
        System.Console.ReadKey();  
    }  
}  
/* Output:  
    Original text: 'one<<two......three<four'  
    3 words in text:  
    one  
    two  
    three<four  
*/  
```  
  
## <a name="see-also"></a>Viz také  
 [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)  
 [Řetězce](../../../csharp/programming-guide/strings/index.md)  
 [Regulární výrazy rozhraní .NET framework](https://msdn.microsoft.com/library/hs600312)
