---
title: Jak počítat výskyty slova v řetězci (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: f8e6f546-7c14-4aa1-8a75-e8d09f3b8ccd
ms.openlocfilehash: 9c3ac2e0d44d52e437586a4d105a022f75c1dc54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79169322"
---
# <a name="how-to-count-occurrences-of-a-word-in-a-string-linq-c"></a>Jak počítat výskyty slova v řetězci (LINQ) (C#)
Tento příklad ukazuje, jak pomocí dotazu LINQ počítat výskyty zadaného slova v řetězci. Všimněte si, že k <xref:System.String.Split%2A> provedení count, nejprve metoda je volána k vytvoření pole slov. <xref:System.String.Split%2A> Je náklady na výkon metody. Pokud jedinou operací na řetězci je počítat slova, <xref:System.Text.RegularExpressions.Regex.Matches%2A> <xref:System.String.IndexOf%2A> měli byste zvážit použití metody nebo místo. Pokud však výkon není kritický problém nebo jste již větu rozdělili, abyste nad ní mohli provádět jiné typy dotazů, má smysl použít linq k počítání slov nebo frází.  
  
## <a name="example"></a>Příklad  
  
```csharp  
class CountWords  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects" +  
          @" have not been well integrated. Programmers work in C# or Visual Basic" +  
          @" and also in SQL or XQuery. On the one side are concepts such as classes," +  
          @" objects, fields, inheritance, and .NET Framework APIs. On the other side" +  
          @" are tables, columns, rows, nodes, and separate languages for dealing with" +  
          @" them. Data types often require translation between the two worlds; there are" +  
          @" different standard functions. Because the object world has no notion of query, a" +  
          @" query can only be represented as a string without compile-time type checking or" +  
          @" IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to" +  
          @" objects in memory is often tedious and error-prone.";  
  
        string searchTerm = "data";  
  
        //Convert the string into an array of words  
        string[] source = text.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' }, StringSplitOptions.RemoveEmptyEntries);  
  
        // Create the query.  Use ToLowerInvariant to match "data" and "Data"
        var matchQuery = from word in source  
                         where word.ToLowerInvariant() == searchTerm.ToLowerInvariant()  
                         select word;  
  
        // Count the matches, which executes the query.  
        int wordCount = matchQuery.Count();  
        Console.WriteLine("{0} occurrences(s) of the search term \"{1}\" were found.", wordCount, searchTerm);  
  
        // Keep console window open in debug mode  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
   3 occurrences(s) of the search term "data" were found.  
*/  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.  
  
## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
