---
title: Jak dotaz na věty, které obsahují zadanou sadu slov (LINQ) (C#)
ms.date: 07/20/2015
ms.assetid: 0724b429-4b87-4d26-a7b1-409358f3fc20
ms.openlocfilehash: df279f57d9965d796397cbcf7a0f3ba05bf9e5c1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168853"
---
# <a name="how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq-c"></a>Jak dotaz na věty, které obsahují zadanou sadu slov (LINQ) (C#)
Tento příklad ukazuje, jak najít věty v textovém souboru, které obsahují shody pro každou zadanou sadu slov. Přestože pole hledaných termínů je pevně zakódován v tomto příkladu, může být také naplněndynamicky za běhu. V tomto příkladu dotaz vrátí věty, které obsahují slova "Historicky", "data" a "integrované".  
  
## <a name="example"></a>Příklad  
  
```csharp  
class FindSentences  
{  
    static void Main()  
    {  
        string text = @"Historically, the world of data and the world of objects " +  
        @"have not been well integrated. Programmers work in C# or Visual Basic " +  
        @"and also in SQL or XQuery. On the one side are concepts such as classes, " +  
        @"objects, fields, inheritance, and .NET Framework APIs. On the other side " +  
        @"are tables, columns, rows, nodes, and separate languages for dealing with " +  
        @"them. Data types often require translation between the two worlds; there are " +  
        @"different standard functions. Because the object world has no notion of query, a " +  
        @"query can only be represented as a string without compile-time type checking or " +  
        @"IntelliSense support in the IDE. Transferring data from SQL tables or XML trees to " +  
        @"objects in memory is often tedious and error-prone.";  
  
        // Split the text block into an array of sentences.  
        string[] sentences = text.Split(new char[] { '.', '?', '!' });  
  
        // Define the search terms. This list could also be dynamically populated at runtime.  
        string[] wordsToMatch = { "Historically", "data", "integrated" };  
  
        // Find sentences that contain all the terms in the wordsToMatch array.  
        // Note that the number of terms to match is not specified at compile time.  
        var sentenceQuery = from sentence in sentences  
                            let w = sentence.Split(new char[] { '.', '?', '!', ' ', ';', ':', ',' },  
                                                    StringSplitOptions.RemoveEmptyEntries)  
                            where w.Distinct().Intersect(wordsToMatch).Count() == wordsToMatch.Count()  
                            select sentence;  
  
        // Execute the query. Note that you can explicitly type  
        // the iteration variable here even though sentenceQuery  
        // was implicitly typed.
        foreach (string str in sentenceQuery)  
        {  
            Console.WriteLine(str);  
        }  
  
        // Keep the console window open in debug mode.  
        Console.WriteLine("Press any key to exit");  
        Console.ReadKey();  
    }  
}  
/* Output:  
Historically, the world of data and the world of objects have not been well integrated  
*/  
```  
  
 Dotaz funguje tak, že nejprve rozdělí text na věty a potom rozdělí věty do pole řetězců, které drží každé slovo. Pro každé z těchto <xref:System.Linq.Enumerable.Distinct%2A> polí metoda odebere všechna duplicitní slova <xref:System.Linq.Enumerable.Intersect%2A> a pak dotaz `wordsToMatch` provede operaci na pole slov a pole. Pokud je počet průsečíku stejný jako `wordsToMatch` počet pole, všechna slova byla nalezena ve slovech a původní věta je vrácena.  
  
 Ve volání <xref:System.String.Split%2A>na , interpunkční znaménka se používají jako oddělovače k jejich odstranění z řetězce. Pokud jste tak neučinili, například můžete mít řetězec "Historicky", který `wordsToMatch` by se neshoduje "Historicky" v poli. V závislosti na typech interpunkce, které se nacházejí ve zdrojovém textu, bude pravděpodobně pravděpodobně třeba použít další oddělovače.  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
Vytvořte projekt aplikace konzoly `using` Jazyka C# se direktivami pro obory názvů System.Linq a System.IO.

## <a name="see-also"></a>Viz také

- [LINQ a řetězce (C#)](./linq-and-strings.md)
